---
title: "dotnet-test コマンド | Microsoft Docs"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 4bf0aef4-148a-41c6-bb95-0a9e1af8762e
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: fb4627f5f8754ff3432d92e20dff2684a92fbeb5

---

#<a name="dotnet-test-tooling-preview-4"></a>dotnet-test (Tooling Preview 4)

> [!WARNING]
> このトピックは、Visual Studio 2017 RC - .NET Core Tools Preview 4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[dotnet-test](../../tools/dotnet-test.md)」トピックを参照してください。

## <a name="name"></a>名前

`dotnet-test` - .NET テスト ドライバー

## <a name="synopsis"></a>構文

`dotnet test [project] [--help] 
    [--settings] [--listTests] [--testCaseFilter] 
    [--testAdapterPath] [--logger] 
    [--configuration] [--output] [--framework] [--diag]
    [--no-build]`  

## <a name="description"></a>説明

`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。 単体テストは、単体テスト フレームワーク (NUnit や xUnit など) およびその単体テスト フレームワークの dotnet テスト ランナーに対する依存関係があるクラス ライブラリ プロジェクトです。 これらは NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。

テスト プロジェクトでは、テスト ランナーを指定する必要もあります。 これは、通常の `<PackageReference>` 要素を使用して指定されます。次のサンプル プロジェクト ファイルのようになります。

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <Compile Include="**\*.cs" />
    <EmbeddedResource Include="**\*.resx" />
  </ItemGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.NETCore.App">
      <Version>1.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Test.Sdk">
      <Version>15.0.0-preview-20161024-02</Version>
    </PackageReference>
    <PackageReference Include="xunit">
      <Version>2.2.0-beta3-build3402</Version>
    </PackageReference>
    <PackageReference Include="xunit.runner.visualstudio">
      <Version>2.2.0-beta4-build1188</Version>
    </PackageReference>
  </ItemGroup>

  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="options"></a>オプション

`[project]`
    
テスト プロジェクトへのパスを指定します。 省略すると、既定で現在のディレクトリに設定されます。

`-h|--help`

コマンドの短いヘルプを印刷します。

`-s | --settings <SETTINGS_FILE>`

テストの実行時に使用される設定です。 

`-lt | --listTests`

現在のプロジェクトで検出されたすべてのテストを一覧表示します。 

`-tcf | --testCaseFilter <EXPRESSION>`

指定された式を使用して、現在のプロジェクト内のテストを除外します。 

`-tap | --testAdapterPath <TEST_ADAPTER_PATH>`

このテストの実行で指定されたパスからカスタムのテスト アダプターを使用します。 

`--logger <LOGGER>`

テスト結果のロガーを指定します。 

`-c|--configuration <Debug|Release>`

ビルドに使用する構成です。 既定値は `Release` です。 

`-o|--output [OUTPUT_DIRECTORY]`

実行するバイナリを検索するディレクトリです。

`-f|--framework [FRAMEWORK]`

特定のフレームワークのテスト バイナリを検索します。

`-r|--runtime [RUNTIME_IDENTIFIER]`

指定されたランタイムのテスト バイナリを検索します。

`--no-build` 

実行の前にテスト プロジェクトをビルドしません。 

`-d | --diag <DIAGNOSTICS_FILE>`

テスト プラットフォームの診断モードを有効にし、指定したファイルに診断メッセージを出力します。 

## <a name="examples"></a>例

現在のディレクトリのプロジェクトでテストを実行します。

`dotnet test` 

test1 プロジェクトでテストを実行します。

`dotnet test ~/projects/test1/test1.csproj` 

## <a name="see-also"></a>関連項目

[フレームワーク](../../../standard/frameworks.md)

[ランタイム識別子 (RID) のカタログ](../../rid-catalog.md)



<!--HONumber=Jan17_HO3-->


