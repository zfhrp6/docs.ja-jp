---
title: "Windows における .NET Core の前提条件 | Microsoft Docs"
description: "Windows コンピューターで .NET Core アプリケーションを開発および実行する場合に必要な依存関係について説明します。"
keywords: ".NET Core, Windows, 前提条件, 依存関係, Visual Studio"
author: mairaw
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 582b7d7f00b939493cea6d8cb4055b6779118c14
ms.contentlocale: ja-jp
ms.lasthandoff: 04/10/2017

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

サポートされるすべてのオペレーティング システムは、[.NET Core のリリース ノート](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)で確認してください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

.NET Core を Windows 10 および Windows Server 2016 よりも前の Windows バージョンで実行する場合、Visual C++ 再頒布可能パッケージが必要です。 この依存関係は、.NET Core インストーラーを使用する場合は自動でインストールされます。 ただし、.NET Core を[インストーラー スクリプト](./tools/dotnet-install-script.md)でインストールしたか、自己完結型の .NET Core アプリケーションを配置する場合は、[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=53840) を手動でインストールする必要があります。

> [!NOTE]
> <em>Windows 7 および Windows Server 2008 コンピューターのみ:</em><br>
> Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/help/2533623) をインストールしていることを確認してください。

## <a name="prerequisites-with-visual-studio-2017"></a>Visual Studio 2017 の前提条件

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 一方、統合開発環境の Windows 上で .NET Core アプリケーションを開発する場合、[Visual Studio 2017](#visual-studio-2017) を使用できます。

> [!IMPORTANT]
> プレビュー バージョンの .NET Core ツールで Visual Studio 2015 を使用できる場合でも、これらのプロジェクトは *project.json* ベースであるため、推奨されなくなりました。 Visual Studio 2017 では、MSBuild に基づくプロジェクト ファイルが使用されます。 この形式変更の詳細については、[変更点の大まかな概要](./tools/cli-msbuild-architecture.md)に関するページをご覧ください。

Visual Studio 2017 を使用して .NET Core アプリを開発する場合は、最新版の Visual Studio をインストールする必要があります。その際、(**[他のツールセット]** セクションで) **プラットフォームに依存しない .NET Core** 開発ツールセットを選択します。
![".NET Core クロスプラットフォームの開発" ワークロードが選択された状態の Visual Studio 2017 インストールのスクリーン ショット](./media/windows-prerequisites/vs_workloads.jpg)

Visual Studio 2017 には複数のエディションがあります。 [Visual Studio Community 2017](https://www.visualstudio.com/downloads/) を無料でダウンロードして始められます。  Visual Studio のインストール プロセスの詳細については、「[Install Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/install-visual-studio)」(Visual Studio のインストール) を参照してください。

Visual Studio 2017 の最新バージョンを実行していることを確認するには、次の操作を行います。

 * [**ヘルプ**] メニューの [**About Microsoft Visual Studio**] (Microsoft Visual Studio のバージョン情報) を選択します。
 * [**Microsoft Visual Studio のバージョン情報**] ダイアログのバージョン番号は、15.0.26228.4 以上である必要があります。

Visual Studio 2017 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes)を参照してください。
