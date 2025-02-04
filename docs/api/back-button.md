---
title: "ion-back-button"
hide_table_of_contents: true
demoUrl: "/docs/demos/api/back-button/index.html"
demoSourceUrl: "https://github.com/ionic-team/ionic-docs/tree/main/static/demos/api/back-button/index.html"
---
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';
import TOCInline from '@theme/TOCInline';

import Props from '@site/static/auto-generated/back-button/props.md';
import Events from '@site/static/auto-generated/back-button/events.md';
import Methods from '@site/static/auto-generated/back-button/methods.md';
import Parts from '@site/static/auto-generated/back-button/parts.md';
import CustomProps from '@site/static/auto-generated/back-button/custom-props.md';
import Slots from '@site/static/auto-generated/back-button/slots.md';

<head>
  <title>Back Button | ion-back-button: Custom Menu Icon for Applications</title>
  <meta name="description" content="ion-back-buttonは、Android、iOS、およびProgressive Web Apps用のカスタムメニューアイコンです。Ionic Frameworkのコンポーネントを使用して、簡単にアプリケーションを構築できます。" />
</head>

import EncapsulationPill from '@components/page/api/EncapsulationPill';

<EncapsulationPill type="shadow" />

<h2 className="table-of-contents__title">コンテンツ</h2>

<TOCInline
  toc={toc}
  maxHeadingLevel={2}
/>



back buttonは、クリックするとアプリのひとつ前の履歴に戻ります。modeに基づいてどのようにレンダリングし、ナビゲーションスタックに基づいていつ表示するかを知っていれば十分です。

back buttonの表示内容を変更するには、`text` と `icon` のプロパティを使用します。




## 使い方

<Tabs groupId="framework" defaultValue="angular" values={[{ value: 'angular', label: 'Angular' }, { value: 'javascript', label: 'Javascript' }, { value: 'react', label: 'React' }, { value: 'stencil', label: 'Stencil' }, { value: 'vue', label: 'Vue' }]}>

<TabItem value="angular">

```html
<!-- Default back button -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with a default href -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button defaultHref="home"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with custom text and icon -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button
          [text]="buttonText"
          [icon]="buttonIcon">
      </ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with no text and custom icon -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button text="" icon="add"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Danger back button next to a menu button -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-menu-button></ion-menu-button>
      <ion-back-button color="danger"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>
```

</TabItem>


<TabItem value="javascript">

```html
<!-- Default back button -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with a default href -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button default-href="home"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with custom text and icon -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button text="Volver" icon="close"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Back button with no text and custom icon -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-back-button text="" icon="add"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>

<!-- Danger back button next to a menu button -->
<ion-header>
  <ion-toolbar>
    <ion-buttons slot="start">
      <ion-menu-button></ion-menu-button>
      <ion-back-button color="danger"></ion-back-button>
    </ion-buttons>
  </ion-toolbar>
</ion-header>
```

</TabItem>


<TabItem value="react">

```tsx
import React from 'react';
import { IonBackButton, IonHeader, IonToolbar, IonButtons, IonMenuButton, IonContent } from '@ionic/react';

export const BackButtonExample: React.FC = () => (
  <IonContent>
    {/*-- Default back button --*/}
    <IonHeader>
      <IonToolbar>
        <IonButtons slot="start">
          <IonBackButton />
        </IonButtons>
      </IonToolbar>
    </IonHeader>

    {/*-- Back button with a default href --*/}
    <IonHeader>
      <IonToolbar>
        <IonButtons slot="start">
          <IonBackButton defaultHref="home" />
        </IonButtons>
      </IonToolbar>
    </IonHeader>

    {/*-- Back button with custom text and icon --*/}
    <IonHeader>
      <IonToolbar>
        <IonButtons slot="start">
          <IonBackButton text="buttonText" icon="buttonIcon" />
        </IonButtons>
      </IonToolbar>
    </IonHeader>

    {/*-- Back button with no text and custom icon --*/}
    <IonHeader>
      <IonToolbar>
        <IonButtons slot="start">
          <IonBackButton text="" icon="add" />
        </IonButtons>
      </IonToolbar>
    </IonHeader>

    {/*-- Danger back button next to a menu button --*/}
    <IonHeader>
      <IonToolbar>
        <IonButtons slot="start">
          <IonMenuButton />
          <IonBackButton color="danger" />
        </IonButtons>
      </IonToolbar>
    </IonHeader>
  </IonContent>
);
```

</TabItem>


<TabItem value="stencil">

```tsx
import { Component, h } from '@stencil/core';

@Component({
  tag: 'back-button-example',
  styleUrl: 'back-button-example.css'
})
export class BackButtonExample {
  render() {
    const buttonText = "Custom";
    const buttonIcon = "add";

    return [
      // Default back button
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-back-button></ion-back-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>,

      // Back button with a default href
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-back-button defaultHref="home"></ion-back-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>,

      // Back button with custom text and icon
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-back-button
              text={buttonText}
              icon={buttonIcon}>
            </ion-back-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>,

      // Back button with no text and custom icon
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-back-button text="" icon="add"></ion-back-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>,

      // Danger back button next to a menu button
      <ion-header>
        <ion-toolbar>
          <ion-buttons slot="start">
            <ion-menu-button></ion-menu-button>
            <ion-back-button color="danger"></ion-back-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-header>
    ];
  }
}
```

</TabItem>


<TabItem value="vue">

```html
<template>
  <!-- Default back button -->
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-back-button></ion-back-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <!-- Back button with a default href -->
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-back-button default-href="home"></ion-back-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <!-- Back button with custom text and icon -->
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-back-button
            :text="buttonText"
            :icon="buttonIcon">
        </ion-back-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <!-- Back button with no text and custom icon -->
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-back-button text="" icon="add"></ion-back-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>

  <!-- Danger back button next to a menu button -->
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-menu-button></ion-menu-button>
        <ion-back-button color="danger"></ion-back-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
</template>

<script>
import { IonButtons, IonHeader, IonMenuButton, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  components: { IonButtons, IonHeader, IonMenuButton, IonToolbar }
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