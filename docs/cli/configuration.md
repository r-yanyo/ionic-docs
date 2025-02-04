---
title: 設定
---

<head>
  <title>Capacitor Configuration | Maintain a Global Configuration File</title>
  <meta
    name="description"
    content="Set and print configuration values from project config files and the global CLI config file with Ionic CLI. Read to learn more about Capacitor configuration."
  />
</head>

## ファイル

設定された値はJSONファイルに格納されます。Ionic CLIは、通常`~/.ionic/config.json`にグローバル設定ファイルを設定します。通常はプロジェクトのルートディレクトリに `ionic.config.json` という名前で保存されます。

CLIには、プロジェクト設定ファイルおよびグローバルCLI設定ファイルから設定値を設定およびprintfするためのコマンドが用意されています。[`ionic config get`](commands/config-get.md) と [`ionic config set`](commands/config-set.md) の使い方については、`ionic config--help`を参照してください。

### プロジェクト設定ファイル

各Ionicプロジェクトには、通常はプロジェクトのルートディレクトリに、プロジェクト設定ファイルがあります。以下は注釈付きの `ionic.config.json` です。

```json
{
  // The human-readable name of the app.
  "name": "My App",

  // The project type of the app. The CLI uses this value to determine which
  // commands and command options are available, what to output for help
  // documentation, and what to use for web asset builds and the dev server.
  "type": "angular",

  // The App ID for Appflow.
  "id": "abc123",

  // Configuration object for integrations such as Cordova and Capacitor.
  "integrations": {
    "cordova": {
      ...
    }
  },

  // Hook configuration--see the Hooks section below for details.
  "hooks": {
    ...
  }
}
```

## 環境変数

CLIは、次の環境変数を検索します:

- `IONIC_CONFIG_DIRECTORY`: The directory of the global CLI config. Defaults to `~/.ionic`.
- `IONIC_HTTP_PROXY`: Set a URL for proxying all CLI requests through. See [Using a Proxy](using-a-proxy.md).
- `IONIC_TOKEN`: Automatically authenticates with [Appflow](https://ionic.io/appflow).

## Flags

CLI flagsは、CLIコマンドの動作を変更するグローバルオプションです。

- `--help`: Instead of running the command, view its help page.
- `--verbose`: Show all log messages for debugging purposes.
- `--quiet`: Only show `WARN` and `ERROR` log messages.
- `--no-interactive`: Turn off interactive prompts and fancy outputs. If CI or a non-TTY terminal is detected, the CLI is automatically non-interactive.
- `--confirm`: Turn on auto-confirmation of confirmation prompts. Careful: the CLI prompts before doing something potentially harmful. Auto-confirming may have unintended results.

## Hooks

CLIは、ビルドの前後など、特定のイベント中にスクリプトを実行できます。CLIにフックするために、以下の [npm scripts](https://docs.npmjs.com/misc/scripts) を `package.json`: ファイルで使用できます。:

* `ionic:serve:before`: dev server が start される前に実行されます
* `ionic:serve:after`: dev server が終了される前に実行されます
* `ionic:build:before`: web assetの構築がはじまる前に実行されます
* `ionic:build:after`: web assetの構築が終了して実行されます。
* `ionic:capacitor:run:before` : executed on capacitor run before capacitor open is executed
* `ionic:capacitor:build:before` : executed on capacitor build before capacitor open is executed
* `ionic:capacitor:sync:after`: executed during `ionic capacitor sync` after a sync

When using a shell script for any of the hooks, hook context is defined in environment variables prefixed with `IONIC_CLI_HOOK_CTX_`.

The following example shows the environment variables that are set for the `ionic:capacitor:build` hook.

```shell
IONIC_CLI_HOOK_CTX_NAME=capacitor:build:before
IONIC_CLI_HOOK_CTX_BUILD_CORDOVA_ASSETS=true
IONIC_CLI_HOOK_CTX_BUILD_ENGINE=browser
IONIC_CLI_HOOK_CTX_BUILD_PROJECT=app
IONIC_CLI_HOOK_CTX_BUILD_TYPE=angular
IONIC_CLI_HOOK_CTX_BUILD_VERBOSE=false
IONIC_CLI_HOOK_CTX_CAPACITOR_APP_ID=io.ionic.starter
IONIC_CLI_HOOK_CTX_CAPACITOR_APP_NAME=ionic-starter-app
IONIC_CLI_HOOK_CTX_CAPACITOR_VERBOSE=false
```

Hooksは `ionic.config.json` で定義することもできます。プロジェクト内でHooksオブジェクトを定義します。各キーはフックの名前(先頭に`ionic:`を付けない)で、値はJavaScriptファイルへのパスまたはパスの配列です。

次の例では、ファイルは `ionic:build:before` フックでインポートされ、実行されます。

```json
"hooks": {
  "build:before": "./scripts/build-before.js"
},
```

JavaScript Hook ファイルは、フックが実行されるたびに単一の引数(`ctx`)が渡される単一の関数をエクスポートする必要があります。

引数は、Hook ファイルに指定されたコンテキストであり、Hook ごと、および呼び出しごとに異なります。

`./scripts/build-before.js`:

```javascript
module.exports = function (ctx) {
  console.log(ctx);
};
```

## Multi-app Projects

<small>
  <em>Available in CLI 6.2.0+</em>
</small>

The Ionic CLI supports a multi-app configuration setup, which involves multiple Ionic apps and shared code within a single repository, or [monorepo](../reference/glossary.md#monorepo).

:::note
Ionic CLIは multi-app 構成セットアップをサポートしており、複数のIonicアプリケーションと共有コードが単一のリポジトリ [monorepo](/docs/reference/glossary#monorepo) 内に存在することができます。

If you're using Angular, please see [this article](https://github.com/ionic-team/ionic-cli/wiki/Angular-Monorepo) for examples.
:::

### セットアップステップ

1. Create a directory and initialize a monorepo (see [Project Structure](#project-structure) for full details).
1. Initialize the monorepo as an Ionic multi-app project. This will create a multi-app `ionic.config.json` file. See [Config File](#config-file) for full details.

   ```shell
   $ ionic init --multi-app
   ```

1. Use `ionic start` to create Ionic apps or `ionic init` to initialize existing apps (see [Adding an App](#adding-an-app) for full details).

### プロジェクト構成

In a multi-app project, project structure is flexible. The only requirement is a multi-app `ionic.config.json` file at the root of the repository.

Below is an example setup, where apps in the `apps/` directory are separated from the shared code in the `lib/` directory. Notice the root `ionic.config.json` file and the monorepo's `package.json` file.

```bash
apps/
├── myApp/
└── myOtherApp/
lib/
ionic.config.json
package.json
```

### 設定ファイル

In a multi-app project, apps share a single `ionic.config.json` file at the root of the repository instead of each app having their own. The multi-app config file contains the configuration for each app by nesting configuration objects in a `projects` object. A default app can be specified using `defaultProject`.

Below is an example file, which corresponds to the file structure above.

```json
{
  "defaultProject": "myApp",
  "projects": {
    "myApp": {
      "name": "My App",
      "integrations": {},
      "type": "angular",
      "root": "apps/myApp"
    },
    "myOtherApp": {
      "name": "My Other App",
      "integrations": {},
      "type": "angular",
      "root": "apps/myOtherApp"
    }
  }
}
```

When a multi-app project is detected, the Ionic CLI will operate under the context of an app configured in the root `ionic.config.json`. Project selection criteria is as follows:

1. If the global CLI option `--project` is specified, the project is looked up by key in the `projects` object. For example, `--project=myApp` will select the `myApp` project.
1. If the CLI detects it is being run within a project path, configured with the `root` key, it will select the matched project. For example, using the CLI within the `apps/myOtherApp/src` directory will select the `myOtherApp` project.
1. If a `defaultProject` is specified in `ionic.config.json`, it will select the specified project when the above criteria is not met.

### アプリの追加

Apps can be registered in a multi-app project either by using `ionic start` to create new apps or `ionic init` to initialize existing apps.

#### Using `ionic start`

If a multi-app project is detected during `ionic start`, the CLI will add the app configuration to the root `ionic.config.json` file instead of creating a project-specific one.

Dependency installation can be skipped using `--no-deps` if dependencies are hoisted to the root of the monorepo.

```shell
$ cd apps/
$ ionic start "My New App" --no-deps
```

#### Using `ionic init`

If an app was created in a way other than `ionic start`, for example by using a prebuilt template, use `ionic init` to register the existing app with the multi-app project.

:::note
Make sure the app doesn't have an existing `ionic.config.json`.
:::

```shell
$ cd apps/existing-app/
$ ionic init
```

## 詳細設定

### Buildの上書き

Normally, the CLI runs a hard-coded set of commands based on the project type. For example, the standard web asset build for Angular projects is `ng run app:build`. The web asset build can be overridden and `ionic build` can continue to be used by utilizing the `ionic:build` [npm script](https://docs.npmjs.com/misc/scripts). Similarly, the dev server can be overridden by using the `ionic:serve` npm script.

Pay close attention to the flags supplied to the script by the Ionic CLI. Irregularities may occur if options are not respected, especially for livereload on devices.

### コマンドオプション

Command options can be expressed with environment variables. They are normally set with `--opt=value` syntax. The naming of these environment variables follows a pattern: start with `IONIC_CMDOPTS_`, add the command name (replacing any spaces with underscores), add the option name (replacing any hyphens with underscores), and then uppercase everything. Boolean flags (command-line options that don't take a value) can be set to `1` or `0`. Strip the `--no-` prefix in boolean flags, if it exists (`--no-open` in ionic serve can be expressed with `IONIC_CMDOPTS_SERVE_OPEN=0`, for example).

For example, the command options in `ionic cordova run ios -lc --livereload-port=1234 --host=0.0.0.0` can also be expressed with this series of environment variables:

```shell
$ export IONIC_CMDOPTS_CORDOVA_RUN_LIVERELOAD=1
$ export IONIC_CMDOPTS_CORDOVA_RUN_CONSOLELOGS=1
$ export IONIC_CMDOPTS_CORDOVA_RUN_LIVERELOAD_PORT=1234
$ export IONIC_CMDOPTS_CORDOVA_RUN_HOST=0.0.0.0
```

If these variables are set in the environment, `ionic cordova build ios` will use new defaults for its options.

### 遠隔計測について

CLIからIonicに使用状況データが送信されるため、操作性が向上します。この機能を無効にするには、`ionic config set-g telemetry false`を実行してください。
