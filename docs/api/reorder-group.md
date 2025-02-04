---
title: "ion-reorder-group"
---
import Props from '@site/static/auto-generated/reorder-group/props.md';
import Events from '@site/static/auto-generated/reorder-group/events.md';
import Methods from '@site/static/auto-generated/reorder-group/methods.md';
import Parts from '@site/static/auto-generated/reorder-group/parts.md';
import CustomProps from '@site/static/auto-generated/reorder-group/custom-props.md';
import Slots from '@site/static/auto-generated/reorder-group/slots.md';

<head>
  <title>ion-reorder-group: Wrapper Component for Ionic Framework Apps</title>
  <meta name="description" content="ion-reorder-groupは、Ionicアプリでion-reorderコンポーネントを使用するアイテムのためのラッパーコンポーネントです。ion-reorder-groupの使い方はこちらをご覧ください。" />
</head>

import EncapsulationPill from '@components/page/api/EncapsulationPill';


The reorder group is a container for items using the [reorder](./reorder) component. When the user drags an item and drops it in a new position, the `ionItemReorder` event is dispatched. A handler for this event should be implemented that calls the `complete` method.

The `detail` property of the `ionItemReorder` event includes all of the relevant information about the reorder operation, including the `from` and `to` indexes. In the context of reordering, an item moves `from` an index `to` a new index. For example usage of the reorder group, see the [reorder](./reorder) documentation.


## Interfaces

### ItemReorderEventDetail

```typescript
interface ItemReorderEventDetail {
  from: number;
  to: number;
  complete: (data?: boolean | any[]) => any;
}
```

### ItemReorderCustomEvent

必須ではありませんが、このコンポーネントから発行される Ionic イベントでより強く型付けを行うために、`CustomEvent` インターフェースの代わりにこのインターフェースを使用することが可能です。

```typescript
interface ItemReorderCustomEvent extends CustomEvent {
  detail: ItemReorderEventDetail;
  target: HTMLIonReorderGroupElement;
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
