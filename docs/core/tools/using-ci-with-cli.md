---
title: "継続的インテグレーション (CI) で .NET Core SDK とツールを使用する | Microsoft Docs"
description: "継続的インテグレーション (CI) で .NET Core SDK とツールを使用する"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 0579d59e8da24428d9e174baf0cc865d62c08195
ms.lasthandoff: 03/07/2017

---

# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>継続的インテグレーション (CI) で .NET Core SDK とツールを使用する

## <a name="overview"></a>概要
このドキュメントでは、ビルド サーバーでの .NET Core SDK とそのツールの使用方法について説明します。 一般に、CI ビルド サーバーでは、何らかの方法でインストールを自動化することが望まれます。 可能な限り自動化に管理者特権を必要としないことが理想的です。 

SaaS CI ソリューションの場合、いくつかのオプションがあります。 このドキュメントでは、非常に一般的な&2; つのオプションである [TravisCI](https://travis-ci.org/) と [AppVeyor](https://www.appveyor.com/) について説明します。 もちろん、他にも多くのサービスがありますが、インストールと使用のメカニズムはどれも似ています。

## <a name="installation-options-for-ci-build-servers"></a>CI ビルド サーバーのインストール オプション

## <a name="using-the-native-installers"></a>ネイティブ インストーラーの使用
管理者特権が必要なインストーラーを使用しても問題がない場合は、各プラットフォーム用のネイティブ インストーラーをビルド サーバーの設定に使用できます。 この方法には (特に Linux ビルド サーバーの場合)、SDK の実行に必要な依存関係が自動的にインストールされるという&1; つの利点があります。 ネイティブ インストーラーはシステム全体バージョンの SDK もインストールし、これは望ましい場合があります。そうでない場合は、以下で説明する[インストーラー スクリプトの使用](#using-the-installer-script)を検討する必要があります。 

このアプローチは簡単に使用できます。 Linux では、フィードに基づくパッケージ マネージャー (Ubuntu の `apt-get` または CentOS の `yum`) を使用するか、パッケージ自体 (DEB または RPM) を使用します。 前者の場合は、パッケージを含むフィードの設定が必要です。

Windows プラットフォームの場合は、MSI を使用できます。 

すべてのバイナリは、最新の安定したリリースを集めた [.NET Core の概要ページ](https://aka.ms/dotnetcoregs)で見つかります。 さらに新しい (安定していない可能性がある) リリースまたは最新版を使用する場合は、[CLI リポジトリ](https://github.com/dotnet/cli)からのリンクを使用できます。 

## <a name="using-the-installer-script"></a>インストーラー スクリプトの使用
インストーラー スクリプトを使用すると、管理者特権を必要としないインストールをビルド サーバーで実行できます。 また、非常に簡単に自動化できます。 スクリプト自体が、必要な ZIP/tarball ファイルをダウンロードして展開します。また、ローカル コンピューター上のインストール場所を PATH に追加して、インストール後すぐにツールを使用できるようにします。 

インストーラー スクリプトは、ビルドの開始時に簡単に自動化し、SDK の必要なバージョンを取得してインストールできます。 "必要なバージョン" とは、ビルドされるアプリケーションで必要なバージョンです。 SDK をローカルにインストールし、ビルド完了後にクリーンアップできるように、インストール パスを選択できます。 ビルド プロセスにカプセル化とアトミック性が追加されます。 

インストール スクリプトのリファレンス情報は、[dotnet-install](dotnet-install-script.md) のドキュメントにあります。 

### <a name="dealing-with-the-dependencies"></a>依存関係の処理
インストーラー スクリプトを使用すると、ネイティブな依存関係は自動的にインストールされず、インストールしているオペレーティング システムにまだない場合は手動でインストールする必要があります。 前提条件の一覧は、[CLI リポジトリ](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をご覧ください。 

## <a name="ci-services-setup-examples"></a>CI サービスのセットアップの例
以下のセクションでは、説明した CI SaaS 製品を使用した構成の例を示します。 

### <a name="travisci"></a>TravisCI

[travis-ci](https://travis-ci.org/) は、`csharp` 言語と `dotnet` キーを使用して .NET Core SDK をインストールするように構成できます。

次のものだけを使用します。

```yaml
dotnet: 1.0.0-preview2-003121
```

Travis は、ビルド マトリックスの `osx` (OS X 10.11) と `linux` (Ubuntu 14.04 ) の両方のジョブを実行できます。詳細については、[example .travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) をご覧ください。

### <a name="appveyor"></a>AppVeyor

[appveyor.com ci](https://www.appveyor.com/) では、.NET Core SDK preview2 がビルド ワーカー イメージ `Visual Studio 2015` に既にインストールされています。

次のものだけを使用します。

```yaml
os: Visual Studio 2015
```

特定のバージョンの .NET Core SDK をインストールできます。詳細については、[appveyor.yml の例](https://github.com/dotnet/docs/blob/master/appveyor.yml)をご覧ください。 

この例では、.NET Core SDK バイナリがダウンロードされ、サブディレクトリに解凍されて、`PATH` 環境変数に追加されます。

複数バージョンの .NET Core SDK との統合テストを実行するために、ビルド マトリックスを追加できます。

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.0-preview2-003121
    - CLI_VERSION: Latest

install:
  # .NET Core SDK binaries
  - ps: $url = "https://dotnetcli.blob.core.windows.net/dotnet/preview/Binaries/$($env:CLI_VERSION)/dotnet-dev-win-x64.$($env:CLI_VERSION.ToLower()).zip"
  # follow normal installation from binaries
```
