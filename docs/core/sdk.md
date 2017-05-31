---
title: ".NET Core SDK 概要"
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
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 5ecc2dd249ab0e1e25e2fcaa4f7548f91085e54a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/10/2017

---

# <a name="net-core-sdk-overview"></a>.NET Core SDK 概要 

## <a name="introduction"></a>はじめに
.NET Core ソフトウェア開発キット (SDK) は一連のライブラリとツールであり、開発者はこれを利用して .NET Core のアプリケーションやライブラリを作成できます。 開発者にとって利用する機会の多いパッケージです。 

次の要素で構成されています。

1. アプリケーションの作成に使用される .NET Core コマンド ライン ツール
2. アプリケーションを作成し、実行するための .NET Core (ライブラリとランタイム)
3. [CLI コマンド](tools/index.md)を実行し、アプリケーションを実行するための `dotnet` ドライバー


## <a name="acquiring-the-net-core-sdk"></a>.NET Core SDK を入手する
他のツールと同様に、最初にコンピューターにツールをインストールする必要があります。 シナリオにもよりますが、ネイティブ インストーラーで SDK をインストールしたり、インストール シェル スクリプトを利用したりできます。

開発者のコンピューターでは、ネイティブ インストーラーが利用されることが多いです。 SDK はサポートされるプラットフォームのネイティブ インストール メカニズムにより配信されます。たとえば、Ubuntu の場合は DEB パッケージ、Windows の場合は MSI バンドルです。 これらのインストーラーは、インストール直後、ユーザーが SDK を使用するために必要とする環境をインストールし、設定します。 ただし、コンピューター上で管理者特権も必要になります。 インストール手順は、[.NET Core のインストール ガイド](https://aka.ms/dotnetcoregs)で確認できます。

一方で、インストール スクリプトの場合、管理者特権は必要ありません。 ただし、いかなる前提条件もコンピューターにインストールされません。前提条件はすべてユーザーが手動でインストールする必要があります。 スクリプトは、通常、管理者特権なしでツールをインストールするとき、ビルド サーバーを設定するために利用されます (上の前提条件警告に注意してください)。 詳細については、[インストール スクリプト参照](tools/dotnet-install-script.md)に関するトピックを参照してください。 CI ビルド サーバーで SDK を設定する方法については、「[SDK with CI servers](tools/using-ci-with-cli.md)」というドキュメントをご覧ください。 

既定では、SDK は "SxS" (side-by-side/横並び) 方式でインストールを実行します。 つまり、1 台のコンピューター上で複数のバージョンの CLI ツールが共存できます。 正しいバージョンを使用する方法については、.NET Core コマンド ライン ツール トピックの[ドライバー セクション](tools/index.md#driver)を参照してください。
