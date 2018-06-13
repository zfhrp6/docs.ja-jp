---
title: .NET Core 1.0 のパッケージ依存関係バージョンを管理する方法
description: .NET Core ライブラリとアプリにおけるパッケージの依存関係のバージョン管理について説明します。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 96d154f045303e32de606475e77ab2e6b4f7bcda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211339"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>.NET Core 1.0 のパッケージ依存関係バージョンを管理する方法

この記事では、.NET Core ライブラリとアプリのパッケージ バージョンについて知っておくべき事項を説明します。

## <a name="glossary"></a>用語集

**固定** - 依存関係を固定するとは、NuGet for .NET Core 1.0 でリリースされた同一 "ファミリ" のパッケージを使用することを意味します。

**メタパッケージ** - NuGet パッケージ セットを表す NuGet パッケージです。

**トリミング** - 依存しないパッケージをメタパッケージから削除する動作です。  これは、NuGet パッケージの作成者に関連するものです。  詳細については、「[Reducing Package Dependencies with project.json](../deploying/reducing-dependencies.md)」 (project.json によるパッケージ依存関係の縮小) を参照してください。 

## <a name="fix-your-dependencies-to-net-core-10"></a>依存関係を .NET Core 1.0 に固定する

パッケージを確実に復元して信頼性の高いコードを記述するには、.NET Core 1.0 と共に配布されるパッケージのバージョンに依存関係を固定することが重要です。  すなわち、どのパッケージのバージョンも、修飾子が付加されていない単一バージョンとする必要があるということです。

**1.0 に固定されたパッケージの例**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**1.0 に固定されていないパッケージの例**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>なぜこれが重要なのでしょうか?

.NET Core 1.0 と共に配布されるバージョンに依存関係を固定すると、それらのパッケージはすべて確実に連携して動作します。 使用するパッケージがこのように固定されたものではない場合、パッケージの連携は保証されません。

### <a name="scenarios"></a>シナリオ

.NET Core 1.0 でリリースされたすべてのパッケージとそのバージョンを掲載した一覧が長くても、コードが特定のシナリオに分類されている場合は、一覧を調べなくてもよい場合があります。

`NETStandard.Library`**のみに依存しますか** **?**

そのようにする場合は、`NETStandard.Library` パッケージをバージョン `1.6` に固定する必要があります。  これは選別されたメタパッケージであるため、そのパッケージ クロージャも 1.0 に固定されます。

`Microsoft.NETCore.App`**のみに依存しますか** **?**

そのようにする場合は、`Microsoft.NETCore.App` パッケージをバージョン `1.0.0` に固定する必要があります。  これは選別されたメタパッケージであるため、そのパッケージ クロージャも 1.0 に固定されます。

**または** `Microsoft.NETCore.App` **メタパッケージ依存関係を** [トリミング](../deploying/reducing-dependencies.md) **する必要がありますか?**`NETStandard.Library`

そのようにする場合は、作業を開始するメタパッケージが 1.0 に固定されていることを確認する必要があります。  トリミングした後に依存する個々のパッケージも 1.0 に固定されます。

**または** `Microsoft.NETCore.App` **メタパッケージ** **の外のパッケージに依存しますか?** `NETStandard.Library`

そのようにする場合は、ほかの依存関係を 1.0 に固定する必要があります。  この記事の最後で、適切なパッケージ バージョンを確認し、数値をビルドします。

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>バージョン管理の際の記号文字列 (\*) の使用に関する注意事項

次のように、記号 (\*) 文字列を使用したバージョン管理パターンを採用している場合があるかもしれません`"System.Collections":"4.0.11-*"`。

**これはよくありません**。  記号文字列を使用すると、さまざまなビルドからパッケージが復元される可能性があります。そのなかには、.NET Core 1.0 よりも前のものが含まれる場合があります。  結果として、互換性のないパッケージが存在することになる可能性があります。

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>メタパッケージで整理されるパッケージとバージョン番号

[1.0 用の .NET Standard パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt)。

[1.0 に対するすべてのランタイム パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt)。

[1.0 に対するすべての NET Core アプリケーション パッケージとそのバージョンの一覧](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt)。
