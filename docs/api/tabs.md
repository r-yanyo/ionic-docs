---
title: "ion-tabs"
hide_table_of_contents: true
demoUrl: "/docs/demos/api/tabs/index.html"
demoSourceUrl: "https://github.com/ionic-team/ionic-docs/tree/main/static/demos/api/tabs/index.html"
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import TOCInline from '@theme/TOCInline';

import Props from '@site/static/auto-generated/tabs/props.md';
import Events from '@site/static/auto-generated/tabs/events.md';
import Methods from '@site/static/auto-generated/tabs/methods.md';
import Parts from '@site/static/auto-generated/tabs/parts.md';
import CustomProps from '@site/static/auto-generated/tabs/custom-props.md';
import Slots from '@site/static/auto-generated/tabs/slots.md';

<head>
  <title>Ion-Tabs: Tab-Based Component for App Top-Level Navigation</title>
  <meta name="description" content="Tabsは、タブベースのナビゲーションを実装するためのトップレベルのコンポーネントです。イオンタブはスタイリングを持たず、ネイティブアプリのように動作するナビゲーションのルーター出口として機能します。" />
</head>

import EncapsulationPill from '@components/page/api/EncapsulationPill';

<EncapsulationPill type="shadow" />

<h2 className="table-of-contents__title">コンテンツ</h2>

<TOCInline
  toc={toc}
  maxHeadingLevel={2}
/>



Tabsは、タブベースのナビゲーションを実現するためのトップレベル・ナビゲーション・コンポーネントです。
このコンポーネントは、個々の [Tab] (tab.md) コンポーネントのコンテナです。

`ion-tabs` コンポーネントはスタイルを持たず、ナビゲーションを処理するためのルータアウトレットとして動作します。また、UI フィードバックやタブを切り替えるための機構は提供しない。タブを切り替えるには、`ion-tabs` の直接の子として `ion-tab-bar` を用意しなければなりません。

`ion-tabs` と `ion-tab-bar` はどちらもスタンドアロンな要素として利用することができます。これらは互いに依存せずに動作しますが、通常は、ネイティブアプリのように動作するタブベースのナビゲーションを実装するために一緒に使用します。

`ion-tab-bar` は、`ion-tabs` コンポーネントの適切な場所に投影するために、スロットを定義する必要があります。

## Interfaces

### TabsCustomEvent

必須ではありませんが、このコンポーネントから発行される Ionic イベントでより強く型付けを行うために、`CustomEvent` インターフェースの代わりにこのインターフェースを使用することが可能です。

```typescript
interface TabsCustomEvent extends CustomEvent {
  detail: { tab: string };
  target: HTMLIonTabsElement;
}
```




## 使い方

<Tabs groupId="framework" defaultValue="angular" values={[{ value: 'angular', label: 'Angular' }, { value: 'javascript', label: 'Javascript' }, { value: 'react', label: 'React' }, { value: 'stencil', label: 'Stencil' }, { value: 'vue', label: 'Vue' }]}>

<TabItem value="angular">

```html
<ion-tabs>
  <ion-tab-bar slot="bottom">
    <ion-tab-button tab="schedule">
      <ion-icon name="calendar"></ion-icon>
      <ion-label>Schedule</ion-label>
      <ion-badge>6</ion-badge>
    </ion-tab-button>

    <ion-tab-button tab="speakers">
      <ion-icon name="person-circle"></ion-icon>
      <ion-label>Speakers</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="map">
      <ion-icon name="map"></ion-icon>
      <ion-label>Map</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="about">
      <ion-icon name="information-circle"></ion-icon>
      <ion-label>About</ion-label>
    </ion-tab-button>
  </ion-tab-bar>
</ion-tabs>
```


### Router integration

When used with Angular's router the `tab` property of the `ion-tab-button` should be a reference to the route path.

```html
<ion-tabs>
  <ion-tab-bar slot="bottom">
    <ion-tab-button tab="schedule">
      <ion-icon name="calendar"></ion-icon>
      <ion-label>Schedule</ion-label>
    </ion-tab-button>
  </ion-tab-bar>
</ion-tabs>
```

```typescript
import { Routes } from '@angular/router';
import { TabsPage } from './tabs-page';

const routes: Routes = [
  {
    path: 'tabs',
    component: TabsPage,
    children: [
      {
        path: 'schedule',
        children: [
          {
            path: '',
            loadChildren: '../schedule/schedule.module#ScheduleModule'
          }
        ]
      },
      {
        path: '',
        redirectTo: '/app/tabs/schedule',
        pathMatch: 'full'
      }
    ]
  }
];
```


</TabItem>


<TabItem value="javascript">

```html
<ion-tabs>

  <ion-tab tab="tab-schedule">
    <ion-nav></ion-nav>
  </ion-tab>

  <ion-tab tab="tab-speaker">
    <ion-nav></ion-nav>
  </ion-tab>

  <ion-tab tab="tab-map" component="page-map">
    <ion-nav></ion-nav>
  </ion-tab>

  <ion-tab tab="tab-about" component="page-about">
    <ion-nav></ion-nav>
  </ion-tab>

  <ion-tab-bar slot="bottom">
    <ion-tab-button tab="tab-schedule">
      <ion-icon name="calendar"></ion-icon>
      <ion-label>Schedule</ion-label>
      <ion-badge>6</ion-badge>
    </ion-tab-button>

    <ion-tab-button tab="tab-speaker">
      <ion-icon name="person-circle"></ion-icon>
      <ion-label>Speakers</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="tab-map">
      <ion-icon name="map"></ion-icon>
      <ion-label>Map</ion-label>
    </ion-tab-button>

    <ion-tab-button tab="tab-about">
      <ion-icon name="information-circle"></ion-icon>
      <ion-label>About</ion-label>
    </ion-tab-button>
  </ion-tab-bar>

</ion-tabs>
```


### Activating Tabs

Each `ion-tab-button` will activate one of the tabs when pressed. In order to link the `ion-tab-button` to the `ion-tab` container, a matching `tab` property should be set on each component.

```html
<ion-tab tab="settings">
  ...
</ion-tab>

<ion-tab-button tab="settings">
  ...
</ion-tab-button>
```

The `ion-tab-button` and `ion-tab` above are linked by the common `tab` property.

The `tab` property identifies each tab, and it has to be unique within the `ion-tabs`. It's important to always set the `tab` property on the `ion-tab` and `ion-tab-button`, even if one component is not used.


### Router integration

When used with Ionic's router (`ion-router`) the `tab` property of the `ion-tab` matches the `component` property of an `ion-route`.

The following route within the scope of an `ion-tabs` outlet:

```html
<ion-route url="/settings-page" component="settings"></ion-route>
```

will match the following tab:

```html
<ion-tab tab="settings" component="settings-component"></ion-tab>
```

</TabItem>


<TabItem value="react">

```tsx
import React from 'react';
import { IonTabs, IonTabBar, IonTabButton, IonIcon, IonLabel, IonBadge } from '@ionic/react';
import { calendar, personCircle, map, informationCircle } from 'ionicons/icons';


export const TabsExample: React.FC = () => (
  <IonTabs>
    <IonTabBar slot="bottom">
      <IonTabButton tab="schedule">
        <IonIcon icon={calendar} />
        <IonLabel>Schedule</IonLabel>
        <IonBadge>6</IonBadge>
      </IonTabButton>

      <IonTabButton tab="speakers">
        <IonIcon icon={personCircle} />
        <IonLabel>Speakers</IonLabel>
      </IonTabButton>

      <IonTabButton tab="map">
        <IonIcon icon={map} />
        <IonLabel>Map</IonLabel>
      </IonTabButton>

      <IonTabButton tab="about">
        <IonIcon icon={informationCircle} />
        <IonLabel>About</IonLabel>
      </IonTabButton>
    </IonTabBar>
  </IonTabs>
);
```


</TabItem>


<TabItem value="stencil">

```tsx
import { Component, h } from '@stencil/core';

@Component({
  tag: 'tabs-example',
  styleUrl: 'tabs-example.css'
})
export class TabsExample {
  render() {
    return [
     <ion-tabs>
      <ion-tab tab="tab-schedule">
        <ion-nav></ion-nav>
      </ion-tab>

      <ion-tab tab="tab-speaker">
        <ion-nav></ion-nav>
      </ion-tab>

      <ion-tab tab="tab-map" component="page-map">
        <ion-nav></ion-nav>
      </ion-tab>

      <ion-tab tab="tab-about" component="page-about">
        <ion-nav></ion-nav>
      </ion-tab>

      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="tab-schedule">
          <ion-icon name="calendar"></ion-icon>
          <ion-label>Schedule</ion-label>
          <ion-badge>6</ion-badge>
        </ion-tab-button>

        <ion-tab-button tab="tab-speaker">
          <ion-icon name="person-circle"></ion-icon>
          <ion-label>Speakers</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab-map">
          <ion-icon name="map"></ion-icon>
          <ion-label>Map</ion-label>
        </ion-tab-button>

        <ion-tab-button tab="tab-about">
          <ion-icon name="information-circle"></ion-icon>
          <ion-label>About</ion-label>
        </ion-tab-button>
      </ion-tab-bar>

    </ion-tabs>
    ];
  }
}
```


### Activating Tabs

Each `ion-tab-button` will activate one of the tabs when pressed. In order to link the `ion-tab-button` to the `ion-tab` container, a matching `tab` property should be set on each component.

```jsx
<ion-tab tab="settings">
  ...
</ion-tab>

<ion-tab-button tab="settings">
  ...
</ion-tab-button>
```

The `ion-tab-button` and `ion-tab` above are linked by the common `tab` property.

The `tab` property identifies each tab, and it has to be unique within the `ion-tabs`. It's important to always set the `tab` property on the `ion-tab` and `ion-tab-button`, even if one component is not used.


### Router integration

When used with Ionic's router (`ion-router`) the `tab` property of the `ion-tab` matches the `component` property of an `ion-route`.

The following route within the scope of an `ion-tabs` outlet:

```tsx
<ion-route url="/settings-page" component="settings"></ion-route>
```

will match the following tab:

```tsx
<ion-tab tab="settings" component="settings-component"></ion-tab>
```

</TabItem>


<TabItem value="vue">

**Tabs.vue**
```html
<template>
  <ion-page>
    <ion-tabs @ionTabsWillChange="beforeTabChange" @ionTabsDidChange="afterTabChange">
      <ion-tab-bar slot="bottom">
        <ion-tab-button tab="schedule" href="/tabs/schedule">
          <ion-icon :icon="calendar"></ion-icon>
          <ion-label>Schedule</ion-label>
          <ion-badge>6</ion-badge>
        </ion-tab-button>
  
        <ion-tab-button tab="speakers" href="/tabs/speakers">
          <ion-icon :icon="personCircle"></ion-icon>
          <ion-label>Speakers</ion-label>
        </ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </ion-page>
</template>

<script>
import { defineComponent } from 'vue';
import { 
  IonIcon, 
  IonLabel, 
  IonPage,
  IonTabBar, 
  IonTabButton, 
  IonTabs
} from '@ionic/vue';
import { calendar, personCircle } from 'ionicons/icons';

export default defineComponent({
  components: { IonIcon, IonLabel, IonPage, IonTabBar, IonTabButton, IonTabs },
  setup() {
    const beforeTabChange = () => {
      // do something before tab change
    }
    const afterTabChange = () => {
      // do something after tab change
    }
    return {
      calendar,
      personCircle,
      beforeTabChange,
      afterTabChange
    }
  }
});
</script>
```

**Schedule.vue**
```html
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Schedule</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content class="ion-padding">Schedule Tab</ion-content>
  </ion-page>
</template>

<script>
import { defineComponent } from 'vue';
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar
} from '@ionic/vue';

export default defineComponent({
  components: { IonContent, IonHeader, IonPage, IonTitle, IonToolbar }
});
</script>
```

**Speakers.vue**
```html
<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Speakers</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content class="ion-padding">Speakers Tab</ion-content>
  </ion-page>
</template>

<script>
import { defineComponent } from 'vue';
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar
} from '@ionic/vue';

export default defineComponent({
  components: { IonContent, IonHeader, IonPage, IonTitle, IonToolbar }
});
</script>
```

</TabItem>

</Tabs>

## プロパティ
<Props />

## イベント
<Events />

## メソッド
<Methods />

## CSS Shadow Parts
<Parts />

## CSSカスタムプロパティ
<CustomProps />

## Slots
<Slots />