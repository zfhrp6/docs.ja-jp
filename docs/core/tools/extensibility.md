---
title: ".NET Core CLI の拡張モデル"
description: "コマンド ライン インターフェイス (CLI) ツールを拡張する方法について説明します。"
keywords: "CLI, 拡張, カスタム コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fffc3400-aeb9-4c07-9fea-83bc8dbdcbf3
ms.openlocfilehash: a8f70505d1bb043ab21f87edbb5aa2d9f18a7071
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="d2791-104">.NET Core CLI ツールの拡張モデル</span><span class="sxs-lookup"><span data-stu-id="d2791-104">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="d2791-105">ここでは、.NET Core コマンド ライン インターフェイス (CLI) ツールを拡張する方法と、各方法を利用するシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d2791-105">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="d2791-106">ツールの使用方法だけでなく、さまざまなツールを構築する方法についても紹介します。</span><span class="sxs-lookup"><span data-stu-id="d2791-106">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="d2791-107">CLI ツールを拡張する方法</span><span class="sxs-lookup"><span data-stu-id="d2791-107">How to extend CLI tools</span></span>
<span data-ttu-id="d2791-108">CLI ツールは、主に次の 3 つの方法で拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-108">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="d2791-109">プロジェクトごとに NuGet パッケージを使用</span><span class="sxs-lookup"><span data-stu-id="d2791-109">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

  <span data-ttu-id="d2791-110">各プロジェクトのツールはプロジェクトのコンテキスト内に含まれますが、復元によって簡単にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d2791-110">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="d2791-111">カスタム ターゲットを持つ NuGet パッケージを使用</span><span class="sxs-lookup"><span data-stu-id="d2791-111">Via NuGet packages with custom targets</span></span>](#custom-targets)

  <span data-ttu-id="d2791-112">カスタム ターゲットを使用すると、カスタム タスクを使用してビルド プロセスを簡単に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-112">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="d2791-113">システムのパスを使用</span><span class="sxs-lookup"><span data-stu-id="d2791-113">Via the system's PATH</span></span>](#path-based-extensibility)

  <span data-ttu-id="d2791-114">パス ベースのツールは、一般的に単一のコンピューターで使用できるプロジェクト間のツールに適しています。</span><span class="sxs-lookup"><span data-stu-id="d2791-114">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="d2791-115">上記で概説されている 3 つの拡張メカニズムは排他的ではありません。</span><span class="sxs-lookup"><span data-stu-id="d2791-115">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="d2791-116">メカニズムの 1 つ、すべて、または組み合わせて使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d2791-116">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="d2791-117">選択するメカニズムは、拡張機能で実現しようとしている目標によって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="d2791-117">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="d2791-118">各プロジェクト ベースの拡張機能</span><span class="sxs-lookup"><span data-stu-id="d2791-118">Per-project based extensibility</span></span>
<span data-ttu-id="d2791-119">各プロジェクトのツールは、NuGet パッケージとして配布される[フレームワーク依存の展開](../deploying/index.md#framework-dependent-deployments-fdd)です。</span><span class="sxs-lookup"><span data-stu-id="d2791-119">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="d2791-120">ツールを参照するプロジェクトのコンテキスト内と、復元する対象にのみ、ツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-120">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="d2791-121">プロジェクトのコンテキスト以外で呼び出すと (たとえば、プロジェクトを含むディレクトリ以外)、コマンドが見つからないので失敗します。</span><span class="sxs-lookup"><span data-stu-id="d2791-121">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="d2791-122">プロジェクト ファイルの外部は必要ないため、これらのツールはビルド サーバーに最適です。</span><span class="sxs-lookup"><span data-stu-id="d2791-122">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="d2791-123">ビルド処理では、ビルドを行うプロジェクトの復元が実行され、ツールが利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="d2791-123">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="d2791-124">各プロジェクトは 1 つの特定の言語でのみ記述できるので、F# などの言語プロジェクトも、このカテゴリに入ります。</span><span class="sxs-lookup"><span data-stu-id="d2791-124">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="d2791-125">最後に、この拡張モデルは、プロジェクトのビルド出力へのアクセス権が必要なツールの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="d2791-125">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="d2791-126">たとえば、[ASP.NET](https://www.asp.net/) MVC アプリケーションのさまざまな Razor ビュー ツールが、このカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-126">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="d2791-127">各プロジェクト ツールの利用</span><span class="sxs-lookup"><span data-stu-id="d2791-127">Consuming per-project tools</span></span>
<span data-ttu-id="d2791-128">これらのツールを利用するには、使用する各ツールの `<DotNetCliToolReference>` 要素をプロジェクト ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-128">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="d2791-129">`<DotNetCliToolReference>` 要素の内部で、ツールが存在するパッケージを参照し、必要なバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d2791-129">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="d2791-130">[`dotnet restore`](dotnet-restore.md) を実行した後、ツールとその依存関係が復元されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-130">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d2791-131">実行するためにプロジェクトのビルド出力を読み込む必要があるツールの場合、通常、別の依存関係がプロジェクト ファイル内の標準の依存関係に一覧されています。</span><span class="sxs-lookup"><span data-stu-id="d2791-131">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="d2791-132">CLI では、ビルド エンジンとして MSBuild を使用するため、ツールのこれらの部分はカスタム MSBuild の[ターゲット](/visualstudio/msbuild/msbuild-targets)および[タスク](/visualstudio/msbuild/msbuild-tasks)として記述することを推奨します。これは、ビルド プロセス全体に参加できるようになるためです。</span><span class="sxs-lookup"><span data-stu-id="d2791-132">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="d2791-133">さらに、出力ファイルの場所、現在ビルドされている構成といった、ビルドによって生成されるすべてのデータを簡単に取得できます。この情報はすべて、どのターゲットからも読み取り可能な一連の MSBuild プロパティになります。</span><span class="sxs-lookup"><span data-stu-id="d2791-133">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="d2791-134">このドキュメントでは、後ほど NuGet を使用してカスタム ターゲットを追加する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d2791-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="d2791-135">単純なツールだけのツールを単純なプロジェクトに追加する例を確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="d2791-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="d2791-136">指定された API の NuGet パッケージを使用して検索できる `dotnet-api-search` というコマンドの例を仮定すると、そのツールを使用するコンソール アプリケーションのプロジェクト ファイルは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d2791-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="d2791-137">`<DotNetCliToolReference>` 要素は、`<PackageReference>` 要素と同様の方法で構造化されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="d2791-138">ツールとそのバージョンを復元して格納できるパッケージのパッケージ ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="d2791-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="d2791-139">ツールのビルド</span><span class="sxs-lookup"><span data-stu-id="d2791-139">Building tools</span></span>
<span data-ttu-id="d2791-140">前述のように、ツールは、単なるポータブル コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="d2791-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="d2791-141">ツールのビルドは、他のコンソール アプリケーションをビルドする方法と同じです。</span><span class="sxs-lookup"><span data-stu-id="d2791-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="d2791-142">ビルドした後、[`dotnet pack`](dotnet-pack.md) コマンドを使用して、コード、その依存関係に関する情報などを含む NuGet パッケージ (.nupkg ファイル) を作成します。</span><span class="sxs-lookup"><span data-stu-id="d2791-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="d2791-143">パッケージには任意の名前を付けることができますが、アプリケーション内 (実際のツール バイナリ) は、`dotnet` から呼び出すことができるように、`dotnet-<command>` の規則に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="d2791-144">.NET Core コマンドライン ツールの RC3 以前のバージョンでは、`dotnet pack` コマンドにバグがあり、`runtime.config.json` をツールでパックできませんでした。</span><span class="sxs-lookup"><span data-stu-id="d2791-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="d2791-145">そのファイルがないことで、実行時にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d2791-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="d2791-146">この動作が見られる場合、最新のツールに更新し、`dotnet pack` をもう一度お試しください。</span><span class="sxs-lookup"><span data-stu-id="d2791-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="d2791-147">ツールはポータブル アプリケーションであるため、ツールを利用しているユーザーは、ツールを実行するためにツールをビルドするバージョンの .NET Core ライブラリを所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="d2791-148">ツールを使用し、.NET Core ライブラリ内に含まれない任意のその他の依存関係は、NuGet キャッシュに復元および配置されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="d2791-149">そのため、ツール全体が、.NET Core ライブラリからのアセンブリ、および NuGet キャッシュからのアセンブリを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="d2791-150">このようなツールには、それらのツールを使用するプロジェクトの依存関係グラフから完全に切り離された依存関係グラフがあります。</span><span class="sxs-lookup"><span data-stu-id="d2791-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="d2791-151">復元処理では、最初にプロジェクトの依存関係を復元し、その後、各ツールとその依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="d2791-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="d2791-152">豊富な例やさまざまな組み合わせを [.NET Core CLI リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects) で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d2791-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="d2791-153">また、同じリポジトリで[使用されたツールの実装](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages)を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d2791-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/rel/1.0.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="d2791-154">カスタム ターゲット</span><span class="sxs-lookup"><span data-stu-id="d2791-154">Custom targets</span></span>
<span data-ttu-id="d2791-155">NuGet には、[カスタム MSBuild ターゲット ファイルとプロパティ ファイルをパッケージ化](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package)する機能があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="d2791-156">.NET Core CLI ツールが MSBuild を使用するようになり、同じ拡張機能のメカニズムが .NET Core プロジェクトに適用されています。</span><span class="sxs-lookup"><span data-stu-id="d2791-156">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="d2791-157">このような拡張機能は、ビルド プロセスの拡張が必要な場合、生成されたファイルなどのビルド プロセスの成果物にアクセスする必要がある場合、またはビルドが呼び出される構成を検査する場合などに使用します。</span><span class="sxs-lookup"><span data-stu-id="d2791-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="d2791-158">次の例では、ターゲットのプロジェクト ファイルで `csproj` 構文を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d2791-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="d2791-159">これは、[`dotnet pack`](dotnet-pack.md) コマンドにパッケージ対象を指示し、ターゲット ファイルだけでなくアセンブリをパッケージ内の *build* フォルダーに格納する例です。</span><span class="sxs-lookup"><span data-stu-id="d2791-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="d2791-160">`Label` プロパティが `dotnet pack instructions` に設定された `<ItemGroup>` 要素があり、その下に Target が定義されています。</span><span class="sxs-lookup"><span data-stu-id="d2791-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
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

<span data-ttu-id="d2791-161">カスタム ターゲットの利用は、拡張されているプロジェクト内部のパッケージとそのバージョンを指す `<PackageReference>` を提供することで行われます。</span><span class="sxs-lookup"><span data-stu-id="d2791-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="d2791-162">ツールとは異なり、カスタム ターゲットのパッケージは利用しているプロジェクトの依存関係クロージャに含まれます。</span><span class="sxs-lookup"><span data-stu-id="d2791-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="d2791-163">カスタム ターゲットの使用はその構成方法のみに依存します。</span><span class="sxs-lookup"><span data-stu-id="d2791-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="d2791-164">これは MSBuild ターゲットなので、指定されたターゲットに依存しており、別のターゲットの後に実行することも、`dotnet msbuild /t:<target-name>` コマンドを使用して手動で呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d2791-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="d2791-165">ただし、ユーザーに優れたユーザー エクスペリエンスを提供するため、プロジェクトごとのツールとカスタム ターゲットを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="d2791-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="d2791-166">このシナリオでは、プロジェクトごとのツールは基本的に必要な任意のパラメーターのみを受け入れ、それをターゲットを実行する必要な [`dotnet msbuild`](dotnet-msbuild.md) の呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="d2791-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="d2791-167">このような相乗効果のサンプルは、[`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) プロジェクトの「[MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016)」 (MVP Summit 2016 ハッカソンのサンプル) レポートで参照することができます。</span><span class="sxs-lookup"><span data-stu-id="d2791-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="d2791-168">パス ベースの拡張機能</span><span class="sxs-lookup"><span data-stu-id="d2791-168">PATH-based extensibility</span></span>
<span data-ttu-id="d2791-169">通常、パス ベースの拡張機能は、概念的に複数のプロジェクトに対応するツールが必要な開発用コンピューターに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d2791-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="d2791-170">この拡張機能のメカニズムの主なデメリットは、ツールが存在するマシンに関連付けられていることです。</span><span class="sxs-lookup"><span data-stu-id="d2791-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="d2791-171">別のコンピューターで拡張機能が必要な場合は、それを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="d2791-172">このパターンの CLI ツールセットの拡張は、非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="d2791-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="d2791-173">[.NET Core CLI の概要](index.md)に関するページにあるように、`dotnet` ドライバーは、`dotnet-<command>` 規則にふさわしい名前が付けられた任意のコマンドを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="d2791-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="d2791-174">この既定の解決ロジックは、最初にいくつかの場所をプローブし、最後にシステム パスに取りかかります。</span><span class="sxs-lookup"><span data-stu-id="d2791-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="d2791-175">要求されたコマンドがシステム パスに存在し、起動することができるバイナリである場合、`dotnet` ドライバーでそれを起動します。</span><span class="sxs-lookup"><span data-stu-id="d2791-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="d2791-176">ファイルは実行可能ファイルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2791-176">The file must be executable.</span></span> <span data-ttu-id="d2791-177">Unix システムでは、`chmod +x` によって実行ビット セットがあるすべてを意味します。</span><span class="sxs-lookup"><span data-stu-id="d2791-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="d2791-178">Windows では、*cmd* ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="d2791-179">とても簡単な "Hello World" ツールの実装を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="d2791-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="d2791-180">Windows では `bash` と `cmd` の両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="d2791-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="d2791-181">次のコマンドでは、単純に "Hello World" をコンソールにエコーします。</span><span class="sxs-lookup"><span data-stu-id="d2791-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="d2791-182">macOS では、このスクリプトを `dotnet-hello` として保存し、その実行可能ビットを `chmod +x dotnet-hello` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d2791-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="d2791-183">これで、コマンド `ln -s <full_path>/dotnet-hello /usr/local/bin/` を使用して、`/usr/local/bin` でこのスクリプトへのシンボリック リンクを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="d2791-184">これにより、`dotnet hello` 構文を使用して、コマンドを起動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="d2791-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="d2791-185">Windows では、このスクリプトを `dotnet-hello.cmd` として保存し、システム パス内の場所に格納できます (または、既にパス内にあるフォルダーに追加できます)。</span><span class="sxs-lookup"><span data-stu-id="d2791-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="d2791-186">その後、`dotnet hello` を使用するだけでこの例を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d2791-186">After this, you can just use `dotnet hello` to run this example.</span></span>
