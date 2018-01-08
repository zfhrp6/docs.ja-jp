---
title: "プロジェクトを整理し、.NET Framework と .NET Core をサポートする"
description: "プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。"
keywords: ".NET, .NET Core, .NET Framework, プロジェクト レイアウト, 複数のフレームワーク"
author: conniey
ms.author: mairaw
ms.date: 04/06/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3af62252-1dfa-4336-8d2f-5cfdb57d7724
ms.workload: dotnetcore
ms.openlocfilehash: 08fe18233c13410f0fb970020bce090d3345ca84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="organizing-your-project-to-support-net-framework-and-net-core"></a><span data-ttu-id="3d79e-104">プロジェクトを整理し、.NET Framework と .NET Core をサポートする</span><span class="sxs-lookup"><span data-stu-id="3d79e-104">Organizing your project to support .NET Framework and .NET Core</span></span>

<span data-ttu-id="3d79e-105">この記事は、プロジェクト所有者が横並びの .NET Framework と .NET Core に対してソリューションをコンパイルするときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-105">This article helps project owners who want to compile their solution against .NET Framework and .NET Core side-by-side.</span></span> <span data-ttu-id="3d79e-106">プロジェクトを整理するためのオプションを提供し、開発者を支援します。</span><span class="sxs-lookup"><span data-stu-id="3d79e-106">It provides several options to organize projects to help developers achieve this goal.</span></span> <span data-ttu-id="3d79e-107">次の一覧で、.NET Core でプロジェクト レイアウトを設定する方法について決定するときに考慮する典型的なシナリオを紹介します。</span><span class="sxs-lookup"><span data-stu-id="3d79e-107">The following list provides some typical scenarios to consider when you're deciding how to setup your project layout with .NET Core.</span></span> <span data-ttu-id="3d79e-108">この一覧はプロジェクトのニーズに基づいて選択されており、すべてを網羅しるわけではりません。</span><span class="sxs-lookup"><span data-stu-id="3d79e-108">The list may not cover everything you want; prioritize based on your project's needs.</span></span>

* <span data-ttu-id="3d79e-109">[**既存のプロジェクトと .NET Core プロジェクトを結合し、シングル プロジェクトを作成する**][option-csproj]</span><span class="sxs-lookup"><span data-stu-id="3d79e-109">[**Combine existing projects and .NET Core projects into single projects**][option-csproj]</span></span>

  <span data-ttu-id="3d79e-110">*効果:*</span><span class="sxs-lookup"><span data-stu-id="3d79e-110">*What this is good for:*</span></span>
  * <span data-ttu-id="3d79e-111">複数のプロジェクトをコンパイルするのではなく、シングル プロジェクトをコンパイルすることでビルド プロセスをシンプルにします。それぞれ、異なる .NET Framework バージョンまたはプラットフォームをターゲットにします。</span><span class="sxs-lookup"><span data-stu-id="3d79e-111">Simplifying your build process by compiling a single project rather than compiling multiple projects, each targeting a different .NET Framework version or platform.</span></span>
  * <span data-ttu-id="3d79e-112">ターゲットが複数のプロジェクトのソース ファイル管理をシンプルにします。シングル プロジェクト ファイルを管理することになります。</span><span class="sxs-lookup"><span data-stu-id="3d79e-112">Simplifying source file management for multi-targeted projects because you must manage a single project file.</span></span> <span data-ttu-id="3d79e-113">ソース ファイルの追加/削除時、代替方法では、これらを他のプロジェクトと手動で同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d79e-113">When adding/removing source files, the alternatives require you to manually sync these with your other projects.</span></span>
  * <span data-ttu-id="3d79e-114">使用する NuGet パッケージを簡単に生成します。</span><span class="sxs-lookup"><span data-stu-id="3d79e-114">Easily generating a NuGet package for consumption.</span></span>
  * <span data-ttu-id="3d79e-115">コンパイラ ディレクティブを利用することで、ライブラリの特定の .NET Framework バージョンに対してコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-115">Allows you to write code for a specific .NET Framework version in your libraries through the use of compiler directives.</span></span>

  <span data-ttu-id="3d79e-116">*サポートされていないシナリオ:*</span><span class="sxs-lookup"><span data-stu-id="3d79e-116">*Unsupported scenarios:*</span></span>
  * <span data-ttu-id="3d79e-117">既存のプロジェクトを開くには、開発者が Visual Studio 2017 を使用している必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d79e-117">Requires developers to use Visual Studio 2017 to open existing projects.</span></span> <span data-ttu-id="3d79e-118">旧バージョンの Visual Studio をサポートするには、[プロジェクト ファイルを異なるフォルダーで保持する](#support-vs)ことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-118">To support older versions of Visual Studio, [keeping your project files in different folders](#support-vs) is a better option.</span></span>

* <a name="support-vs"></a><span data-ttu-id="3d79e-119">[**既存のプロジェクトと新しい .NET Core プロジェクトを別々に保存する**][option-csproj-folder]</span><span class="sxs-lookup"><span data-stu-id="3d79e-119">[**Keep existing projects and new .NET Core projects separate**][option-csproj-folder]</span></span>

  <span data-ttu-id="3d79e-120">*効果:*</span><span class="sxs-lookup"><span data-stu-id="3d79e-120">*What this is good for:*</span></span>
  * <span data-ttu-id="3d79e-121">既存のプロジェクトで引き続き開発をサポートします。Visual Studio 2017 を所有していない開発者/貢献者はアップグレードする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="3d79e-121">Continuing to support development on existing projects without having to upgrade for developers/contributors who may not have Visual Studio 2017.</span></span>
  * <span data-ttu-id="3d79e-122">既存のプロジェクトで新しいバグが発生する可能性が減ります。既存のプロジェクトではコード チャーンが要求されないためです。</span><span class="sxs-lookup"><span data-stu-id="3d79e-122">Decreasing the possibility of creating new bugs in existing projects because no code churn is required in those projects.</span></span>

## <a name="example"></a><span data-ttu-id="3d79e-123">例</span><span class="sxs-lookup"><span data-stu-id="3d79e-123">Example</span></span>

<span data-ttu-id="3d79e-124">次のリポジトリを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3d79e-124">Consider the repository below:</span></span>

<span data-ttu-id="3d79e-125">![既存のプロジェクト][example-initial-project]</span><span class="sxs-lookup"><span data-stu-id="3d79e-125">![Existing project][example-initial-project]</span></span>

<span data-ttu-id="3d79e-126">[**ソース コード**][example-initial-project-code]</span><span class="sxs-lookup"><span data-stu-id="3d79e-126">[**Source Code**][example-initial-project-code]</span></span>

<span data-ttu-id="3d79e-127">下に説明する既存のプロジェクトの制約や複雑性にもよりますが、このリポジトリのために .NET Core のサポートを追加する方法がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3d79e-127">The following describes several ways to add support for .NET Core for this repository depending on the constraints and complexity of the existing projects.</span></span>

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a><span data-ttu-id="3d79e-128">既存のプロジェクトとターゲットが複数ある .NET Core Project を置換します</span><span class="sxs-lookup"><span data-stu-id="3d79e-128">Replace existing projects with a multi-targeted .NET Core project</span></span>

<span data-ttu-id="3d79e-129">リポジトリを再整理できます。既存の *\*.csproj* ファイルが削除され、複数のフレームワークをターゲットにするシングル *\*.csproj* ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-129">Reorganize the repository so that any existing *\*.csproj* files are removed and a single *\*.csproj* file is created that targets multiple frameworks.</span></span> <span data-ttu-id="3d79e-130">異なるフレームワークに対してシングル プロジェクトでコンパイルできるので、この方法が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-130">This is a great option because a single project is able to compile for different frameworks.</span></span> <span data-ttu-id="3d79e-131">さまざまなコンパイル オプション、ターゲットにするフレームワークごとの依存関係などを処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-131">It also has the power to handle different compilation options and dependencies per targeted framework.</span></span>

<span data-ttu-id="3d79e-132">![複数のフレームワークをターゲットにする csproj の作成][example-csproj]</span><span class="sxs-lookup"><span data-stu-id="3d79e-132">![Create an csproj that targets multiple frameworks][example-csproj]</span></span>

<span data-ttu-id="3d79e-133">[**ソース コード**][example-csproj-code]</span><span class="sxs-lookup"><span data-stu-id="3d79e-133">[**Source Code**][example-csproj-code]</span></span>

<span data-ttu-id="3d79e-134">注目するべき変更点:</span><span class="sxs-lookup"><span data-stu-id="3d79e-134">Changes to note are:</span></span>
* <span data-ttu-id="3d79e-135">*packages.config* と *\*.csproj* が新しい [.NET Core *\*.csproj*][example-csproj-netcore] に置き換わりました。</span><span class="sxs-lookup"><span data-stu-id="3d79e-135">Replacement of *packages.config* and *\*.csproj* with a new [.NET Core *\*.csproj*][example-csproj-netcore].</span></span> <span data-ttu-id="3d79e-136">NuGet パッケージが `<PackageReference> ItemGroup` で指定されています。</span><span class="sxs-lookup"><span data-stu-id="3d79e-136">NuGet packages are specified with `<PackageReference> ItemGroup`.</span></span>

## <a name="keep-existing-projects-and-create-a-net-core-project"></a><span data-ttu-id="3d79e-137">既存のプロジェクトを保持し、.NET Core プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="3d79e-137">Keep existing projects and create a .NET Core project</span></span>

<span data-ttu-id="3d79e-138">古いフレームワークをターゲットにする既存のプロジェクトがあるとき、そのようなプロジェクトをそのまま残し、.NET Core プロジェクトを利用して今後のフレームワークをターゲットにすると効率的な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d79e-138">If there are existing projects that target older frameworks, you may want to leave these projects untouched and use a .NET Core project to target future frameworks.</span></span>

<span data-ttu-id="3d79e-139">![別のフォルダーに既存のプロジェクトがある .NET Core プロジェクト][example-csproj-different-folder]</span><span class="sxs-lookup"><span data-stu-id="3d79e-139">![.NET Core project with existing project in different folder][example-csproj-different-folder]</span></span>

<span data-ttu-id="3d79e-140">[**ソース コード**][example-csproj-different-code]</span><span class="sxs-lookup"><span data-stu-id="3d79e-140">[**Source Code**][example-csproj-different-code]</span></span>

<span data-ttu-id="3d79e-141">注目するべき変更点:</span><span class="sxs-lookup"><span data-stu-id="3d79e-141">Changes to note are:</span></span>
* <span data-ttu-id="3d79e-142">.NET Core と既存のプロジェクトを別々のフォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="3d79e-142">The .NET Core and existing projects are kept in separate folders.</span></span>
    * <span data-ttu-id="3d79e-143">プロジェクトを別々のフォルダーに保存すれば、Visual Studio 2017 を所有する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="3d79e-143">Keeping projects in separate folders avoids forcing you to have Visual Studio 2017.</span></span> <span data-ttu-id="3d79e-144">古いプロジェクトだけを開く別個のソリューションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3d79e-144">You can create a separate solution that only opens the old projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d79e-145">参照</span><span class="sxs-lookup"><span data-stu-id="3d79e-145">See Also</span></span>

<span data-ttu-id="3d79e-146">.NET Core に移行する方法の詳細なガイダンスについては、[.NET Core の移植に関するドキュメント][porting-doc]のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d79e-146">Please see the [.NET Core porting documentation][porting-doc] for more guidance on migrating to .NET Core.</span></span>

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "既存のプロジェクト"
[example-initial-project-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "複数のフレームワークをターゲットにする csproj の作成"
[example-csproj-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "別のフォルダーに既存の PCL がある .NET Core プロジェクト"
[example-csproj-different-code]: https://github.com/dotnet/docs/tree/master/samples/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
