---
title: "csproj リファレンス | Microsoft Docs"
description: "既存の csproj ファイルと .NET Core の csproj ファイルの違いについて説明します"
keywords: "リファレンス, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 07/02/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
translationtype: Human Translation
ms.sourcegitcommit: 0402707f98af8b716b041ba1260162cd227918cc
ms.openlocfilehash: 98f6ced2a199bdbe2f91f46e48ffd3ac52438cf8

---

# <a name="additions-to-the-csproj-format-for-net-core"></a>.NET Core の csproj 形式に追加されたもの

[!INCLUDE[preview-warning](../../../includes/warning.md)]

ここでは、`project.json` から csproj `csproj` および [MSBuild](https://github.com/Microsoft/MSBuild) への移行に伴って csproj ファイルに追加された変更の概要を示します。 一般的なプロジェクト ファイルの構文とリファレンスの詳細については、[MSBuild プロジェクト ファイル](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference)のドキュメントを参照してください。  

## <a name="additions"></a>追加

* プロジェクトの NuGet 依存関係を指定する PackageReference 項目。 `Include` 属性は、パッケージ ID を指定します。 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

## <a name="version"></a>バージョン
`Version` は、復元するパッケージのバージョンを指定します。 要素は、NuGet のバージョン管理スキームの規則に従います。

## <a name="includeassets"></a>IncludeAssets
`IncludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使う必要があるものを指定します。 

この属性には、次の値を&1; つまたは複数含めることができます。

* `Compile` - コンパイルで使用できる lib フォルダーの内容です。
* `Runtime` - 配布する runtime フォルダーの内容です。
* `ContentFiles` - 使用する contentfiles フォルダーの内容です。
* `Build` - 使用する build フォルダーのプロパティ/ターゲットです。
* `Native` - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です。
* `Analyzers` - アナライザーが使用されます。

代わりに、次の値を属性に含めることもできます。

* `None` - いずれのアセットも使用されません。
* `All` - すべてのアセットが使用されます。

## <a name="excludeassets"></a>ExcludeAssets
`ExcludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使ってはならないものを指定します。

この属性には、次の値を&1; つまたは複数含めることができます。

* `Compile` - コンパイルで使用できる lib フォルダーの内容です。
* `Runtime` - 配布する runtime フォルダーの内容です。
* `ContentFiles` - 使用する contentfiles フォルダーの内容です。
* `Build` - 使用する build フォルダーのプロパティ/ターゲットです。
* `Native` - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です。
* `Analyzers` - アナライザーが使用されます。

代わりに、次の値を要素に含めることもできます。

* `None` - いずれのアセットも使用されません。
* `All` - すべてのアセットが使用されます。

## <a name="privateassets"></a>PrivateAssets
`PrivateAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットで、使う必要はあるが、次のプロジェクトに渡してはならないものを指定します。 

> [!NOTE]
> これは、project.json/xproj の `SuppressParent` 要素に対する新しい用語です。 

この属性には、次の値を&1; つまたは複数含めることができます。

* `Compile` - コンパイルで使用できる lib フォルダーの内容です。
* `Runtime` - 配布する runtime フォルダーの内容です。
* `ContentFiles` - 使用する contentfiles フォルダーの内容です。
* `Build` - 使用する build フォルダーのプロパティ/ターゲットです。
* `Native` - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です。
* `Analyzers` - アナライザーが使用されます。

代わりに、次の値を属性に含めることもできます。

* `None` - いずれのアセットも使用されません。
* `All` - すべてのアセットが使用されます。

* DotnetCliToolReference `<DotnetCliToolReference>` item 要素は、プロジェクトのコンテキストでユーザーが復元を望む CLI ツールを指定します。 `project.json` の `tools` ノードに代わるものです。 

```xml
<DotnetCliToolReference Include="<package-id>" Version="" />
```

## <a name="version"></a>バージョン
`Version` は、復元するパッケージのバージョンを指定します。 この属性は、NuGet のバージョン管理スキームの規則に従います。

* RuntimeIdentifiers `<RuntimeIdentifiers>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../../rid-catalog.md) のセミコロン区切りリストを指定できます。 RID により、自己完結型の展開を発行できます。 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


* RuntimeIdentifier `<RuntieIdentifier>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../../rid-catalog.md) を&1; つだけ指定できます。 RID により、自己完結型の展開を発行できます。 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


* PackageTargetFallback `<PackageTargetFallback>` 要素では、パッケージの復元時に使用する、互換性のある一連のターゲットを指定できます。 dotnet TxM を使用するパッケージに、dotnet TxM を宣言しないパッケージで動作することを許可するように設計されています。 プロジェクトで dotnet TxM を使用せず、依存するすべてのパッケージに dotnet TxM を与える必要がある場合、非 dotnet プラットフォームを dotnet 対応にするためにプロジェクトに `<PackageTargetFallback>` を追加します。 

次の例では、プロジェクトのすべてのターゲットにフォールバックを提供しています。 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

次の例では、`netcoreapp1.0` ターゲットにのみフォールバックを指定しています。

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a>NuGet メタデータ プロパティ
MSbuild への移行に伴い、project.json ファイルから csproj ファイルに NuGet パッケージをパックするときに使用される入力メタデータを移動しました。 入力は MSBuild プロパティです。 次に示すのは、`dotnet pack` コマンドまたは SDK の一部である `Pack` MSBuild ターゲットを使用するときに、パッキング プロセスへの入力として使用されるプロパティの一覧です。 

* IsPackable
* PackageVersion
* PackageId
* タイトル
* 作成者
* 説明
* Copyright
* PackageRequireLicenseAcceptance
* PackageLicenseUrl
* PackageProjectUrl
* PackageIconUrl
* PackageReleaseNotes
* PackageTags
* PackageOutputPath
* IncludeSymbols
* IncludeSource
* PackageTypes
* IsTool
* RepositoryUrl
* RepositoryType
* NoPackageAnalysis
* MinClientVersion
* IncludeBuildOutput
* IncludeContentInPack
* BuildOutputTargetFolder
* ContentTargetFolders
* NuspecFile
* NuspecBasePath
* NuspecProperties


<!--HONumber=Feb17_HO2-->


