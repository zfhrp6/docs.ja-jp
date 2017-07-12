---
title: ".NET Core SDK 概要 | Microsoft Docs"
description: ".NET Core SDK 概要"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 26bc9822-e42b-48ec-b0d6-499dc604add7
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 1b05b7e1a2d274f02cd1222c0a90a59583d37e92
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---

<a id="net-core-sdk-overview" class="xliff"></a>

# .NET Core SDK 概要 

<a id="introduction" class="xliff"></a>

## はじめに
.NET Core ソフトウェア開発キット (SDK) は一連のライブラリとツールであり、開発者はこれを利用して .NET Core のアプリケーションやライブラリを作成できます。 開発者にとって利用する機会の多いパッケージです。 

次の要素で構成されています。

1. アプリケーションの作成に使用される .NET Core コマンド ライン ツール
2. アプリケーションを作成し、実行するための .NET Core (ライブラリとランタイム)
3. [CLI コマンド](tools/index.md)を実行し、アプリケーションを実行するための `dotnet` ドライバー


<a id="acquiring-the-net-core-sdk" class="xliff"></a>

## .NET Core SDK を入手する
他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。 シナリオにもよりますが、ネイティブ インストーラーで SDK をインストールしたり、インストール シェル スクリプトを利用したりできます。

開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。 SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。 これらのインストーラーは、インストール直後、ユーザーが SDK を使用するために必要とする環境をインストールし、設定します。 ただし、コンピューター上で管理者特権も必要になります。 インストール手順は、[.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)で確認できます。

一方で、インストール スクリプトの場合、管理者特権は必要ありません。 ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。 スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。 詳細については、[インストール スクリプト参照](tools/dotnet-install-script.md)に関するトピックを参照してください。 CI ビルド サーバーで SDK を設定する方法については、「[SDK with CI servers](tools/using-ci-with-cli.md)」というドキュメントをご覧ください。 

既定では、SDK は "SxS" (side-by-side/横並び) 方式でインストールを実行します。 つまり、1 台のコンピューター上で複数のバージョンの CLI ツールが共存できます。 正しいバージョンを使用する方法については、.NET Core コマンド ライン ツール トピックの[ドライバー セクション](tools/index.md#driver)を参照してください。

