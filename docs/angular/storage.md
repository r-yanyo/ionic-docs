---
title: データストレージ
sidebar_label: ストレージ
---

<head>
  <title>Angular App Data Storage Options - Ionic Documentation</title>
  <meta
    name="description"
    content="A variety of options are available for storing data within Ionic apps made using Angular. Read our documentation for Ionic Secure Storage and @ionic/storage."
  />
</head>

Ionicアプリ内にデータを保存するためのさまざまなオプションを用意しています。

Here are two official Ionic options:

## Ionic Secure Storage

For teams building mission-critical apps or requiring encryption support, [Ionic Secure Storage](https://ionic.io/docs/secure-storage) is an official premium solution from the Ionic team that provides a cross-platform data storage system that works on iOS and Android.

It makes it easy to build high performance, offline-ready Ionic apps across iOS, Android, and the web.

[Learn more](https://ionic.io/products/secure-storage)

## @ionic/storage

For developers not requiring encryption nor relational data support, [@ionic/storage](https://github.com/ionic-team/ionic-storage) is an open source key/value API for building apps that work across storage engines on multiple platforms.

Additionally, Ionic Secure Storage has a driver that works with the key/value API in `@ionic/storage` while providing encryption and SQLite support.

Learn more about [@ionic/storage](https://github.com/ionic-team/ionic-storage)
