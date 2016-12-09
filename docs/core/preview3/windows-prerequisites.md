---
title: ".NET Core の前提条件 (Preview 3 ツール)"
description: ".NET Core の前提条件 (Preview 3 ツール)"
keywords: .NET, .NET Core
author: billwagner
ms.author: wiwagn
ms.date: 09/15/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
translationtype: Human Translation
ms.sourcegitcommit: 07b62bd7163193eff8dc8f61fda7a45a924bba2b
ms.openlocfilehash: ee4ccba7c06f0a7f67e3fe59c885febf895235fd

---

# <a name="prerequisites-for-windows-development-preview-3-tooling"></a>Windows 開発の前提条件 (Preview 3 ツール)

Windows 上で Visual Studio を使用し、.NET Core で開発を行うには、次が必要です。

* サポートされているバージョンの Windows クライアントまたはオペレーティング システム
* Visual Studio 2017 RC 以降
* .NET Core Tooling Preview 3

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

.NET Core アプリは任意のエディターで .NET Core コマンドライン ツールを使用して開発できますが、Visual Studio と .NET Core ツールのPreview 3 を使用する場合は、Visual Studio 2017 RC 以降が必要になります。 [Visual Studio Community 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) は無料でダウンロードできます。 

次のように、Visual Studio 2017 RC を実行していることを確認します。

* [**ヘルプ**] メニューの [**About Microsoft Visual Studio**] (Microsoft Visual Studio のバージョン情報) を選択します。
* **[Microsoft Visual Studio のバージョン情報]** ダイアログ ボックスのバージョン番号が 15.0.25831.1 以上である必要があります。

Visual Studio 2017 RC での変更の詳細については、[リリース ノート](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes)を参照してください。

セットアップ中に ".NET Core と Docker (Preview)" のワークロードをインストールしたことを確認します。 インストールしていない場合は、再度セットアップを実行して選択できます。



<!--HONumber=Nov16_HO3-->


