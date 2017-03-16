---
title: "Windows における .NET Core の前提条件 | Microsoft Docs"
description: "Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。"
keywords: ".NET Core, Windows, 前提条件, 依存関係, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 01/05/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: e374b924bf78d62227cb9607641130dfd9128186
ms.openlocfilehash: 6383a0ce253f6f7000ed8a81b29b9e1d58914acc
ms.lasthandoff: 03/06/2017

---

# <a name="prerequisites-for-net-core-on-windows"></a>Windows における .NET Core の前提条件

この記事では、.NET Core アプリケーションを Windows コンピューターで展開および実行、ならびに Visual Studio を使用して開発するのに必要となる依存関係について説明します。

## <a name="supported-windows-versions"></a>サポートされている Windows バージョン

.NET Core は、Windows の次のバージョンでサポートされています。

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 R2 SP1 (フル サーバーまたは Server Core)
* Windows Server 2016 (フル サーバー、Server Core または Nano Server)

[サポートされるすべてのオペレーティング システム](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support)については、[.NET Core 1.0.0 のリリース ノート](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md)でご確認ください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

.NET Core を Windows 10 および Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。 この依存関係は、.NET Core インストーラーを使用する場合は自動でインストールされます。 ただし、.NET Core を[インストーラー スクリプト](https://docs.microsoft.com/en-us/dotnet/articles/core/tools/dotnet-install-script)でインストールしたか、自己完結型の .NET Core アプリケーションをデプロイする場合は、[Visual Studio 2015 の Visual C++ 再頒布可能パッケージ](https://www.microsoft.com/en-us/download/details.aspx?id=48145)を手動でインストールする必要があります。

> [!NOTE]
> <em>Windows 7 および Windows Server 2008 コンピューターのみ:</em><br>
> Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/en-us/kb/2533623) をインストールしていることを確認してください。

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 の前提条件

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 一方、統合開発環境の Windows 上で .NET Core アプリケーションを開発する場合、[Visual Studio 2017](#visual-studio-2017) を使用できます。

Visual Studio 2017 を使用して .NET Core アプリを開発する場合は、最新版の Visual Studio をインストールする必要があります。その際、(**[他のツールセット]** セクションで) **プラットフォームに依存しない .NET Core **開発ツールセットを選択します。

Visual Studio 2017 には複数のエディションがあります。 [Visual Studio Community 2017](https://www.visualstudio.com/vs/visual-studio-2017/#downloadvs) を無料でダウンロードして始められます。  Visual Studio のインストール プロセスの詳細については、「[Install Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio)」(Visual Studio のインストール) を参照してください。

Visual Studio 2017 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)を参照してください。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546
