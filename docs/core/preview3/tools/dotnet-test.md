---
title: "dotnet-test コマンド | .NET Core SDK"
description: "`dotnet test` コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。"
keywords: "dotnet-test, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3a0fa917-eb0a-4d7e-9217-d06e65455675
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 66c9f949980612f6e21b6d441c004cc09f4eb7d3

---

#<a name="dotnet-test"></a>dotnet-test

## <a name="name"></a>名前

`dotnet-test` - .NET テスト ドライバー

## <a name="synopsis"></a>構文

`dotnet test [project] [--help] 
    [--settings] [--listTests] [--testCaseFilter] 
    [--testAdapterPath] [--logger] 
    [--configuration] [--output] [--framework] [--diag]
    [--noBuild]`  

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

`--noBuild` 

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



<!--HONumber=Nov16_HO3-->


