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
ms.sourcegitcommit: a8019c9fc25ef458aa555743e61cd83a3beb11ed
ms.openlocfilehash: b5c088da7d1155414a08995ae0d72154af891190

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

## <a name="prerequisites-with-visual-studio"></a>Visual Studio の前提条件

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 一方、Windows 上で Visual Studio を使用して .NET Core アプリケーションを開発する場合、使用可能なバージョンは次の 2 つです。

* [Visual Studio 2015](#visual-studio-2015)
* [Visual Studio 2017 RC](#visual-studio-2017-rc)

プロジェクトのベースは、Visual Studio 2015 を使用して作成した場合は既定で project.json になりますが、Visual Studio 2017 RC を使用した場合は常に MSBuild です。 この形式変更の詳細については、[変更点の大まかな概要](./preview3/tools/layering.md)に関するページをご覧ください。

### <a name="visual-studio-2015"></a>Visual Studio 2015

Visual Studio 2015 を使用して .NET Core アプリを開発する場合は、次のものが必要です。

* Visual Studio 2015 更新プログラム 3.3 以降

   Visual Studio 2015 には複数の[エディション](https://www.visualstudio.com/vs/compare)があります。 [Visual Studio Community 2015](https://www.visualstudio.com/downloads/) を無料でダウンロードして始められます。 

   [Visual Studio 2015 更新プログラム 3.3](https://msdn.microsoft.com/library/mt752379.aspx) を実行していることを確認するには、以下を実行します。

   * [**ヘルプ**] メニューの [**About Microsoft Visual Studio**] (Microsoft Visual Studio のバージョン情報) を選択します。
   * **「About Microsoft Visual Studio」** (Microsoft Visual Studio のバージョン情報) ダイアログ ボックスのバージョン番号が 14.0.25424.00 以上であり、"更新プログラム 3" が含まれている必要があります。
   * 更新プログラム 3 が含まれていない場合、まず [Visual Studio 2015 の更新プログラム 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs) をダウンロードしてインストールする必要があります。
   * 更新プログラム 3 がインストールされているが、バージョン番号が 14.0.25424.00 よりも小さい場合、[Visual Studio 2015 更新プログラム 3.3](https://msdn.microsoft.com/library/mt752379.aspx) をダウンロードしてインストールする必要があります。

   更新プログラム 3 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)を参照してください。

* Visual Studio 向け NuGet マネージャーの拡張機能

   NuGet は、.NET Core などの Microsoft 開発プラットフォーム用のパッケージ マネージャーです。 .NET Core アプリを構築するには、[NuGet 3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 以上が必要です。

* .NET Core Tooling Preview 2

   [.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk] をダウンロードし、インストールします。 

   .NET Core ツール パッケージにより、Visual Studio 2015 用の .NET Core、プロジェクト テンプレートおよびその他のツールがインストールされます。

   > [!NOTE]
   > 現時点では、[.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk] のオフライン インストーラーはダウンロードできません。 代わりに、[正規のブートストラップ][sdk]をダウンロードし、コマンドライン オプション (`/layout c:\path` など) を使用してオフラインのレイアウトを取得する必要があります。 その後、実行可能ファイルをローカル パスから実行し、オフラインのインストーラーとして使用します。 なお、これは完全なレイアウトであるため、この手順によって、約 1 GB のサポート対象のすべての言語のすべてのパッケージがダウンロードされます。

### <a name="visual-studio-2017-rc"></a>Visual Studio 2017 RC

Visual Studio 2017 RC を使用して .NET Core アプリを開発する場合は、Visual Studio RC の最新バージョンをインストールし、".NET Core および Docker (プレビュー)" ワークロードを選択する必要があります。 

Visual Studio 2017 RC には複数のエディションがあります。 [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/#downloadvs) を無料でダウンロードして始められます。  Visual Studio のインストール プロセスの詳細については、「[Install Visual Studio 2017 RC](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio)」(Visual Studio のインストール) を参照してください。

Visual Studio 2017 RC の最新バージョンを実行していることを確認するには、次の操作を行います。

* [**ヘルプ**] メニューの [**About Microsoft Visual Studio**] (Microsoft Visual Studio のバージョン情報) を選択します。
* **[Microsoft Visual Studio のバージョン情報]** ダイアログ ボックスのバージョン番号が 15.0.26020.0 以上である必要があります。

Visual Studio 2017 RC での変更の詳細については、[リリース ノート](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)を参照してください。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546



<!--HONumber=Jan17_HO4-->


