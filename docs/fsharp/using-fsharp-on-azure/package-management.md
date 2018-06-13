---
title: Azure の f# でパッケージの管理の使用
description: パケットを作成または Nuget を使用して、F# で Azure の依存関係を管理するには
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fd9c4a15ab0741d44d6d5cf909b7219d310affb0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566973"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# の Azure の依存関係のためのパッケージ管理

パッケージ マネージャーを使用する場合は、この Azure 開発用のパッケージを取得することは簡単です。 2 つのオプション[パケットを作成](https://fsprojects.github.io/Paket/)と[NuGet](https://www.nuget.org/)です。

## <a name="using-paket"></a>使用するパケットを作成

使用する場合[パケットを作成](https://fsprojects.github.io/Paket/)の依存関係マネージャーとして使用することができます、 `paket.exe` Azure の依存関係を追加するツールです。 例えば:

    > paket add nuget WindowsAzure.Storage

または、使用する場合[モノラル](https://www.mono-project.com/)のクロス プラットフォームの .NET 開発。

    > mono paket.exe add nuget WindowsAzure.Storage

これが追加されます`WindowsAzure.Storage`、現在のディレクトリ内のプロジェクトのパッケージの依存関係のセット、変更、`paket.dependencies`ファイル、およびパッケージをダウンロードします。 依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。

    > paket install

または、Mono 開発。

    > mono paket.exe install

次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。

    > paket update

または、Mono 開発。

    > mono paket.exe update

## <a name="using-nuget"></a>Nuget を使用します。

使用する場合[NuGet](https://www.nuget.org/)の依存関係マネージャーとして使用することができます、 `nuget.exe` Azure の依存関係を追加するツールです。 例えば:

    > nuget install WindowsAzure.Storage -ExcludeVersion

または、Mono 開発。

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

これが追加されます`WindowsAzure.Storage`現在のディレクトリ、およびダウンロード パッケージにプロジェクトのパッケージの依存関係のセットにします。 依存関係、設定されている他の開発者が依存関係が設定されているプロジェクトを使用するかを解決して、ローカルで次のような依存関係をインストールできます。

    > nuget restore 

または、Mono 開発。

    > mono nuget.exe restore

次のように、最新バージョンに、すべてのパッケージの依存関係を更新することができます。

    > nuget update

または、Mono 開発。

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>参照元のアセンブリ

F# スクリプトで、パッケージを使用するのを使用してパッケージに含まれるアセンブリを参照する必要があります、`#r`ディレクティブです。 例えば:

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

ご覧のように、DLL と完全の DLL の名前は必ずしも厳密パッケージ名と同じ相対パスを指定する必要があります。 Framework のバージョンおよび可能性のあるパッケージのバージョン番号、パスが含まれます。 インストールされているすべてのアセンブリを検索するには、Windows のコマンドラインで次のように使用できます。

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

または、Unix のシェルでは、何か次のようにします。

    > find packages/WindowsAzure.Storage -name "*.dll"

これにより、パスにインストールされているアセンブリ。 そこから、フレームワークのバージョンの正しいパスを選択できます。
