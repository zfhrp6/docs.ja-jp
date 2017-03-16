---
title: ".NET Core CLI の拡張モデル | Microsoft Docs"
description: ".NET Core CLI の拡張モデル"
keywords: "CLI, 拡張, カスタム コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 02/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 827b5567400fd8ed1f32e60ba593a3ae71a0d745
ms.lasthandoff: 03/07/2017

---

# <a name="net-core-cli-extensibility-model"></a>.NET Core CLI の拡張モデル

## <a name="overview"></a>概要
このドキュメントは、CLI ツールを拡張する主な方法と、それぞれのツールを動作させるシナリオについて説明します。 ここでは、ツールの利用方法を概説するだけでなく、両方の種類のツールをビルドする方法の簡単なメモを提供します。 

## <a name="how-to-extend-cli-tools"></a>CLI ツールを拡張する方法
CLI ツールは、主に次の&3; つの方法で拡張できます。

1. プロジェクトごとに NuGet パッケージを使用
2. カスタム ターゲットを持つ NuGet パッケージを使用  
3. システムのパスを使用

上記で説明した&3; つの拡張メカニズムは、排他的ではありません。すべて、または&1; つだけ使用するか、これらを組み合わせることができます。 どちらを選択するかは、拡張機能で実現しようとしている目標によって大きく異なります。

## <a name="per-project-based-extensibility"></a>各プロジェクト ベースの拡張機能
各プロジェクトのツールは、NuGet パッケージとして配布される[フレームワーク依存の展開](../deploying/index.md)です。 ツールは、ツールを参照および復元するプロジェクトのコンテキスト内でのみ使用できます。プロジェクトのコンテキストの外部 (たとえば、プロジェクトが含まれているディレクトリの外) での起動は、コマンドを見つけることができないために失敗します。

プロジェクト ファイルの外部は必要ないため、これらのツールはビルド サーバーに最適です。 ビルド処理では、ビルドを行うプロジェクトの復元が実行され、ツールが利用可能になります。 F# などの言語プロジェクトも、このカテゴリに入ります。結局、各プロジェクトは&1; つの特定の言語でのみ記述できます。 

最後に、この拡張モデルは、プロジェクトのビルド出力へのアクセス権が必要なツールの作成をサポートします。 たとえば、[ASP.NET](https://www.asp.net/) MVC アプリケーションのさまざまな Razor ビュー ツールが、このカテゴリに分類されます。 

### <a name="consuming-per-project-tools"></a>各プロジェクト ツールの利用
これらのツールを利用するには、使用する各ツールの `<DotNetCliToolReference>` 要素をプロジェクト ファイルに追加する必要があります。 `<DotNetCliToolReference>` 要素の内部で、ツールが存在するパッケージを参照し、必要なバージョンを指定します。 `dotnet restore` を実行した後、ツールとその依存関係が復元されます。 

実行するためにプロジェクトのビルド出力を読み込む必要があるツールの場合、通常、別の依存関係がプロジェクト ファイル内の標準の依存関係に一覧されています。 CLI では、ビルド エンジンとして MSBuild を使用するため、ツールのこれらの部分はカスタム MSBuild のターゲットおよびタスクとして記述することを推奨します。これにより、ビルド プロセス全体に参加できるようになるためです。 さらに、出力ファイルの場所、現在ビルドされている構成といった、ビルドによって生成されるすべてのデータを簡単に取得できます。この情報はすべて、どのターゲットからも読み取り可能な一連の MSBuild プロパティになります。 このドキュメントでは、後ほど NuGet を使用してカスタム ターゲットを追加する方法を説明します。 

単純なツールだけのツールを単純なプロジェクトに追加する例を確認してみましょう。 指定された API の NuGet パッケージを使用して検索できる `dotnet-api-search` というコマンドの例を仮定すると、そのツールを使用するコンソール アプリケーションのプロジェクト ファイルは、次のようになります。


```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1/TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` 要素は、`<PackageReference>` 要素と同様の方法で構造化されます。 少なくともツールとそのバージョンを含む、パッケージのパッケージ ID が必要です。 

### <a name="building-tools"></a>ツールのビルド
前述のように、ツールは、単なるポータブル コンソール アプリケーションです。 お客様はコンソール アプリケーションをビルドするように、ツールをビルドします。 ビルドした後、[`dotnet pack`](dotnet-pack.md) コマンドを使用して、コード、その依存関係に関する情報などを含む NuGet パッケージ (nupkg) を作成します。 パッケージ名は、作成者が必要な内容であることがありますが、アプリケーション内 (実際のツール バイナリ) は、`dotnet` がそれを起動できるように、`dotnet-<command>` の規則に準拠している必要があります。 

> [!NOTE]
> .NET Core コマンドライン ツールの RC3 以前のバージョンでは、`dotnet pack` コマンドにバグがあり、`runtime.config.json` をツールでパックできませんでした。 そのファイルがないことで、実行時にエラーが発生します。 この動作が見られる場合、最新のツールに更新し、`dotnet pack` をもう一度お試しください。 

ツールはポータブル アプリケーションであるため、ツールを利用しているユーザーは、ツールを実行するためにツールをビルドするバージョンの .NET Core ライブラリを所有している必要があります。 ツールを使用し、.NET Core ライブラリ内に含まれない任意のその他の依存関係は、NuGet キャッシュに復元および配置されます。 そのため、ツール全体が、.NET Core ライブラリからのアセンブリ、および NuGet キャッシュからのアセンブリを使用して実行されます。 

このようなツールには、それらのツールを使用するプロジェクトの依存関係グラフから完全に切り離された依存関係グラフがあります。 復元処理では、最初にプロジェクトの依存関係を復元し、その後、各ツールとその依存関係を復元します。 

豊富な例やさまざまな組み合わせを [.NET Core CLI リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestProjects) で見つけることができます。 また、同じリポジトリで[使用されたツールの実装](https://github.com/dotnet/cli/tree/rel/1.0.0-preview2/TestAssets/TestPackages)を確認することもできます。 

### <a name="custom-targets"></a>カスタム ターゲット
NuGet には以前からカスタム MSBuild ターゲットおよびプロパティ ファイルをパッケージ化する機能が備わっており、[NuGet ドキュメントのサイト](https://docs.microsoft.com/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package)でこれに関する公式の情報を確認することができます。 CLI が MSBuild を使用するようになり、機能拡張の同じ機構が .NET Core プロジェクトに適用されています。 このような機能拡張は、ビルド プロセスの拡張が必要な場合、生成されたファイルなどのビルド プロセスの成果物にアクセスする必要がある場合、またはビルドが呼び出される構成を検査する場合などに使用します。 

参考のため、サンプルのターゲットのプロジェクト ファイルが以下に含まれています。 何をパッケージ化して、そのパッケージの `build` フォルダーにターゲットとアセンブリを配置するかについて `dotnet pack` コマンドに指示するための新しい `csproj` 構文の使い方を示します。 `Label` プロパティが "dotnet pack instructions" に設定されている `<ItemGroup>` に注目してください。 

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets;$(OutputPath)\*.dll;$(OutputPath)\*.json">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

カスタム ターゲットの利用は、拡張されているプロジェクト内部のパッケージとそのバージョンを指す `<PackageReference>` を提供することで行われます。 ツールとは異なり、カスタム ターゲットのパッケージは利用しているプロジェクトの依存関係クロージャに含まれます。 

カスタム ターゲットの使用はその構成方法のみに依存します。 これは通常の MSBuild ターゲットであるため、指定されたターゲットに依存しており、別のターゲットの後に実行することも、`dotnet msbuild /t:<target-name>` コマンドを使用して手動で呼び出すこともできます。 

ただし、ユーザーに優れたユーザー エクスペリエンスを提供するため、プロジェクトごとのツールとカスタム ターゲットを組み合わせることができます。 このシナリオでは、プロジェクトごとのツールは基本的に必要な任意のパラメーターのみを受け入れ、それをターゲットを実行する必要な `dotnet msbuild` の呼び出しに変換します。 このような相乗効果のサンプルは、[`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) プロジェクトの「[MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016)」 (MVP Summit 2016 ハッカソンのサンプル) レポートで参照することができます。 

### <a name="path-based-extensibility"></a>パス ベースの拡張機能
通常、パス ベースの拡張機能は、概念的に複数のプロジェクトに対応するツールが必要な開発用コンピューターに使用されます。 この拡張機能のメカニズムの主なデメリットは、ツールが存在するマシンに関連付けられていることです。 別のコンピューターで拡張機能が必要な場合は、それを展開する必要があります。

このパターンの CLI ツールセットの拡張は、非常に単純です。 [.NET Core CLI の概要](index.md)に関するページにあるように、`dotnet` ドライバーは、`dotnet-<command>` 規則にふさわしい名前が付けられた任意のコマンドを実行することができます。 この既定の解決ロジックは、最初にいくつかの場所をプローブし、最後にシステム パスに取りかかります。 要求されたコマンドがシステム パスに存在し、起動することができるバイナリである場合、`dotnet` ドライバーでそれを起動します。 

オペレーティング システムが実行できるほぼすべてがバイナリです。 Unix システムでは、`chmod +x` によって実行ビット セットがあるすべてを意味します。 Windows では、Windows が実行方法を理解しているすべてのことです。 

例として、`dotnet clean` コマンドの単純な実装を見てみましょう。 このコマンドを実装するには、`bash` を使用します。 このコマンドは、単純に現在のディレクトリ内の `bin/` と `obj/` ディレクトリを削除します。 `--lock` 引数が渡された場合、これは `project.lock.json` ファイルも削除します。 コマンドの全体は次のとおりです。 

```bash
#!/bin/bash

# Delete the bin and obj dirs
rm -rf bin/ obj/

LOCK_FILE=$1
if [[ "$LOCK_FILE" = "--lock" ]]; then
    rm project.lock.json
fi


echo "Cleaning complete..."
```

macOS では、このスクリプトを `dotnet-clean` として保存し、その実行可能ビットを `chmod +x dotnet-clean` に設定します。 これで、コマンド `ln -s dotnet-clean /usr/local/bin/` を使用して、`/usr/local/bin` でこのスクリプトへのシンボリック リンクを作成できます。 これにより、`dotnet clean` 構文を使用して、クリーン コマンドを起動できるようになります。 アプリを作成し、そのアプリで `dotnet build` を実行して、`dotnet clean` を実行し、これをテストできます。 

## <a name="conclusion"></a>まとめ
.NET Core CLI ツールでは、3 つの主な拡張ポイントを許可します。 各プロジェクトのツールはプロジェクトのコンテキスト内に含まれますが、復元によって簡単にインストールできます。 カスタム ターゲットを使用すると、カスタム タスクを使用してビルド プロセスを簡単に拡張できます。 パス ベースのツールは、一般的に単一のコンピューターで使用できるプロジェクト間のツールに適しています。 


