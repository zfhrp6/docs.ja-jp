---
title: ".NET Core Preview 3 ツールでの依存関係の管理"
description: "Preview 3 では、依存関係の管理方法が変更されています"
keywords: "CLI, 拡張, カスタム コマンド, .NET Core"
author: blackdwarf
manager: wpickett
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 74b87cdb-a244-4c13-908c-539118bfeef9
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e04d5f3b08c7f6885ed9914a91fc308234e6ce3b

---

<a name="managing-dependencies-in-net-core-preview-3-tooling"></a>.NET Core Preview 3 ツールでの依存関係の管理
----------------------------------------------------

# <a name="overview"></a>概要
.NET Core プロジェクトでの project.json から csproj と MSBuild への移行では、プロジェクト ファイルとアセットの統合も行われ、依存関係を追跡できるようになりました。 .NET Core プロジェクトでの依存関係の追跡は、project.json と似ています。 NuGet の依存関係を追跡するための独立した JSON または XML ファイルはありません。 この変更により、`<PackageReference>` と呼ばれる別の*参照*の型も csproj 構文に導入されました。 

ここでは、新しい参照型について説明します。 また、この新しい参照型を使ってプロジェクトにパッケージの依存関係を追加する方法も示します。 

# <a name="the-new-packagereference-element"></a>新しい <PackageReference> 要素
`<PackageReference>` の基本的な構造は次のとおりです。

```xml
<PackageReference Include="<Package_ID>">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

MSBuild に詳しい場合は、既に存在する他の[参照型]()と似ていることが分かります。 重要なのは、`Include` ステートメントではプロジェクトに追加するパッケージ ID を指定することです。 `<Version>` 子要素は取得するバージョンを指定します。 バージョンは、[NuGet のバージョン ルール](https://docs.nuget.org/ndocs/create-packages/dependency-versions#version-ranges)に従って指定します。  

> **注:** `csproj` の構文に詳しくない場合は、[MSBuild プロジェクトのリファレンス ドキュメント]()をご覧ください。  

特定のターゲットでのみ使用可能な依存関係を追加するには、次の条件を使います。

```xml
<PackageReference Include="<Package_ID>" Condition="'$(TargetFramework)' == 'netcoreapp1.0'">
    <Version>PACKAGE_VERSION</Version>
</PackageReference>
```

これは、ビルドがその特定のターゲットに対して行われる場合にのみ依存関係が有効であることを意味します。 条件の `$(TargetFramework)` は、プロジェクトで設定されている MSBuild プロパティです。 最も一般的な .NET Core アプリケーションの場合、これを行う必要はありません。 

# <a name="adding-a-dependency-to-your-project"></a>プロジェクトへの依存関係の追加
簡単に依存関係をプロジェクトに追加できます。 ここでは、`JSON.net` バージョン `9.0.1` をプロジェクトに追加する方法の例を示します。 もちろん、NuGet の他の依存関係にも適用できます。 

プロジェクト ファイルを開くと、2 つ以上の `<ItemGroup>` ノードがあります。 ノードの 1 つには `<PackageReference>` 要素が既にあります。 このノードに新しい依存関係を追加することも、新しいノードを追加することもできます。結果は同じなので開発者次第です。 

この例では、`dotnet new` によって削除される既定のテンプレートを使います。 これは、簡単なコンソール アプリケーションです。 プロジェクトを開き、最初に `<PackageReference>` が既に存在する `<ItemGroup>` を探します。 次に、以下のコードをそれに追加します。

```xml
<PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1</Version>
</PackageReference>
```
その後、プロジェクトを保存し、`dotnet restore` コマンドを実行して依存関係をインストールします。 

完全なプロジェクトは次のようになります。

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
    <PackageReference Include="Newtonsoft.Json">
        <Version>9.0.1</Version>
    </PackageReference>
    <PackageReference Include="Microsoft.NET.Sdk">
      <Version>1.0.0-alpha-20161104-2</Version>
      <PrivateAssets>All</PrivateAssets>
    </PackageReference>
  </ItemGroup>
  
  <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />
</Project>
```

# <a name="removing-a-dependency-from-the-project"></a>プロジェクトからの依存関係の削除
プロジェクト ファイルから依存関係を削除するには、プロジェクト ファイルから `<PackageReference>` を削除するだけです。 





<!--HONumber=Nov16_HO3-->


