---
title: "ion-datetime-button"
---
import Props from '@site/static/auto-generated/datetime-button/props.md';
import Events from '@site/static/auto-generated/datetime-button/events.md';
import Methods from '@site/static/auto-generated/datetime-button/methods.md';
import Parts from '@site/static/auto-generated/datetime-button/parts.md';
import CustomProps from '@site/static/auto-generated/datetime-button/custom-props.md';
import Slots from '@site/static/auto-generated/datetime-button/slots.md';

<head>
  <title>ion-datetime-button: Ionic API Input for interacting with Datetime picker</title>
  <meta name="description" content="Datetime button links with a datetime instance to easily a datetime in a popover, modal, and more." />
</head>

import EncapsulationPill from '@components/page/api/EncapsulationPill';

<EncapsulationPill type="shadow" />

Datetimeボタンは、[Datetime](./datetime) コンポーネントとリンクし、フォーマットされた日付と時刻を表示します。また、モーダルやポップオーバーなどで日時を表示するためのボタンも用意されています。

## 概要

Datetimeボタンは、スペースに制約がある場合に使用する必要があります。このコンポーネントは、現在の日付と時刻の値を表示するボタンを表示します。ボタンがタップされると、日付や時刻のピッカーがオーバーレイで表示されます。

Angular、React、VueなどのJavaScriptフレームワークでDatetime Buttonを使用する場合は、 [ion-modalのkeepContentsMountedプロパティ](./modal#keepcontentsmounted) または [ion-popover](./popover#keepcontentsmounted) を使用していることを確認してください。これにより、オーバーレイがまだ表示されていない場合でも、リンクされたdatetimeインスタンスがマウントされるようになります。

## 基本的な使い方

import Basic from '@site/static/usage/datetime-button/basic/index.md';

<Basic />

## ローカライゼーション

The localized text on `ion-datetime-button` is determined by the `locale` property on the associated `ion-datetime` instance. See [Datetime Localization](./datetime#localization) for more details.

## モーダルやポップオーバーと使う

`ion-datetime-button` は、マウントされた `ion-datetime` インスタンスと関連付ける必要があります。そのため、[Inline Modals](./modal#inline-modals-recommended) と [Inline Popovers](./popover#inline-popovers) は `keepContentsMounted` プロパティを `true` に設定して使用しなければなりません。

<!--
## Customization

TODO

### Buttons

TODO

### Theming

TODO
-->

## Properties
<Props />

## Events
<Events />

## Methods
<Methods />

## CSS Shadow Parts
<Parts />

## CSS Custom Properties
<CustomProps />

## Slots
<Slots />
