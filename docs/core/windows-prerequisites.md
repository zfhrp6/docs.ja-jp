---
title: ".NET Core の前提条件"
description: ".NET Core の前提条件"
keywords: .NET, .NET Core
author: billwagner
manager: wpickett
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 130b94a745b0e3222e205d8af26194239130ec9c
ms.openlocfilehash: 2e6483b3f1b8b9e1f36a0f4f7377319871fd5674

---

# <a name="prerequisites-for-windows-development"></a>Windows 開発の前提条件

Windows 上で Visual Studio を使用し、.NET Core で開発を行うには、次が必要です。

* サポートされているバージョンの Windows クライアントまたはオペレーティング システム
* Visual Studio 2015 更新プログラム 3.3 以降
* Visual Studio 向け NuGet マネージャーの拡張機能
* .NET Core Tooling Preview 2

## <a name="supported-windows-versions"></a>サポートされている Windows バージョン

.NET Core は、Windows の次のバージョンでサポートされています。

* Windows 7 SP1
* Windows 8.1
* Windows 10
* Windows Server 2008 R2 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 SP1 (フル サーバーまたは Server Core)
* Windows Server 2012 R2 SP1 (フル サーバーまたは Server Core)
* Windows Server 2016 (フル サーバー、Server Core または Nano Server)

[サポートされるすべてのオペレーティング システム](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md#rtm-platform-support)は、[.NET Core のリリース ノート](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md)でご確認ください。

## <a name="net-core-dependencies"></a>.NET Core の依存関係

.NET Core を Windows で実行する場合、VC++ 再頒布可能ファイルが必要です。 これは、.NET Core インストーラーによってインストールされます。 インストーラー スクリプト (`dotnet-install.ps1`) を使用して .NET Core をインストールする場合は、Visual C++ 再頒布可能ファイルを手動でインストールする必要があります。 

Visual C++ 再頒布可能ファイルのバージョンは、Windows のバージョンによって異なります。

* Windows 10
    * [Visual C++ Redistributable for Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
* Windows 7 以降 (Windows 10 は含まず)
    * Windows のインストールが最新であり、Windows Update から修正プログラム [KB2533623](https://support.microsoft.com/en-us/kb/2533623) をインストールしていることを確認してください。
    * [Universal CRT の更新プログラム](https://www.microsoft.com/en-us/download/details.aspx?id=48234) (Universal CRT の詳細については、[このブログの投稿](https://blogs.msdn.microsoft.com/vcblog/2015/03/03/introducing-the-universal-crt/)を参照してください)

## <a name="visual-studio"></a>Visual Studio

.NET Core アプリの開発には、Visual Studio 2015 が必要です。 [Visual Studio Community 2015](https://www.visualstudio.com/downloads/download-visual-studio-vs) は無料でダウンロードできます。 

[Visual Studio 2015 更新プログラム 3.3](https://msdn.microsoft.com/library/mt752379.aspx) を実行していることを確認します。

* [**ヘルプ**] メニューの **「About Microsoft Visual Studio」** (Microsoft Visual Studio のバージョン情報) を選択します。
* **「About Microsoft Visual Studio」** (Microsoft Visual Studio のバージョン情報) ダイアログ ボックスのバージョン番号が 14.0.25424.00 以上であり、"更新プログラム 3" が含まれている必要があります。
* 更新プログラム 3 が含まれていない場合、まず [Visual Studio 2015 の更新プログラム 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs) をダウンロードしてインストールする必要があります。
* 更新プログラム 3 がインストールされているが、バージョン番号が 14.0.25424.00 よりも小さい場合、[Visual Studio 2015 更新プログラム 3.3](https://msdn.microsoft.com/library/mt752379.aspx) をダウンロードしてインストールする必要があります。

更新プログラム 3 での変更の詳細については、[リリース ノート](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)を参照してください。

## <a name="nuget-manager-extension-for-visual-studio"></a>Visual Studio 向け NuGet マネージャーの拡張機能

NuGet は、.NET Core などの Microsoft 開発プラットフォーム用のパッケージ マネージャーです。 .NET Core アプリを構築するには、[NuGet 3.5.0](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 以上が必要です。

## <a name="net-core-tools-for-visual-studio-2015"></a>Visual Studio 2015 用の .NET Core のツール

[.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk] をダウンロードし、インストールします。 

.NET Core ツール パッケージにより、Visual Studio 2015 用の .NET Core、プロジェクト テンプレートおよびその他のツールがインストールされます。

> [!NOTE]
現時点では、[.NET Core 1.0.1 - VS 2015 Tooling Preview 2][sdk] のオフライン インストーラーはダウンロードできません。 代わりに、[正規のブートストラップ] [sdk] をダウンロードし、(`/layout c:\path` などの) コマンド ライン オプションを使用してオフラインのレイアウトを取得します。 その後、実行可能ファイルをローカル パスから実行し、オフラインのインストーラーとして使用します。 なお、これは完全なレイアウトであるため、この手順によって、約 1 GB のサポート対象のすべての言語のすべてのパッケージがダウンロードされます。

[sdk]: https://go.microsoft.com/fwlink/?LinkID=827546



<!--HONumber=Nov16_HO3-->


