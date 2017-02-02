---
title: "csproj リファレンス | .NET Core SDK"
description: "既存の csproj ファイルと .NET Core の csproj ファイルの違いについて説明します"
keywords: "リファレンス, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 1a0178cc5763f06213d45b9b3826c56ce970776c

---

# <a name="additions-to-csproj-format-for-net-core"></a>.NET Core の csproj 形式に追加されたもの

ここでは、project.json から csproj および [MSBuild](https://github.com/Microsoft/MSBuild) への移行に伴って csproj ファイルに追加された変更について説明します。 **非コア csproj ファイルに対する差分についてのみ**説明します。 一般的なプロジェクト ファイルの構文とリファレンスの詳細が必要な場合は、[MSBuild プロジェクト ファイル]()のドキュメントをご覧ください。 

> ![注] このドキュメントの内容は今後増えるので、ときどき新しい追加項目を確認してください。 

## <a name="additions"></a>追加

### <a name="packagereference"></a>PackageReference
プロジェクトでの NuGet の依存関係を指定します。 `Include` 属性は、パッケージ ID を指定します。 

```xml
<PackageReference Include="<package-id>">
    <Version></Version>
    <PrivateAssets></PrivateAssets>
    <IncludeAssets></IncludeAssets>
    <ExcludeAssets></ExcludeAssets>
</PackageReference>
```

#### <a name="version"></a>バージョン
`<Version>` は、復元するパッケージのバージョンを指定します。 要素は、NuGet のバージョン管理スキームの規則に従います。

#### <a name="includeassets"></a>IncludeAssets
`<IncludeAssets>` 子要素は、親の `<PackageReference>` で指定されているパッケージに属するアセットで、使う必要があるものを指定します。 

要素には、次の値の 1 つ以上を含めることができます。

* Compile - コンパイルで使用できる lib フォルダーの内容です
* Runtime - 配布する runtime フォルダーの内容です
* ContentFiles - 使用する contentfiles フォルダーの内容です
* Build - 使用する build フォルダーのプロパティ/ターゲットです
* Native - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です
* Analyzers - 使用するアナライザーです

代わりに、次の値を要素に含めることもできます。

* None - これらのいずれも使用しません
* All - これらのものをすべて使用します

#### <a name="excludeassets"></a>ExcludeAssets
`<ExcludeAssets>` 子要素は、親の `<PackageReference>` で指定されているパッケージに属するアセットで、使ってはならないものを指定します。

要素には、次の値の 1 つ以上を含めることができます。

* Compile - コンパイルで使用できる lib フォルダーの内容です
* Runtime - 配布する runtime フォルダーの内容です
* ContentFiles - 使用する contentfiles フォルダーの内容です
* Build - 使用する build フォルダーのプロパティ/ターゲットです
* Native - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です
* Analyzers - 使用するアナライザーです

代わりに、次の値を要素に含めることもできます。

* None - これらのいずれも使用しません
* All - これらのものをすべて使用します

#### <a name="privateassets"></a>PrivateAssets
`<PrivateAssets>` 子要素は、親の `<PackageReference>` で指定されているパッケージに属するアセットで、使う必要はあるが、次のプロジェクトに渡してはならないものを指定します。 

> [!NOTE]
> これは、project.json/xproj の `SuppressParent` 要素に対する新しい用語です。 

要素には、次の値の 1 つ以上を含めることができます。

* Compile - コンパイルで使用できる lib フォルダーの内容です
* Runtime - 配布する runtime フォルダーの内容です
* ContentFiles - 使用する contentfiles フォルダーの内容です
* Build - 使用する build フォルダーのプロパティ/ターゲットです
* Native - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です
* Analyzers - 使用するアナライザーです

代わりに、次の値を要素に含めることもできます。

* None - これらのいずれも使用しません
* All - これらのものをすべて使用します

### <a name="dotnetclitoolreference"></a>DotnetCliToolReference
`<DotnetCliToolReference>` 要素は、プロジェクトのコンテキストでユーザーが復元を望む CLI ツールを指定します。 `project.json` の `tools` ノードに代わるものです。 

#### <a name="version"></a>バージョン
`<Version>` は、復元するパッケージのバージョンを指定します。 要素は、NuGet のバージョン管理スキームの規則に従います。

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers
`<RuntimeIdentifiers>` 要素では、プロジェクトの[ランタイム識別子](../../rid-catalog.md)のセミコロン区切りリストを指定できます。 これにより、自己完結型の展開を発行できます。 




<!--HONumber=Jan17_HO3-->


