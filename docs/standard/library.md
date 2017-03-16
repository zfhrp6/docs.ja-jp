---
title: .NET Standard Library
description: .NET Standard Library
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
translationtype: Human Translation
ms.sourcegitcommit: 519253bd6dc105afb138268c62347c29a6072fbb
ms.openlocfilehash: f681b1663d1a2e6c2fbbd1cc415290d26bbbe429
ms.lasthandoff: 03/07/2017

---

# <a name="net-standard-library"></a>.NET Standard Library

.NET Standard Library は、すべての .NET ランタイムで使用できるようにすることを目的とした .NET API の正式な仕様です。 Standard Library の背後にある動機は、.NET エコシステムの高度な統一性を確立することです。 [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) は引き続き .NET ランタイムの動作の統一性を確立しますが、.NET ライブラリの実装用の .NET 基底クラス ライブラリ (BCL) に同様の仕様はありません。 

.NET Standard Library により、次の主なシナリオが可能になります。 

- ワークロードに関係なく、すべての .NET プラットフォーム用に統一された BCL API のセットを定義し、実装する。
- 開発者が、この同じ API のセットを使用して、.NET ランタイム間で使用可能なポータブル ライブラリを生成できるようにする。
- .NET API による共有ソースの条件付きコンパイルを削減するか、できればなくし、OS API に対してのみにする。

さまざまな .NET ランタイムが、.NET Standard Library の特定のバージョンを実装します。 各 .NET ランタイム バージョンは、それがサポートしている最高の .NET Standard バージョンをアドバタイズし、そのことは以前のバージョンもサポートしていることを意味します。 たとえば、.NET Framework 4.6 は .NET Standard Library 1.3 を実装しており、このことは、.NET Standard Library のバージョン 1.0 ～ 1.3 で定義されているすべての API を公開していることを意味します。 同様に、.NET Framework 4.6.2 は.NET Standard Library 1.5 を実装し、.NET Core 1.0 は .NET Standard Library 1.6 を実装しています。

## <a name="net-platforms-support"></a>.NET Platform のサポート

.NET Standard Library をサポートしているすべての .NET ランタイムのセットを確認できます。

| プラットフォーム名 | Alias |  |  |  |  |  | | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 | 2.0 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|2.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|vNext|4.6.1|
|Mono/Xamarin プラットフォーム||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|vNext|
|ユニバーサル Windows プラットフォーム|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|&rarr;|&rarr;|vNext|
|Windows|win|&rarr;|8.0|8.1||||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1||||||
|Windows Phone Silverlight|wp|8.0||||||||

## <a name="comparison-to-portable-class-libraries"></a>ポータブル クラス ライブラリとの比較

.NET Standard Library は、次世代の[ポータブル クラス ライブラリ (PCL)](https://msdn.microsoft.com/library/gg597391.aspx) と考えることができます。 .NET Standard Library は、標準 BCL を精選し、結果として、.NET ランタイム間で高度な統一性を確立することによって、ポータブル ライブラリの作成の方法を向上しています。 .NET Standard Library を対象とするライブラリは、PCL つまり ".NET Standard ベースの PCL" です。 既存の PCL は、"プロファイルベースの PCL" です。

.NET Standard Library と PCL プロファイルは、似たような目的で作成されましたが、主な点が異なります。

類似点:

- バイナリ コード共有に使用できる API を定義します。

相違点:

- .NET Standard Library は精選された API のセットで、PCL プロファイルは、既存のプラットフォームの交差部分によって定義されています。
- .NET Standard Library は線形的にバージョン管理されていますが、PCL プロファイルはそうではありません。
- PCL プロファイルはマイクロソフトのプラットフォームを表し、.NET Standard Library はプラットフォームに依存しません。

## <a name="specification"></a>指定

.NET Standard Library の仕様は、標準化された API のセットです。 この仕様は、.NET ランタイムの実装、具体的には Microsoft (.NET Framework、.NET Core、Mono を含む) と Unity によって管理されています。 新しい .NET Standard Library のバージョンの構築の一環として、公開フィードバック プロセスが使われています。

### <a name="official-artifacts"></a>正式な成果物

正式な仕様は標準に含まれる API を定義する一連の .cs ファイルです。 各[コンポーネント](https://github.com/dotnet/corefx/tree/master/src) の [ref ディレクトリ](https://github.com/dotnet/corefx/tree/master/src/System.Runtime/ref) に.NET Standard Library API が定義されています。 ref 成果物は [CoreFX リポジトリ](https://github.com/dotnet/corefx)内に存在しますが、それらは .NET Core 固有ではありません。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) メタパッケージ ([ソース](https://github.com/dotnet/corefx/blob/master/pkg/NETStandard.Library/NETStandard.Library.packages.targets)) は、1 つ以上の.NET Standard Library のバージョンを定義する (一部) ライブラリのセットについて説明しています。

System.Runtime などの特定のコンポーネントは、次のように説明されています。

- .NET Standard Library の一部 (そのスコープだけ)。
- そのスコープの.NET Standard Library の複数のバージョン。

便利に読めるようにし、特定の開発者シナリオ (コンパイラを使用するなど) を可能にするために、派生成果物が提供されています。

- マークダウンの API 一覧 (TBD)
- [NuGet パッケージ](../core/packages.md)として配布され、[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) メタパッケージによって参照される参照アセンブリ。

### <a name="package-representation"></a>パッケージ表現

.NET Standard Library 参照アセンブリの主要な配布手段は [NuGet パッケージ](../core/packages.md)です。 実装は、各 .NET ランタイムに適切なさまざまな方法で配布されます。

NuGet パッケージは&1; つまたは複数の[フレームワーク](frameworks.md)を対象にしています。 .NET Standard Library パッケージは、".NET Standard" フレームワークを対象にしています。 `netstandard` [compact TFM](frameworks.md) (`netstandard1.4` など) を使用して、.NET Standard Framework を対象にすることができます。 複数のランタイムでの実行を意図したライブラリは、このフレームワークを対象とする必要があります。 

`NETStandard.Library` メタパッケージは .NET Standard Library を定義する NuGet パッケージの完全なセットを参照しています。  `netstandard` を対象とする最も一般的な方法は、このメタパッケージを参照することです。 それは、.NET Standard Library を定義する約&40; の .NET ライブラリと関連する API について説明しており、それらにアクセスできるようにしています。 `netstandard` を対象とする追加のパッケージを参照して、追加の API にアクセスできます。 

### <a name="versioning"></a>バージョン管理

仕様は&1; つだけではありませんが、段階的に拡張され、直線的にバージョン管理された API のセットです。 標準の最初のバージョンは、API のベースライン セットを構築しています。 それ以降のバージョンでは、API が追加され、以前のバージョンによって定義された API を継承しています。 標準から API を削除するために確立された取り決めはありません。

.NET Standard Library は、1 つの .NET ランタイムに固有ではなく、それらのランタイムのいずれかのバージョン管理スキームに一致することもありません。

いずれかのランタイム (.NET Framework、.NET Core、Mono など) に追加された API は、本質的に基本的であると考えられる場合に、仕様に追加される候補とみなされる可能性があります。 新しい[.NET Standard Library のバージョン](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md#list-of-net-corefx-apis-and-their-associated-net-platform-standard-version) は、.NET ランタイムのリリースに基づいて作成されるので、.NET Standard PCL から新しい API を対象にすることができます。 バージョン管理メカニズムの詳細は、「[.NET Core Versioning](../core/versions/index.md)」(.NET Core のバージョン管理) で説明されています。

.NET Standard Library のバージョン管理は、使用する場合に重要です。 .NET Standard Library のバージョンが指定されている場合、それと同じか以下のバージョンを対象とするライブラリを使用できます。 次の方法では、.NET Standard Library の対象設定に固有の、.NET Standard Library PCL の使用のワークフローを説明します。

- PCL に使用する .NET Standard Library のバージョンを選択します。
- .NET Standard Library と同じかそれ以下のバージョンに依存するライブラリを使用します。
- それより上の .NET Standard Library バージョンに依存するライブラリを見つけた場合は、それと同じバージョンを採用するか、そのライブラリを使用しないようにする必要があります。

### <a name="pcl-compatibility"></a>PCL 互換性

.NET Standard Library は、PCL プロファイルのサブセットと互換性があります。 .NET Standard Library 1.0、1.1、1.2 はそれぞれ PCL プロファイルのセットと重複します。 この重複は&2; つの理由で作成されました。

- .NET Standard ベースの PCL がプロファイルベースの PCL を参照できるようにする。
- プロファイルベースの PCL を .NET Standard ベースの PCL としてパッケージできるようにする。

プロファイルベースの PCL の互換性は、[Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet パッケージで提供されています。 プロファイルベースの PCL を含む NuGet パッケージを参照するときに、この依存関係が必要です。

`netstandard` としてパッケージされたプロファイルベースの PCL は、通常パッケージされるプロファイルベースの PCL より使いやすくなります。 `netstandard` パッケージは、既存のユーザーと互換性があります。

標準 .NET と互換性がある PCL プロファイルのセットを確認できます。 

| Profile | .NET Platform Standard バージョン |
| ---------| --------------- |
| Profile7  .NET ポータブル サブセット (.NET Framework 4.5、Windows 8) | 1.1 |
| Profile31 .NET ポータブル サブセット (Windows 8.1、Windows Phone Silverlight 8.1)| 1.0 |
| Profile32 .NET ポータブル サブセット (Windows 8.1、Windows Phone 8.1) | 1.2 |
| Profile44 .NET ポータブル サブセット (.NET Framework 4.5.1、Windows 8.1) | 1.2 |
| Profile49 .NET ポータブル サブセット (.NET Framework 4.5、Windows Phone Silverlight 8) | 1.0 |
| Profile78 .NET ポータブル サブセット (.NET Framework 4.5、Windows 8、Windows Phone Silverlight 8) | 1.0 |
| Profile84 .NET ポータブル サブセット (Windows Phone 8.1、Windows Phone Silverlight 8.1) | 1.0 |
| Profile111 .NET ポータブル サブセット (.NET Framework 4.5、Windows 8、Windows Phone 8.1) | 1.1 |
| Profile151 .NET ポータブル サブセット (.NET Framework 4.5.1、Windows 8.1、Windows Phone 8.1) | 1.2 |
| Profile157 .NET ポータブル サブセット (Windows 8.1、Windows Phone 8.1、Windows Phone Silverlight 8.1) | 1.0 |
| Profile259 .NET ポータブル サブセット (.NET Framework 4.5、Windows 8、Windows Phone 8.1、Windows Phone Silverlight 8) | 1.0 |

## <a name="targeting-net-standard-library"></a>.NET Standard Library を対象とする

`netstandard` フレームワークと NETStandard.Library メタパッケージの組み合わせを使用して、[.NET Standard Library をビルド](../core/tutorials/libraries.md)できます。 [.NET Core ツールを使用して .NET Standard Library を対象とする](../core/packages.md)例を参照できます。

