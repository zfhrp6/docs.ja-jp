---
title: .NET Framework のアプリケーションの互換性
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b75429d0de69c60e7c24551bf1d9218e74d0c5ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="application-compatibility-in-the-net-framework"></a><span data-ttu-id="7c153-102">.NET Framework のアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="7c153-102">Application Compatibility in the .NET Framework</span></span>

## <a name="introduction"></a><span data-ttu-id="7c153-103">はじめに</span><span class="sxs-lookup"><span data-stu-id="7c153-103">Introduction</span></span>
<span data-ttu-id="7c153-104">.NET の各リリースにおいて互換性は非常に重要な目標です。</span><span class="sxs-lookup"><span data-stu-id="7c153-104">Compatibility is a very important goal of each .NET release.</span></span> <span data-ttu-id="7c153-105">各バージョンが付加的な場合は互換性が確保され、以前のバージョンも引き続き動作します。</span><span class="sxs-lookup"><span data-stu-id="7c153-105">Compatibility ensures that each version is additive, so previous versions will still work.</span></span> <span data-ttu-id="7c153-106">一方、以前の機能に変更が生じた場合 (パフォーマンスの向上、セキュリティに関する問題への対処、またはバグの修正を目的として)、既存のコードまたは既存のアプリケーションを以降のバージョンで実行すると互換性に問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c153-106">On the other hand, changes to previous functionality (to improve performance, address security issues, or fix bugs) can cause compatibility problems in existing code or existing applications that run under a later version.</span></span> <span data-ttu-id="7c153-107">.NET Framework では、変更の再ターゲットとランタイムの変更点を認識します。</span><span class="sxs-lookup"><span data-stu-id="7c153-107">The .NET Framework recognizes retargeting changes and runtime changes.</span></span> <span data-ttu-id="7c153-108">変更の再ターゲットは、.NET Framework の特定のバージョンをターゲットとしているもののそれ以降のバージョンで実行されるアプリケーションに影響します。</span><span class="sxs-lookup"><span data-stu-id="7c153-108">Retargeting changes affect applications that target a specific version of the .NET Framework but are running on a later version.</span></span> <span data-ttu-id="7c153-109">ランタイムの変更点は、特定のバージョンで実行されるすべてのアプリケーションに影響します。</span><span class="sxs-lookup"><span data-stu-id="7c153-109">Runtime changes affect all applications running on a particular version.</span></span>

<span data-ttu-id="7c153-110">各アプリは .NET Framework の特定のバージョンをターゲットとします。バージョンは次の方法で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="7c153-110">Each app targets a specific version of the .NET Framework, which can be specified by:</span></span>

* <span data-ttu-id="7c153-111">Visual Studio でターゲット フレームワークを定義する。</span><span class="sxs-lookup"><span data-stu-id="7c153-111">Defining a target framework in Visual Studio.</span></span>
* <span data-ttu-id="7c153-112">プロジェクト ファイルでターゲット フレームワークを指定する。</span><span class="sxs-lookup"><span data-stu-id="7c153-112">Specifying the target framework in a project file.</span></span>
* <span data-ttu-id="7c153-113"><xref:System.Runtime.Versioning.TargetFrameworkAttribute> をソース コードに適用する。</span><span class="sxs-lookup"><span data-stu-id="7c153-113">Applying a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> to the source code.</span></span>

<span data-ttu-id="7c153-114">ターゲットに指定されたバージョンより新しいバージョンでアプリが実行されると、.NET Framework は後方互換動作によって、ターゲットに指定されている古いバージョンを模倣します。</span><span class="sxs-lookup"><span data-stu-id="7c153-114">When running on a newer version than what was targeted, the .NET Framework will use quirked behavior to mimic the older targeted version.</span></span> <span data-ttu-id="7c153-115">つまり、アプリは、Framework の新しいバージョンで実行されていても、古いバージョンで実行されているように機能します。</span><span class="sxs-lookup"><span data-stu-id="7c153-115">In other words, the app will run on the newer version of the Framework, but act as if it's running on the older version.</span></span> <span data-ttu-id="7c153-116">.NET Framework のバージョン間の互換性の問題の多くは、この後方互換モデルを通して対応されます。</span><span class="sxs-lookup"><span data-stu-id="7c153-116">Many of the compatibility issues between versions of the .NET Framework are mitigated through this quirking model.</span></span>

## <a name="runtime-changes"></a><span data-ttu-id="7c153-117">ランタイムの変更</span><span class="sxs-lookup"><span data-stu-id="7c153-117">Runtime changes</span></span>

<span data-ttu-id="7c153-118">ランタイムの問題とは、コンピューターに新しいランタイムを配置し前と同じバイナリを実行したが動作が異なっている場合に発生する問題です。</span><span class="sxs-lookup"><span data-stu-id="7c153-118">Runtime issues are those that arise when a new runtime is placed on a machine and the same binaries are run, but different behavior is seen.</span></span> <span data-ttu-id="7c153-119">バイナリが .NET Framework 4.0 向けにコンパイルされている場合、そのバイナリは .NET Framework 4.5 以降のバージョンでは .NET Framework 4.0 互換モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="7c153-119">If a binary was compiled for .NET Framework 4.0 it will run in .NET Framework 4.0 compatibility mode on 4.5 or later versions.</span></span> <span data-ttu-id="7c153-120">4.5 に影響する変更の多くは、4.0 向けにコンパイルされたバイナリには影響しません。</span><span class="sxs-lookup"><span data-stu-id="7c153-120">Many of the changes that affect 4.5 will not affect a binary compiled for 4.0.</span></span> <span data-ttu-id="7c153-121">これは、AppDomain に固有のものであり、入力アセンブリの設定内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="7c153-121">This is specific to the AppDomain and depends on the settings of the entry assembly.</span></span>

## <a name="retargeting-changes"></a><span data-ttu-id="7c153-122">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="7c153-122">Retargeting changes</span></span>

<span data-ttu-id="7c153-123">再ターゲットの問題とは、4.0 をターゲットにしていたアセンブリが今度は 4.5 をターゲットにするように設定されたときに発生するものです。</span><span class="sxs-lookup"><span data-stu-id="7c153-123">Retargeting issues are those that arise when an assembly that was targeting 4.0 is now set to target 4.5.</span></span> <span data-ttu-id="7c153-124">この場合、アセンブリは新しい機能を選択するようになるので、古い機能との互換性の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c153-124">Now the assembly opts into the new features as well as potential compatibility issues to old features.</span></span> <span data-ttu-id="7c153-125">繰り返しますが、これは入力アセンブリによって異なります。したがって、アセンブリを使用するコンソール アプリ、またはアセンブリを参照する Web サイトが該当します。</span><span class="sxs-lookup"><span data-stu-id="7c153-125">Again, this is dictated by the entry assembly, so the console app that uses the assembly, or the website that references the assembly.</span></span>

## <a name="net-compatibility-diagnostics"></a><span data-ttu-id="7c153-126">.NET 互換性診断</span><span class="sxs-lookup"><span data-stu-id="7c153-126">.NET Compatibility Diagnostics</span></span>

<span data-ttu-id="7c153-127">.NET 互換性診断は、.NET Framework のバージョン間のアプリケーション互換性問題の識別に役立つ Roslyn を使用したアナライザーです。</span><span class="sxs-lookup"><span data-stu-id="7c153-127">The .NET Compatibility Diagnostics are Roslyn-powered analyzers that help identify application compatibility issues between versions of the .NET Framework.</span></span> <span data-ttu-id="7c153-128">この一覧には、使用可能なすべてのアナライザーが含まれますが、特定の移行に適用されるのは、その一部分のみです。</span><span class="sxs-lookup"><span data-stu-id="7c153-128">This list contains all of the analyzers available, although only a subset will apply to any specific migration.</span></span> <span data-ttu-id="7c153-129">アナライザーは、計画的な移行に該当する問題と表面上の問題にすぎないものを判断します。</span><span class="sxs-lookup"><span data-stu-id="7c153-129">The analyzers will determine which issues are applicable for the planned migration and will only surface those.</span></span>

<span data-ttu-id="7c153-130">各問題には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7c153-130">Each issue includes the following information:</span></span>

-   <span data-ttu-id="7c153-131">以前のバージョンからの変更点の説明。</span><span class="sxs-lookup"><span data-stu-id="7c153-131">The description of what has changed from a previous version.</span></span>

-   <span data-ttu-id="7c153-132">変更が顧客に与える影響と、バージョン間で互換性を保つための回避策があるかどうかの説明。</span><span class="sxs-lookup"><span data-stu-id="7c153-132">How the change affects customers and whether any workarounds are available to preserve compatibility across versions.</span></span>

-   <span data-ttu-id="7c153-133">変更の重要性の評価。</span><span class="sxs-lookup"><span data-stu-id="7c153-133">An assessment of how important the change is.</span></span> <span data-ttu-id="7c153-134">アプリケーション互換性問題は、次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="7c153-134">Application compatibility issue are categorized as follows:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="7c153-135">Major</span><span class="sxs-lookup"><span data-stu-id="7c153-135">Major</span></span>|<span data-ttu-id="7c153-136">多数のアプリに影響するか、コードの大幅な変更を必要とする重大な変更。</span><span class="sxs-lookup"><span data-stu-id="7c153-136">A significant change that affects a large number of apps or requires substantial modification of code.</span></span>|
    |<span data-ttu-id="7c153-137">マイナー</span><span class="sxs-lookup"><span data-stu-id="7c153-137">Minor</span></span>|<span data-ttu-id="7c153-138">少数のアプリに影響するか、コードにわずかな変更を加える必要がある変更。</span><span class="sxs-lookup"><span data-stu-id="7c153-138">A change that affects a small number of apps or that requires minor modification of code.</span></span>|
    |<span data-ttu-id="7c153-139">エッジ ケース</span><span class="sxs-lookup"><span data-stu-id="7c153-139">Edge case</span></span>|<span data-ttu-id="7c153-140">非常に限られた一般的でないシナリオでアプリに影響を与える変更。</span><span class="sxs-lookup"><span data-stu-id="7c153-140">A change that affects apps under very specific, uncommon scenarios.</span></span>|
    |<span data-ttu-id="7c153-141">透明</span><span class="sxs-lookup"><span data-stu-id="7c153-141">Transparent</span></span>|<span data-ttu-id="7c153-142">アプリケーションの開発者やユーザーには大きな影響を及ぼさない変更。</span><span class="sxs-lookup"><span data-stu-id="7c153-142">A change with no noticeable effect on the application's developer or user.</span></span>|

-   <span data-ttu-id="7c153-143">バージョンは、フレームワークで変更が最初に適用されたバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="7c153-143">Version indicates when the change first appears in the framework.</span></span> <span data-ttu-id="7c153-144">変更によっては、特定のバージョンで導入され、それ以降のバージョンで元に戻されるものがあります。そのバージョンも同様に示されます。</span><span class="sxs-lookup"><span data-stu-id="7c153-144">Some of the changes are introduced in a particular version and reverted in a later version; that is indicated as well.</span></span>

-   <span data-ttu-id="7c153-145">変更の種類：</span><span class="sxs-lookup"><span data-stu-id="7c153-145">The type of change:</span></span>

    |   |   |
    |---|---|
    |<span data-ttu-id="7c153-146">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="7c153-146">Retargeting</span></span>|<span data-ttu-id="7c153-147">変更は、新しいバージョンの .NET Framework 向けに再コンパイルされるアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="7c153-147">The change affects apps that are recompiled to target a new version of the .NET Framework.</span></span>|
    |<span data-ttu-id="7c153-148">ランタイム</span><span class="sxs-lookup"><span data-stu-id="7c153-148">Runtime</span></span>|<span data-ttu-id="7c153-149">変更は、以前のバージョンの .NET Framework 向けだが、その後のバージョンでも実行する既存のアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="7c153-149">The change affects an existing app that targets a previous version of the .NET Framework but runs on a later version.</span></span>|

-   <span data-ttu-id="7c153-150">影響を受ける API (ある場合)。</span><span class="sxs-lookup"><span data-stu-id="7c153-150">The affected APIS, if any.</span></span>

-   <span data-ttu-id="7c153-151">使用可能な診断の ID</span><span class="sxs-lookup"><span data-stu-id="7c153-151">The IDs of the available diagnostics</span></span>

## <a name="usage"></a><span data-ttu-id="7c153-152">使用法</span><span class="sxs-lookup"><span data-stu-id="7c153-152">Usage</span></span>
<span data-ttu-id="7c153-153">開始するには、以下の中から互換性の変更の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="7c153-153">To begin, select the type of compatibility change below:</span></span>

* [<span data-ttu-id="7c153-154">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="7c153-154">Retargeting Changes</span></span>](./retargeting/index.md)
* [<span data-ttu-id="7c153-155">ランタイムの変更点</span><span class="sxs-lookup"><span data-stu-id="7c153-155">Runtime Changes</span></span>](./runtime/index.md)


## <a name="see-also"></a><span data-ttu-id="7c153-156">参照</span><span class="sxs-lookup"><span data-stu-id="7c153-156">See Also</span></span>

* [<span data-ttu-id="7c153-157">バージョンおよび依存関係</span><span class="sxs-lookup"><span data-stu-id="7c153-157">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [<span data-ttu-id="7c153-158">新機能</span><span class="sxs-lookup"><span data-stu-id="7c153-158">What's New</span></span>](../../../docs/framework/whats-new/index.md)
* [<span data-ttu-id="7c153-159">クラス ライブラリの互換性のために残されている機能</span><span class="sxs-lookup"><span data-stu-id="7c153-159">What's Obsolete in the Class Library</span></span>](../../../docs/framework/whats-new/whats-obsolete.md)
