---
title: "csproj リファレンス | Microsoft Docs"
description: "既存の csproj ファイルと .NET Core の csproj ファイルの違いについて説明します"
keywords: "リファレンス, csproj, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.translationtype: Human Translation
ms.sourcegitcommit: e47bec77aa3b87f7a46b1c60387cbf8c1193ff17
ms.openlocfilehash: bbbf3616e7836d029116fe0b307b00001ecdd7da
ms.contentlocale: ja-jp
ms.lasthandoff: 06/27/2017

---

<a id="additions-to-the-csproj-format-for-net-core" class="xliff"></a>

# .NET Core の csproj 形式に追加されたもの

ここでは、*project.json* から *csproj* および [MSBuild](https://github.com/Microsoft/MSBuild) への移行に伴ってプロジェクト ファイルに追加された変更について説明します。 一般的なプロジェクト ファイルの構文とリファレンスの詳細については、[MSBuild プロジェクト ファイル](https://docs.microsoft.com/visualstudio/msbuild/msbuild-project-file-schema-reference)のドキュメントを参照してください。  

<a id="implicit-package-references" class="xliff"></a>

## 暗黙的なパッケージ参照
メタパッケージは、プロジェクト ファイルの `<TargetFramework>` または `<TargetFrameworks>` プロパティに指定されている対象フレームワークに基づいて暗黙的に参照されています。 `<TargetFramework>` を指定すると、順序に関係なく `<TargetFrameworks>` は無視されます。

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

<a id="recommendations" class="xliff"></a>

### 推奨事項
`Microsoft.NETCore.App` または `NetStandard.Library` メタパッケージは暗黙的に参照されるので、ベスト プラクティスとして以下が推奨されます。

* プロジェクト ファイルの `<PackageReference>` アイテム経由で `Microsoft.NETCore.App` または `NetStandard.Library` メタパッケージを明示的に参照しないようにします。
* 特定バージョンのランタイムが必要な場合、メタパッケージを参照するのではなく、プロジェクト内で `<RuntimeFrameworkVersion>` プロパティを使用します (`1.0.4` など)。
    * [自己完結型の展開](../deploying/index.md#self-contained-deployments-scd)を使用し、特定のパッチ バージョンの 1.0.0 LTS ランタイムが必要な場合などにこの問題が発生する可能性があります。
* 特定バージョンの `NetStandard.Library` メタパッケージが必要な場合、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンを設定できます。 

<a id="default-compilation-includes-in-net-core-projects" class="xliff"></a>

## .NET Core プロジェクトの既定のコンパイルの include
最新バージョンの SDK の *csproj* 形式に移行すると共に、コンパイル項目と、SDK プロパティ ファイルに埋め込みリソースの既定の include と exclude を SDK プロパティ ファイルに移行しました。 つまり、これらの項目をプロジェクト ファイルに指定する必要はなくなりました。 

これを行う主な理由は、プロジェクト ファイルを見やすくするためです。 SDK の既定値は、最も一般的な使用例に対応しているので、作成するプロジェクトごとに繰り返す必要はありません。 その結果、プロジェクト ファイルが小さくなり、わかりやすく、編集が必要な場合に編集しやすくなります。 

次の表は、SDK に含まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) の一覧です。 

| 要素           | 含まれる glob                              | 除外される glob                                                  | glob の削除                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Compile           | \*\*/\*.cs (または他の言語拡張機能) | \*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc  | N/A                        |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | N/A                        |
| なし              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc     | - \*\*/\*.cs; \*\*/\*.resx |

プロジェクトに glob があり、最新の SDK を使用してビルドしようとすると、次のエラーが発生します。

> 重複するコンパイル項目が含まれていました。 .NET SDK には、既定でプロジェクト ディレクトリのコンパイル項目が含まれています。 これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultCompileItems' プロパティを 'false' に設定することができます。 

このエラーを回避するには、前の表にあるものと一致する明示的な `Compile` 項目を削除するか、次のように `<EnableDefaultCompileItems>` プロパティを `false` に設定します。

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
このプロパティを `false` に設定すると、暗黙的な包含がオーバーライドされ、動作は前の SDK に戻り、プロジェクトに既定の glob を指定する必要が生じます。 

この変更で、他の include の主なしくみは変わりません。 ただし、たとえばアプリで発行する一部のファイルを指定する場合は、*csproj* で既知のしくみ (たとえば `<Content>` 要素) を使用することができます。

<a id="recommendation" class="xliff"></a>

### 推奨事項
csproj では、プロジェクトから既定の glob を削除し、多様なシナリオ (ランタイムや NuGet パッケージなど) でアプリまたはライブラリが必要とする成果物の glob のファイル パスのみを追加することをお勧めします。

<a id="how-to-see-the-whole-project-as-msbuild-sees-it" class="xliff"></a>

## MSBuild と同じようにプロジェクト全体を表示する方法

これらの csproj 変更でプロジェクト ファイルが大幅に簡素化されますが、SDK とそのターゲットが追加されたとき、MSBuild と同様にプロジェクト全体を表示すると便利なことがあります。 [`dotnet msbuild`](dotnet-msbuild.md) コマンドの [`/pp` スイッチ](https://docs.microsoft.com/en-us/visualstudio/msbuild/msbuild-command-line-reference#preprocess)でプロジェクトを事前処理します。インポートされるファイル、そのソース、ビルドに対するその貢献が、実際にプロジェクトをビルドすることなく、表示されます。

`dotnet msbuild /pp:fullproject.xml`

プロジェクトにターゲット フレームワークが複数存在する場合、MSBuild プロパティとして指定し、1 つだけにコマンドの結果を集中させてください。

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

<a id="additions" class="xliff"></a>

## 追加

<a id="sdk-attribute" class="xliff"></a>

### SDK 属性 
*.csproj* ファイルの `<Project>` 要素には、`Sdk` という新しい属性があります。 `Sdk` は、プロジェクトで使用される SDK を指定します。 [レイヤー化のドキュメント](cli-msbuild-architecture.md)で説明されているように、SDK は、.NET Core コードをビルドできる MSBuild [タスク](https://docs.microsoft.com/visualstudio/msbuild/msbuild-tasks)および[ターゲット](https://docs.microsoft.com/visualstudio/msbuild/msbuild-targets)のセットです。 .NET Core ツールには主に 2 つの SDK が付属しています。

1. ID が `Microsoft.NET.Sdk` の .NET Core SDK
2. ID が `Microsoft.NET.Sdk.Web` の .NET Core Web SDK

.NET Core ツールを使用し、コードをビルドするには、`Sdk` 属性を `<Project>` 要素の ID のいずれかに設定する必要があります。 

<a id="packagereference" class="xliff"></a>

### PackageReference
プロジェクトの NuGet の依存関係を指定する項目。 `Include` 属性は、パッケージ ID を指定します。 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

<a id="version" class="xliff"></a>

#### バージョン
`Version` は、復元するパッケージのバージョンを指定します。 要素は、NuGet のバージョン管理スキームの規則に従います。

<a id="includeassets-excludeassets-and-privateassets" class="xliff"></a>

#### IncludeAssets、ExcludeAssets、PrivateAssets
`IncludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使う必要があるものを指定します。 

`ExcludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使ってはならないものを指定します。

`PrivateAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットで、使う必要はあるが、次のプロジェクトに渡してはならないものを指定します。 

> [!NOTE]
> `PrivateAssets` は *project.json*/*xproj* `SuppressParent` 要素と同等です。

これらの属性には、次の項目を 1 つまたは複数含めることができます。

* `Compile` - コンパイルで使用できる lib フォルダーの内容です。
* `Runtime` - 配布する runtime フォルダーの内容です。
* `ContentFiles` - 使用する *contentfiles* フォルダーの内容です。
* `Build` - 使用する build フォルダーのプロパティ/ターゲットです。
* `Native` - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です。
* `Analyzers` - アナライザーが使用されます。

代わりに、次の値を属性に含めることもできます。

* `None` - いずれのアセットも使用されません。
* `All` - すべてのアセットが使用されます。

<a id="dotnetclitoolreference" class="xliff"></a>

### DotNetCliToolReference
`<DotNetCliToolReference>` 項目要素は、プロジェクトのコンテキストでユーザーが復元を望む CLI ツールを指定します。 *project.json* の `tools` ノードに代わるものです。 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<a id="version" class="xliff"></a>

#### バージョン
`Version` は、復元するパッケージのバージョンを指定します。 この属性は、NuGet のバージョン管理スキームの規則に従います。

<a id="runtimeidentifiers" class="xliff"></a>

### RuntimeIdentifiers
`<RuntimeIdentifiers>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。 RID により、自己完結型の展開を発行できます。 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```


<a id="runtimeidentifier" class="xliff"></a>

### RuntimeIdentifier
`<RuntimeIdentifier>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) を 1 つだけ指定できます。 RID により、自己完結型の展開を発行できます。 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```


<a id="packagetargetfallback" class="xliff"></a>

### PackageTargetFallback 
`<PackageTargetFallback>` 要素では、パッケージの復元時に使用する、互換性のある一連のターゲットを指定できます。 dotnet [TxM (Target x Moniker)](https://docs.microsoft.com/nuget/schema/target-frameworks) を使用するパッケージに、dotnet TxM を宣言しないパッケージで動作することを許可するように設計されています。 プロジェクトで dotnet TxM を使用せず、依存するすべてのパッケージに dotnet TxM を与える必要がある場合、非 dotnet プラットフォームを dotnet 対応にするためにプロジェクトに `<PackageTargetFallback>` を追加します。 

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

<a id="nuget-metadata-properties" class="xliff"></a>

## NuGet メタデータ プロパティ
MSbuild への移行に伴い、*project.json* ファイルから *csproj* ファイルに NuGet パッケージをパックするときに使用される入力メタデータを移動しました。 入力は MSBuild プロパティなので、`<PropertyGroup>` グループ内で行う必要があります。 次に示すのは、`dotnet pack` コマンドまたは SDK の一部である `Pack` MSBuild ターゲットを使用するときに、パッキング プロセスへの入力として使用されるプロパティの一覧です。 

<a id="ispackable" class="xliff"></a>

### IsPackable
プロジェクトをパックできるかどうかを示すブール値。 既定値は `true` です。 

<a id="packageversion" class="xliff"></a>

### PackageVersion
結果のパッケージのバージョンを指定します。 すべてのフォームの NuGet バージョン文字列を受け入れます。 既定値は `$(Version)` です。つまり、プロジェクトのプロパティ `Version` の値です。 

<a id="packageid" class="xliff"></a>

### PackageId
結果のパッケージの名前を指定します。 指定しない場合、`pack` 操作の既定では、`AssemblyName` またはディレクトリ名をパッケージ名として使用します。 

<a id="title" class="xliff"></a>

### タイトル
人が読みやすいパッケージのタイトル。通常、nuget.org と、Visual Studio のパッケージ マネージャーの UI 画面で使用されます。 指定しない場合、パッケージ ID が代わりに使用されます。

<a id="authors" class="xliff"></a>

### 作成者
nuget.org のプロファイル名と一致するパッケージ作成者をセミコロンで区切った一覧。 これらは nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。

<a id="description" class="xliff"></a>

### 説明
UI 画面用のパッケージの長い説明。

<a id="copyright" class="xliff"></a>

### Copyright
パッケージの著作権の詳細。

<a id="packagerequirelicenseacceptance" class="xliff"></a>

### PackageRequireLicenseAcceptance
クライアントがユーザーに対して、パッケージのインストール前にパッケージ ライセンスに同意することを必須にするかどうかを示すブール値。 既定値は、`false` です。

<a id="packagelicenseurl" class="xliff"></a>

### PackageLicenseUrl
パッケージに適用されるライセンスの URL。

<a id="packageprojecturl" class="xliff"></a>

### PackageProjectUrl
パッケージのホーム ページの URL。多くの場合、UI 画面と nuget.org に表示されます。

<a id="packageiconurl" class="xliff"></a>

### PackageIconUrl
UI 画面のパッケージのアイコンとして使用する背景が透明な 64x64 の画像の URL。

<a id="packagereleasenotes" class="xliff"></a>

### PackageReleaseNotes
パッケージのリリース ノート。

<a id="packagetags" class="xliff"></a>

### PackageTags
パッケージを指定するタグのセミコロン区切りの一覧。

<a id="packageoutputpath" class="xliff"></a>

### PackageOutputPath
パックされたパッケージをドロップする出力パスを指定します。 既定値は `$(OutputPath)` です。 

<a id="includesymbols" class="xliff"></a>

### IncludeSymbols
このブール値は、プロジェクトをパックするときに、パッケージが追加のシンボル パッケージを作成するかどうかを指定します。 このパッケージの拡張子は *.symbols.nupkg* になります。DLL や他の出力ファイルと共に PDF ファイルがコピーされます。

<a id="includesource" class="xliff"></a>

### IncludeSource
このブール値は、パック プロセスでソース パッケージを作成するかどうかを示します。 ソース パッケージには、ライブラリのソース コードと PDB ファイルが含まれます。 ソース ファイルは、結果のパッケージ ファイルの `src/ProjectName` ディレクトリに置かれます。 

<a id="istool" class="xliff"></a>

### IsTool
すべての出力ファイルを *lib* フォルダーではなく *tools* フォルダーにコピーするかどうかを指定します。 *.csproj* ファイルに `PackageType` を設定することで指定される `DotNetCliTool` とは異なります。

<a id="repositoryurl" class="xliff"></a>

### RepositoryUrl
パッケージのソース コードがある、またはビルド元のリポジトリの URL を指定します。 

<a id="repositorytype" class="xliff"></a>

### RepositoryType
リポジトリの種類を指定します。 既定値は "git" です。 

<a id="nopackageanalysis" class="xliff"></a>

### NoPackageAnalysis
パッケージのビルド後に、パックでパッケージの分析を実行しないことを指定します。

<a id="minclientversion" class="xliff"></a>

### MinClientVersion
nuget.exe および Visual Studio パッケージ マネージャーで強制する、このパッケージをインストールできる NuGet クライアントの最小バージョンを指定します。

<a id="includebuildoutput" class="xliff"></a>

### IncludeBuildOutput
このブール値は、ビルド出力アセンブリを *.nupkg* ファイルにパックするかどうかを指定します。

<a id="includecontentinpack" class="xliff"></a>

### IncludeContentInPack
このブール値は、種類が `Content` の項目を結果のパッケージに自動的に含めるかどうかを指定します。 既定値は、`true` です。 

<a id="buildoutputtargetfolder" class="xliff"></a>

### BuildOutputTargetFolder
出力アセンブリを配置するフォルダーを指定します。 出力アセンブリ (および他の出力ファイル) は、各フレームワーク フォルダーにコピーされます。

<a id="contenttargetfolders" class="xliff"></a>

### ContentTargetFolders
このプロパティには、`PackagePath` が指定されていない場合に、すべてのコンテンツ ファイルを配置する既定の場所を指定します。 既定値は "content;contentFiles" です。

<a id="nuspecfile" class="xliff"></a>

### NuspecFile
パックに使用する *.nuspec* ファイルの相対パスまたは絶対パス。 

> [!NOTE]
> *.nuspec* ファイルを指定すると、情報のパッケージに**のみ**使用され、プロジェクト内の情報は使用されません。 

<a id="nuspecbasepath" class="xliff"></a>

### NuspecBasePath
*.nuspec* ファイルのベース パス。

<a id="nuspecproperties" class="xliff"></a>

### NuspecProperties
キー=値ペアのセミコロン区切りの一覧。

