---
title: .NET Core の csproj 形式に追加されたもの
description: 既存の csproj ファイルと .NET Core の csproj ファイルの違いについて説明します
keywords: リファレンス, csproj, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: bdc29497-64f2-4d11-a21b-4097e0bdf5c9
ms.workload:
- dotnetcore
ms.openlocfilehash: fdf91bdb24819c2d92b708e5937980ac2fb0d5fc
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="e60bc-104">.NET Core の csproj 形式に追加されたもの</span><span class="sxs-lookup"><span data-stu-id="e60bc-104">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="e60bc-105">ここでは、*project.json* から *csproj* および [MSBuild](https://github.com/Microsoft/MSBuild) への移行に伴ってプロジェクト ファイルに追加された変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-105">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="e60bc-106">一般的なプロジェクト ファイルの構文とリファレンスの詳細については、[MSBuild プロジェクト ファイル](/visualstudio/msbuild/msbuild-project-file-schema-reference)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e60bc-106">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="e60bc-107">暗黙的なパッケージ参照</span><span class="sxs-lookup"><span data-stu-id="e60bc-107">Implicit package references</span></span>
<span data-ttu-id="e60bc-108">メタパッケージは、プロジェクト ファイルの `<TargetFramework>` または `<TargetFrameworks>` プロパティに指定されている対象フレームワークに基づいて暗黙的に参照されています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-108">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="e60bc-109">`<TargetFramework>` を指定すると、順序に関係なく `<TargetFrameworks>` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-109">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="e60bc-110">推奨事項</span><span class="sxs-lookup"><span data-stu-id="e60bc-110">Recommendations</span></span>
<span data-ttu-id="e60bc-111">`Microsoft.NETCore.App` または `NetStandard.Library` メタパッケージは暗黙的に参照されるので、ベスト プラクティスとして以下が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-111">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="e60bc-112">.NET Core または .NET Standard を対象とするとき、プロジェクト ファイルの `<PackageReference>` アイテム経由で `Microsoft.NETCore.App` または `NetStandard.Library` メタパッケージを明示的に参照しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e60bc-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="e60bc-113">.NET Core を対象にするとき、特定バージョンのランタイムが必要な場合、メタパッケージを参照するのではなく、プロジェクト内で `<RuntimeFrameworkVersion>` プロパティを使用します (`1.0.4` など)。</span><span class="sxs-lookup"><span data-stu-id="e60bc-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="e60bc-114">[自己完結型の展開](../deploying/index.md#self-contained-deployments-scd)を使用し、特定のパッチ バージョンの 1.0.0 LTS ランタイムが必要な場合などにこの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-114">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="e60bc-115">.NET Standard を対象にするとき、特定バージョンの `NetStandard.Library` メタパッケージが必要な場合、`<NetStandardImplicitPackageVersion>` プロパティを使用し、必要なバージョンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-115">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="e60bc-116">.NET Framework プロジェクトでは、`Microsoft.NETCore.App` または `NetStandard.Library` メタパッケージに参照を明示的に追加したり、更新したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="e60bc-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="e60bc-117">.NET Standard ベースの NuGet パッケージを使用するとき、何らかのバージョンの `NetStandard.Library` が必要であれば、NuGet はそのバージョンを自動的にインストールします。</span><span class="sxs-lookup"><span data-stu-id="e60bc-117">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="e60bc-118">.NET Core プロジェクトの既定のコンパイルの include</span><span class="sxs-lookup"><span data-stu-id="e60bc-118">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="e60bc-119">最新バージョンの SDK の *csproj* 形式に移行すると共に、コンパイル項目と、SDK プロパティ ファイルに埋め込みリソースの既定の include と exclude を SDK プロパティ ファイルに移行しました。</span><span class="sxs-lookup"><span data-stu-id="e60bc-119">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="e60bc-120">つまり、これらの項目をプロジェクト ファイルに指定する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e60bc-120">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="e60bc-121">これを行う主な理由は、プロジェクト ファイルを見やすくするためです。</span><span class="sxs-lookup"><span data-stu-id="e60bc-121">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="e60bc-122">SDK の既定値は、最も一般的な使用例に対応しているので、作成するプロジェクトごとに繰り返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e60bc-122">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="e60bc-123">その結果、プロジェクト ファイルが小さくなり、わかりやすく、編集が必要な場合に編集しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-123">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="e60bc-124">次の表は、SDK に含まれる、および除外される要素と [glob](https://en.wikipedia.org/wiki/Glob_(programming)) の一覧です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-124">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="e60bc-125">要素</span><span class="sxs-lookup"><span data-stu-id="e60bc-125">Element</span></span>           | <span data-ttu-id="e60bc-126">含まれる glob</span><span class="sxs-lookup"><span data-stu-id="e60bc-126">Include glob</span></span>                              | <span data-ttu-id="e60bc-127">除外される glob</span><span class="sxs-lookup"><span data-stu-id="e60bc-127">Exclude glob</span></span>                                                  | <span data-ttu-id="e60bc-128">glob の削除</span><span class="sxs-lookup"><span data-stu-id="e60bc-128">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="e60bc-129">Compile</span><span class="sxs-lookup"><span data-stu-id="e60bc-129">Compile</span></span>           | <span data-ttu-id="e60bc-130">\*\*/\*.cs (または他の言語拡張機能)</span><span class="sxs-lookup"><span data-stu-id="e60bc-130">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="e60bc-131">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e60bc-131">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="e60bc-132">N/A</span><span class="sxs-lookup"><span data-stu-id="e60bc-132">N/A</span></span>                        |
| <span data-ttu-id="e60bc-133">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="e60bc-133">EmbeddedResource</span></span>  | <span data-ttu-id="e60bc-134">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e60bc-134">\*\*/\*.resx</span></span>                              | <span data-ttu-id="e60bc-135">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e60bc-135">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e60bc-136">N/A</span><span class="sxs-lookup"><span data-stu-id="e60bc-136">N/A</span></span>                        |
| <span data-ttu-id="e60bc-137">なし</span><span class="sxs-lookup"><span data-stu-id="e60bc-137">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="e60bc-138">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="e60bc-138">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="e60bc-139">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="e60bc-139">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="e60bc-140">プロジェクトに glob があり、最新の SDK を使用してビルドしようとすると、次のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-140">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="e60bc-141">重複するコンパイル項目が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="e60bc-141">Duplicate Compile items were included.</span></span> <span data-ttu-id="e60bc-142">.NET SDK には、既定でプロジェクト ディレクトリのコンパイル項目が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-142">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="e60bc-143">これらの項目をプロジェクト ファイルから削除するか、プロジェクト ファイルに明示的に含める場合は 'EnableDefaultCompileItems' プロパティを 'false' に設定することができます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-143">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="e60bc-144">このエラーを回避するには、前の表にあるものと一致する明示的な `Compile` 項目を削除するか、次のように `<EnableDefaultCompileItems>` プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-144">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="e60bc-145">このプロパティを `false` に設定すると、暗黙的な包含がオーバーライドされ、動作は前の SDK に戻り、プロジェクトに既定の glob を指定する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-145">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="e60bc-146">この変更で、他の include の主なしくみは変わりません。</span><span class="sxs-lookup"><span data-stu-id="e60bc-146">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="e60bc-147">ただし、たとえばアプリで発行する一部のファイルを指定する場合は、*csproj* で既知のしくみ (たとえば `<Content>` 要素) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-147">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="e60bc-148">`<EnableDefaultCompileItems>` は `Compile` glob のみを無効にし、\*.cs 項目にも適用される暗黙的 `None` glob など、他の Glob には影響しません。</span><span class="sxs-lookup"><span data-stu-id="e60bc-148">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="e60bc-149">そのため、**ソリューション エクスプローラー**は \*.cs 項目を `None` 項目として含まれた、プロジェクトの一部として引き続き表示します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-149">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="e60bc-150">同様に、`<EnableDefaultNoneItems>` を利用して暗黙的 `None` glob を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-150">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="e60bc-151">**暗黙的 glob をすべて**無効にするには、`<EnableDefaultItems>` プロパティを `false` に設定します。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e60bc-151">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="e60bc-152">推奨事項</span><span class="sxs-lookup"><span data-stu-id="e60bc-152">Recommendation</span></span>
<span data-ttu-id="e60bc-153">csproj では、プロジェクトから既定の glob を削除し、多様なシナリオ (ランタイムや NuGet パッケージなど) でアプリまたはライブラリが必要とする成果物の glob のファイル パスのみを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e60bc-153">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="e60bc-154">MSBuild と同じようにプロジェクト全体を表示する方法</span><span class="sxs-lookup"><span data-stu-id="e60bc-154">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="e60bc-155">これらの csproj 変更でプロジェクト ファイルが大幅に簡素化されますが、SDK とそのターゲットが追加されたとき、MSBuild と同様にプロジェクト全体を表示すると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-155">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="e60bc-156">[`dotnet msbuild`](dotnet-msbuild.md) コマンドの [`/pp` スイッチ](/visualstudio/msbuild/msbuild-command-line-reference#preprocess)でプロジェクトを事前処理します。インポートされるファイル、そのソース、ビルドに対するその貢献が、実際にプロジェクトをビルドすることなく、表示されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-156">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="e60bc-157">プロジェクトにターゲット フレームワークが複数存在する場合、MSBuild プロパティとして指定し、1 つだけにコマンドの結果を集中させてください。</span><span class="sxs-lookup"><span data-stu-id="e60bc-157">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="e60bc-158">追加</span><span class="sxs-lookup"><span data-stu-id="e60bc-158">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="e60bc-159">SDK 属性</span><span class="sxs-lookup"><span data-stu-id="e60bc-159">Sdk attribute</span></span> 
<span data-ttu-id="e60bc-160">*.csproj* ファイルの `<Project>` 要素には、`Sdk` という新しい属性があります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-160">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="e60bc-161">`Sdk` は、プロジェクトで使用される SDK を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-161">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="e60bc-162">[レイヤー化のドキュメント](cli-msbuild-architecture.md)で説明されているように、SDK は、.NET Core コードをビルドできる MSBuild [タスク](/visualstudio/msbuild/msbuild-tasks)および[ターゲット](/visualstudio/msbuild/msbuild-targets)のセットです。</span><span class="sxs-lookup"><span data-stu-id="e60bc-162">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="e60bc-163">.NET Core ツールには主に 2 つの SDK が付属しています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-163">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="e60bc-164">ID が `Microsoft.NET.Sdk` の .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e60bc-164">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="e60bc-165">ID が `Microsoft.NET.Sdk.Web` の .NET Core Web SDK</span><span class="sxs-lookup"><span data-stu-id="e60bc-165">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="e60bc-166">.NET Core ツールを使用し、コードをビルドするには、`Sdk` 属性を `<Project>` 要素の ID のいずれかに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-166">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="e60bc-167">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e60bc-167">PackageReference</span></span>
<span data-ttu-id="e60bc-168">プロジェクトの NuGet の依存関係を指定する項目。</span><span class="sxs-lookup"><span data-stu-id="e60bc-168">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="e60bc-169">`Include` 属性は、パッケージ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-169">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="e60bc-170">Version</span><span class="sxs-lookup"><span data-stu-id="e60bc-170">Version</span></span>
<span data-ttu-id="e60bc-171">`Version` は、復元するパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-171">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="e60bc-172">この属性は、[NuGet バージョン管理](/nuget/create-packages/dependency-versions#version-ranges)スキームの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="e60bc-172">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="e60bc-173">既定の動作では、バージョンを正確に一致させます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-173">The default behavior is an exact version match.</span></span> <span data-ttu-id="e60bc-174">たとえば、`Version="1.2.3"` を指定すると、パッケージのバージョンが正確に 1.2.3 であることを表す NuGet 表記の `[1.2.3]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-174">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="e60bc-175">IncludeAssets、ExcludeAssets、PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="e60bc-175">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="e60bc-176">`IncludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使う必要があるものを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-176">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="e60bc-177">`ExcludeAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットのうち、使ってはならないものを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-177">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="e60bc-178">`PrivateAssets` 属性は、`<PackageReference>` で指定されているパッケージに属するアセットで、使う必要はあるが、次のプロジェクトに渡してはならないものを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-178">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="e60bc-179">`PrivateAssets` は *project.json*/*xproj* `SuppressParent` 要素と同等です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-179">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="e60bc-180">これらの属性には、次の項目を 1 つまたは複数含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-180">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="e60bc-181">`Compile` - コンパイルで使用できる lib フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-181">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="e60bc-182">`Runtime` - 配布する runtime フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-182">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="e60bc-183">`ContentFiles` - 使用する *contentfiles* フォルダーの内容です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-183">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="e60bc-184">`Build` - 使用する build フォルダーのプロパティ/ターゲットです。</span><span class="sxs-lookup"><span data-stu-id="e60bc-184">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="e60bc-185">`Native` - ランタイムの output フォルダーにコピーするネイティブ アセットの内容です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-185">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="e60bc-186">`Analyzers` - アナライザーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-186">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="e60bc-187">代わりに、次の値を属性に含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-187">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="e60bc-188">`None` - いずれのアセットも使用されません。</span><span class="sxs-lookup"><span data-stu-id="e60bc-188">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="e60bc-189">`All` - すべてのアセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-189">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="e60bc-190">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="e60bc-190">DotNetCliToolReference</span></span>
<span data-ttu-id="e60bc-191">`<DotNetCliToolReference>` 項目要素は、プロジェクトのコンテキストでユーザーが復元を望む CLI ツールを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-191">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="e60bc-192">*project.json* の `tools` ノードに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="e60bc-192">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="e60bc-193">Version</span><span class="sxs-lookup"><span data-stu-id="e60bc-193">Version</span></span>
<span data-ttu-id="e60bc-194">`Version` は、復元するパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-194">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="e60bc-195">この属性は、[NuGet バージョン管理](/nuget/create-packages/dependency-versions#version-ranges)スキームの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="e60bc-195">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="e60bc-196">既定の動作では、バージョンを正確に一致させます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-196">The default behavior is an exact version match.</span></span> <span data-ttu-id="e60bc-197">たとえば、`Version="1.2.3"` を指定すると、パッケージのバージョンが正確に 1.2.3 であることを表す NuGet 表記の `[1.2.3]` と同じになります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-197">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="e60bc-198">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e60bc-198">RuntimeIdentifiers</span></span>
<span data-ttu-id="e60bc-199">`<RuntimeIdentifiers>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-199">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e60bc-200">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-200">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="e60bc-201">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e60bc-201">RuntimeIdentifier</span></span>
<span data-ttu-id="e60bc-202">`<RuntimeIdentifier>` 要素では、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) を 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-202">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e60bc-203">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-203">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="e60bc-204">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e60bc-204">PackageTargetFallback</span></span> 
<span data-ttu-id="e60bc-205">`<PackageTargetFallback>` 要素では、パッケージの復元時に使用する、互換性のある一連のターゲットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-205">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="e60bc-206">dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) を使用するパッケージに、dotnet TxM を宣言しないパッケージで動作することを許可するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-206">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="e60bc-207">プロジェクトで dotnet TxM を使用せず、依存するすべてのパッケージに dotnet TxM を与える必要がある場合、非 dotnet プラットフォームを dotnet 対応にするためにプロジェクトに `<PackageTargetFallback>` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-207">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="e60bc-208">次の例では、プロジェクトのすべてのターゲットにフォールバックを提供しています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-208">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="e60bc-209">次の例では、`netcoreapp1.0` ターゲットにのみフォールバックを指定しています。</span><span class="sxs-lookup"><span data-stu-id="e60bc-209">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="e60bc-210">NuGet メタデータ プロパティ</span><span class="sxs-lookup"><span data-stu-id="e60bc-210">NuGet metadata properties</span></span>
<span data-ttu-id="e60bc-211">MSbuild への移行に伴い、*project.json* ファイルから *csproj* ファイルに NuGet パッケージをパックするときに使用される入力メタデータを移動しました。</span><span class="sxs-lookup"><span data-stu-id="e60bc-211">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="e60bc-212">入力は MSBuild プロパティなので、`<PropertyGroup>` グループ内で行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-212">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="e60bc-213">次に示すのは、`dotnet pack` コマンドまたは SDK の一部である `Pack` MSBuild ターゲットを使用するときに、パッキング プロセスへの入力として使用されるプロパティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-213">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="e60bc-214">IsPackable</span><span class="sxs-lookup"><span data-stu-id="e60bc-214">IsPackable</span></span>
<span data-ttu-id="e60bc-215">プロジェクトをパックできるかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="e60bc-215">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="e60bc-216">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-216">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="e60bc-217">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="e60bc-217">PackageVersion</span></span>
<span data-ttu-id="e60bc-218">結果のパッケージのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-218">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="e60bc-219">すべてのフォームの NuGet バージョン文字列を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-219">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="e60bc-220">既定値は `$(Version)` です。つまり、プロジェクトのプロパティ `Version` の値です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-220">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="e60bc-221">PackageId</span><span class="sxs-lookup"><span data-stu-id="e60bc-221">PackageId</span></span>
<span data-ttu-id="e60bc-222">結果のパッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-222">Specifies the name for the resulting package.</span></span> <span data-ttu-id="e60bc-223">指定しない場合、`pack` 操作の既定では、`AssemblyName` またはディレクトリ名をパッケージ名として使用します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-223">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="e60bc-224">Title</span><span class="sxs-lookup"><span data-stu-id="e60bc-224">Title</span></span>
<span data-ttu-id="e60bc-225">人が読みやすいパッケージのタイトル。通常、nuget.org と、Visual Studio のパッケージ マネージャーの UI 画面で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-225">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="e60bc-226">指定しない場合、パッケージ ID が代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-226">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="e60bc-227">Authors</span><span class="sxs-lookup"><span data-stu-id="e60bc-227">Authors</span></span>
<span data-ttu-id="e60bc-228">nuget.org のプロファイル名と一致するパッケージ作成者をセミコロンで区切った一覧。これらは nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-228">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="e60bc-229">説明</span><span class="sxs-lookup"><span data-stu-id="e60bc-229">Description</span></span>
<span data-ttu-id="e60bc-230">UI 画面用のパッケージの長い説明。</span><span class="sxs-lookup"><span data-stu-id="e60bc-230">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="e60bc-231">Copyright</span><span class="sxs-lookup"><span data-stu-id="e60bc-231">Copyright</span></span>
<span data-ttu-id="e60bc-232">パッケージの著作権の詳細。</span><span class="sxs-lookup"><span data-stu-id="e60bc-232">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="e60bc-233">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="e60bc-233">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="e60bc-234">クライアントがユーザーに対して、パッケージのインストール前にパッケージ ライセンスに同意することを必須にするかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="e60bc-234">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="e60bc-235">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-235">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="e60bc-236">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="e60bc-236">PackageLicenseUrl</span></span>
<span data-ttu-id="e60bc-237">パッケージに適用されるライセンスの URL。</span><span class="sxs-lookup"><span data-stu-id="e60bc-237">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="e60bc-238">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="e60bc-238">PackageProjectUrl</span></span>
<span data-ttu-id="e60bc-239">パッケージのホーム ページの URL。多くの場合、UI 画面と nuget.org に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-239">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="e60bc-240">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="e60bc-240">PackageIconUrl</span></span>
<span data-ttu-id="e60bc-241">UI 画面のパッケージのアイコンとして使用する背景が透明な 64x64 の画像の URL。</span><span class="sxs-lookup"><span data-stu-id="e60bc-241">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="e60bc-242">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="e60bc-242">PackageReleaseNotes</span></span>
<span data-ttu-id="e60bc-243">パッケージのリリース ノート。</span><span class="sxs-lookup"><span data-stu-id="e60bc-243">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="e60bc-244">PackageTags</span><span class="sxs-lookup"><span data-stu-id="e60bc-244">PackageTags</span></span>
<span data-ttu-id="e60bc-245">パッケージを指定するタグのセミコロン区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="e60bc-245">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="e60bc-246">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="e60bc-246">PackageOutputPath</span></span>
<span data-ttu-id="e60bc-247">パックされたパッケージをドロップする出力パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-247">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="e60bc-248">既定値は `$(OutputPath)` です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-248">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="e60bc-249">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="e60bc-249">IncludeSymbols</span></span>
<span data-ttu-id="e60bc-250">このブール値は、プロジェクトをパックするときに、パッケージが追加のシンボル パッケージを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-250">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="e60bc-251">このパッケージの拡張子は *.symbols.nupkg* になります。DLL や他の出力ファイルと共に PDF ファイルがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-251">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="e60bc-252">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="e60bc-252">IncludeSource</span></span>
<span data-ttu-id="e60bc-253">このブール値は、パック プロセスでソース パッケージを作成するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-253">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="e60bc-254">ソース パッケージには、ライブラリのソース コードと PDB ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-254">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="e60bc-255">ソース ファイルは、結果のパッケージ ファイルの `src/ProjectName` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-255">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="e60bc-256">IsTool</span><span class="sxs-lookup"><span data-stu-id="e60bc-256">IsTool</span></span>
<span data-ttu-id="e60bc-257">すべての出力ファイルを *lib* フォルダーではなく *tools* フォルダーにコピーするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-257">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="e60bc-258">*.csproj* ファイルに `PackageType` を設定することで指定される `DotNetCliTool` とは異なります。</span><span class="sxs-lookup"><span data-stu-id="e60bc-258">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="e60bc-259">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="e60bc-259">RepositoryUrl</span></span>
<span data-ttu-id="e60bc-260">パッケージのソース コードがある、またはビルド元のリポジトリの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-260">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="e60bc-261">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="e60bc-261">RepositoryType</span></span>
<span data-ttu-id="e60bc-262">リポジトリの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-262">Specifies the type of the repository.</span></span> <span data-ttu-id="e60bc-263">既定値は "git" です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-263">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="e60bc-264">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="e60bc-264">NoPackageAnalysis</span></span>
<span data-ttu-id="e60bc-265">パッケージのビルド後に、パックでパッケージの分析を実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-265">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="e60bc-266">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="e60bc-266">MinClientVersion</span></span>
<span data-ttu-id="e60bc-267">nuget.exe および Visual Studio パッケージ マネージャーで強制する、このパッケージをインストールできる NuGet クライアントの最小バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-267">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="e60bc-268">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="e60bc-268">IncludeBuildOutput</span></span>
<span data-ttu-id="e60bc-269">このブール値は、ビルド出力アセンブリを *.nupkg* ファイルにパックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-269">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="e60bc-270">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="e60bc-270">IncludeContentInPack</span></span>
<span data-ttu-id="e60bc-271">このブール値は、種類が `Content` の項目を結果のパッケージに自動的に含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-271">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="e60bc-272">既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-272">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="e60bc-273">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="e60bc-273">BuildOutputTargetFolder</span></span>
<span data-ttu-id="e60bc-274">出力アセンブリを配置するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-274">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="e60bc-275">出力アセンブリ (および他の出力ファイル) は、各フレームワーク フォルダーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="e60bc-275">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="e60bc-276">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="e60bc-276">ContentTargetFolders</span></span>
<span data-ttu-id="e60bc-277">このプロパティには、`PackagePath` が指定されていない場合に、すべてのコンテンツ ファイルを配置する既定の場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="e60bc-277">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="e60bc-278">既定値は "content;contentFiles" です。</span><span class="sxs-lookup"><span data-stu-id="e60bc-278">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="e60bc-279">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="e60bc-279">NuspecFile</span></span>
<span data-ttu-id="e60bc-280">パックに使用する *.nuspec* ファイルの相対パスまたは絶対パス。</span><span class="sxs-lookup"><span data-stu-id="e60bc-280">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="e60bc-281">*.nuspec* ファイルを指定すると、情報のパッケージに**のみ**使用され、プロジェクト内の情報は使用されません。</span><span class="sxs-lookup"><span data-stu-id="e60bc-281">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="e60bc-282">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="e60bc-282">NuspecBasePath</span></span>
<span data-ttu-id="e60bc-283">*.nuspec* ファイルのベース パス。</span><span class="sxs-lookup"><span data-stu-id="e60bc-283">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="e60bc-284">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="e60bc-284">NuspecProperties</span></span>
<span data-ttu-id="e60bc-285">キー=値ペアのセミコロン区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="e60bc-285">Semicolon separated list of key=value pairs.</span></span>
