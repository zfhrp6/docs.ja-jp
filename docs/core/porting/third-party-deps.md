---
title: ".NET Core への移植 - サードパーティの依存関係の分析"
description: ".NET Core への移植 - サードパーティの依存関係の分析"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.workload: dotnetcore
ms.openlocfilehash: 70b39c9762e4ee7450d0f59455bace0ac728844c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="0256e-104">.NET Core への移植 - サードパーティの依存関係の分析</span><span class="sxs-lookup"><span data-stu-id="0256e-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="0256e-105">移植プロセスの最初の手順は、サード パーティの依存関係を理解することです。</span><span class="sxs-lookup"><span data-stu-id="0256e-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="0256e-106">.NET Core でまだ実行されていないもの (がある場合) はどれかを確認し、それらに対して代替計画を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0256e-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0256e-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0256e-107">Prerequisites</span></span>

<span data-ttu-id="0256e-108">この記事は、Windows および Visual Studio を使用しており、最新の .NET Framework で実行されるコードがあることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="0256e-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="0256e-109">NuGet パッケージの分析</span><span class="sxs-lookup"><span data-stu-id="0256e-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="0256e-110">NuGet パッケージの移植性の分析は非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="0256e-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="0256e-111">NuGet パッケージはそれ自体がプラットフォーム固有のアセンブリを含むフォルダーのセットであるため、.NET Core のアセンブリが含まれるフォルダーがあるかどうかを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="0256e-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="0256e-112">[NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用すると、最も簡単に NuGet パッケージ フォルダーを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0256e-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="0256e-113">これを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0256e-113">Here's how to do it.</span></span>

1. <span data-ttu-id="0256e-114">NuGet Package Explorer をダウンロードして開きます。</span><span class="sxs-lookup"><span data-stu-id="0256e-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="0256e-115">「Open package from online feed」 (オンライン フィードからパッケージを開く) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0256e-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="0256e-116">パッケージの名前を検索します。</span><span class="sxs-lookup"><span data-stu-id="0256e-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="0256e-117">右側にある "lib" フォルダーを展開し、フォルダー名を確認します。</span><span class="sxs-lookup"><span data-stu-id="0256e-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="0256e-118">そのパッケージのページの **[Dependencies]** (依存関係) セクションで、[nuget.org](https://www.nuget.org/) でサポートされているパッケージを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="0256e-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="0256e-119">どちらの場合でも、次のいずれかの名前のフォルダーまたはエントリを [nuget.org](https://www.nuget.org/) で探す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0256e-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="0256e-120">これらは [.NET Standard](../../standard/net-standard.md) のバージョンにマップされる Target Framework Moniker (TFM) であり、.NET Core と互換性がある従来のポータブル クラス ライブラリ (PCL) プロファイルです。</span><span class="sxs-lookup"><span data-stu-id="0256e-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="0256e-121">`netcoreapp1.0` には互換性はありますが、アプリケーションを対象としており、ライブラリは対象としていません。</span><span class="sxs-lookup"><span data-stu-id="0256e-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="0256e-122">`netcoreapp1.0` をベースとするライブラリを使用する場合は問題ありませんが、そのライブラリが他の `netcoreapp1.0` アプリケーションで使用される*以外*のことを想定していない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0256e-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="0256e-123">また、プレリリース版の .NET Core で使用されるレガシ TFM にも、互換性のあるものがあります。</span><span class="sxs-lookup"><span data-stu-id="0256e-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="0256e-124">**これらは、あなたのコードで動作する可能性が高いですが、互換性は保証されていません**。</span><span class="sxs-lookup"><span data-stu-id="0256e-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="0256e-125">このような TFM を含むパッケージは、プレリリース版の .NET Core パッケージで構築されています。</span><span class="sxs-lookup"><span data-stu-id="0256e-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="0256e-126">このようなパッケージが `netstandard` ベースに更新されるか、また、更新される場合はいつ行われるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0256e-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="0256e-127">従来の PCL またはプレリリースの .NET Core ターゲットを対象とするパッケージを使用するには、`project.json` ファイルで `imports` ディレクティブを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0256e-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="0256e-128">NuGet パッケージの依存関係が .NET Core で動作しない場合の対処方法</span><span class="sxs-lookup"><span data-stu-id="0256e-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="0256e-129">依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="0256e-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="0256e-130">プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。</span><span class="sxs-lookup"><span data-stu-id="0256e-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="0256e-131">パッケージを検索してパッケージのページの左側にある 「Contact Owners」 (オーナーに連絡する) をクリックすることで、[nuget.org](https://www.nuget.org/) の作成者に直接連絡することができます。</span><span class="sxs-lookup"><span data-stu-id="0256e-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="0256e-132">.NET Core で実行され、使っていたパッケージと同じタスクを実行する別のパッケージを探すことができます。</span><span class="sxs-lookup"><span data-stu-id="0256e-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="0256e-133">パッケージが行っていたコードを自分で記述できます。</span><span class="sxs-lookup"><span data-stu-id="0256e-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="0256e-134">少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="0256e-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="0256e-135">オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、その分野に関心があるために無償で作業を行っているボランティアであり、日中に別の仕事を抱えていることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="0256e-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="0256e-136">連絡を取る場合は、.NET Core サポートについて質問する前に、ライブラリについて肯定的なコメントを述べるとよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="0256e-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="0256e-137">上記のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0256e-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="0256e-138">.NET チームは次の .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="0256e-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="0256e-139">使用したいライブラリについて、dotnet@microsoft.comにメールを送ることもできます。</span><span class="sxs-lookup"><span data-stu-id="0256e-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="0256e-140">NuGet パッケージではない依存関係の分析</span><span class="sxs-lookup"><span data-stu-id="0256e-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="0256e-141">ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0256e-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="0256e-142">その依存関係の移植性を調べる唯一の方法が、[ApiPort ツール](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)を実行することです。</span><span class="sxs-lookup"><span data-stu-id="0256e-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0256e-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="0256e-143">Next steps</span></span>

<span data-ttu-id="0256e-144">ライブラリを移植している場合は、「[Porting your Libraries](libraries.md)」(ライブラリへの移植) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0256e-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
