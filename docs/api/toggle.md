---
title: "ion-toggle"
---
import Props from '@site/static/auto-generated/toggle/props.md';
import Events from '@site/static/auto-generated/toggle/events.md';
import Methods from '@site/static/auto-generated/toggle/methods.md';
import Parts from '@site/static/auto-generated/toggle/parts.md';
import CustomProps from '@site/static/auto-generated/toggle/custom-props.md';
import Slots from '@site/static/auto-generated/toggle/slots.md';

<head>
  <title>Toggle | ion-toggle: Custom Toggle Button for Ionic Applications</title>
  <meta name="description" content="Toggleは、1つのオプションの状態を変更します。ion-toggleを使用して、アプリケーションのオン/オフを切り替えることができるカスタマイズ可能なトグルボタンを作成します。" />
</head>

import EncapsulationPill from '@components/page/api/EncapsulationPill';

<EncapsulationPill type="shadow" />


Toggles are switches that change the state of a single option. They can be switched on or off by pressing or swiping them. Toggles can also be checked programmatically by setting the `checked` property.

## Basic Usage

import Basic from '@site/static/usage/toggle/basic/index.md';

<Basic />


## On / Off Labels

Toggles can enable on/off labels by setting the `enableOnOffLabels` property. This is important for accessibility as it makes it easier to differentiate between a checked and unchecked toggle.

import OnOff from '@site/static/usage/toggle/on-off/index.md';

<OnOff />


## Theming

### Colors

import Colors from '@site/static/usage/toggle/theming/colors/index.md';

<Colors />

### CSS Custom Properties

CSS custom properties can be combined with standard CSS to target different parts of a toggle. We can modify the `width` and `height` of the toggle directly to change the size of the track, while using the `--handle-width` and `--handle-height` custom properties to customize the handle size.

import CSSProps from '@site/static/usage/toggle/theming/css-properties/index.md';

<CSSProps />

### CSS Shadow Parts

We can further customize toggle by targeting specific shadow parts that are exposed. Any CSS property on these parts can be styled and they can also be combined with CSS custom properties.

import CSSParts from '@site/static/usage/toggle/theming/css-shadow-parts/index.md';

<CSSParts />


## Interfaces

### ToggleChangeEventDetail

```typescript
interface ToggleChangeEventDetail<T = any> {
  value: T;
  checked: boolean;
}
```

### ToggleCustomEvent

必須ではありませんが、このコンポーネントから発行される Ionic イベントでより強く型付けを行うために、`CustomEvent` インターフェースの代わりにこのインターフェースを使用することが可能です。

```typescript
interface ToggleCustomEvent<T = any> extends CustomEvent {
  detail: ToggleChangeEventDetail<T>;
  target: HTMLIonToggleElement;
}
```


## Properties
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
