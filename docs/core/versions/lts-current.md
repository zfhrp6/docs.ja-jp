---
title: .NET Core サポート
description: .NET Core のさまざまなリリース トレーニング サポート (LTS と現在) について説明します。
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.openlocfilehash: b61aa48451cee60be4968c151b97746a3aef85c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212737"
---
# <a name="net-core-support"></a><span data-ttu-id="0991a-103">.NET Core サポート</span><span class="sxs-lookup"><span data-stu-id="0991a-103">.NET Core Support</span></span>

<span data-ttu-id="0991a-104">これは .NET Core サポートの一般的な説明です。</span><span class="sxs-lookup"><span data-stu-id="0991a-104">This is a general description of .NET Core support.</span></span>

## <a name="lts-and-current-release-trains"></a><span data-ttu-id="0991a-105">LTS と現在のリリース トレーニング</span><span class="sxs-lookup"><span data-stu-id="0991a-105">LTS and Current Release Trains</span></span>

<span data-ttu-id="0991a-106">2 つのサポート リリース トレーニングを用意することは、ソフトウェア業界、特に、.NET Core のようなオープンソース プロジェクトで一般的に利用されている共通の概念です。</span><span class="sxs-lookup"><span data-stu-id="0991a-106">Having two support release trains is a common concept in use throughout the software world, specially for open-source projects like .NET Core.</span></span> <span data-ttu-id="0991a-107">.NET Core には、[LTS (Long Term Support/長期サポート)](https://en.wikipedia.org/wiki/Long-term_support) と現在というサポート リリース トレーニングがあります。</span><span class="sxs-lookup"><span data-stu-id="0991a-107">.NET Core has the following support release trains: [Long Term Support (LTS)](https://en.wikipedia.org/wiki/Long-term_support) and Current.</span></span> <span data-ttu-id="0991a-108">LTS はライフサイクルを通して安定してご利用いただくためのものであり、重大な問題の修正プログラムやセキュリティ上の修正プログラムが提供されます。</span><span class="sxs-lookup"><span data-stu-id="0991a-108">LTS releases are maintained for stability over their lifecycle, receiving fixes for important issues and security fixes.</span></span> <span data-ttu-id="0991a-109">新機能の動作と追加のバグ修正は現在のリリースで提供されます。</span><span class="sxs-lookup"><span data-stu-id="0991a-109">New feature work and additional bug fixes take place in Current releases.</span></span> <span data-ttu-id="0991a-110">サポートの観点から、リリース トレーニングには次のサポート ライフサイクル属性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="0991a-110">From a support perspective, these release trains have the following support lifecycle attributes.</span></span>

<span data-ttu-id="0991a-111">LTS リリースのサポート期間</span><span class="sxs-lookup"><span data-stu-id="0991a-111">LTS releases are</span></span>
* <span data-ttu-id="0991a-112">LTS リリースの一般公開日から 3 年間</span><span class="sxs-lookup"><span data-stu-id="0991a-112">Supported for three years after the general availability date of a LTS release</span></span>
* <span data-ttu-id="0991a-113">または後続の LTS リリースの一般公開から 1 年間</span><span class="sxs-lookup"><span data-stu-id="0991a-113">Or one year after the general availability of a subsequent LTS release</span></span>

<span data-ttu-id="0991a-114">現在のリリースのサポート期間</span><span class="sxs-lookup"><span data-stu-id="0991a-114">Current releases are</span></span>
* <span data-ttu-id="0991a-115">親 LTS リリースと同じ 3 年間</span><span class="sxs-lookup"><span data-stu-id="0991a-115">Supported within the same three-year window as the parent LTS release</span></span>
* <span data-ttu-id="0991a-116">後続の現在のリリースの一般公開から 3 か月</span><span class="sxs-lookup"><span data-stu-id="0991a-116">Supported for three months after the general availability of a subsequent Current release</span></span>
* <span data-ttu-id="0991a-117">および後続の LTS リリースの一般公開から 1 年間</span><span class="sxs-lookup"><span data-stu-id="0991a-117">And one year after the general availability of a subsequent LTS release</span></span>

## <a name="versioning"></a><span data-ttu-id="0991a-118">バージョン管理</span><span class="sxs-lookup"><span data-stu-id="0991a-118">Versioning</span></span>
<span data-ttu-id="0991a-119">新しい LTS リリースが発表されると、メジャー バージョン番号が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="0991a-119">New LTS releases are marked by an increase in the Major version number.</span></span> <span data-ttu-id="0991a-120">現在のリリースにはそれに対応する LTS トレーニングと同じメジャー番号が与えられ、マイナー バージョン番号が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="0991a-120">Current releases have the same Major number as the corresponding LTS train and are marked by an increase in the Minor version number.</span></span> <span data-ttu-id="0991a-121">たとえば、1.0.3 が LTS で、1.1.0 が現在になります。</span><span class="sxs-lookup"><span data-stu-id="0991a-121">For example, 1.0.3 would be LTS and 1.1.0 would be Current.</span></span> <span data-ttu-id="0991a-122">いずれかのトレーニングをバグ修正でアップデートすると、パッチ番号が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="0991a-122">Bug fix updates to either train increment the Patch version.</span></span> <span data-ttu-id="0991a-123">バージョン管理スキームの詳細については、「[.NET Core バージョン管理](index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0991a-123">For more information on the versioning scheme, see [.NET Core Versioning](index.md).</span></span>

## <a name="what-causes-updates-in-lts-and-current-trains"></a><span data-ttu-id="0991a-124">LTS トレーニングと現在のトレーニングが更新されるしくみ</span><span class="sxs-lookup"><span data-stu-id="0991a-124">What causes updates in LTS and Current trains?</span></span>
<span data-ttu-id="0991a-125">バグ修正や API 追加など、特定の変更によりバージョン番号が更新されるしくみを理解するには、「[Versioning Documentation](index.md)」 (バージョン管理文書) の「デシジョン ツリー」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0991a-125">To understand what specific changes, such as bug fixes or the addition of APIs, cause updates to the version numbers review the Decision Tree section in the [Versioning Documentation](index.md).</span></span> <span data-ttu-id="0991a-126">現在から LTS 分岐に引き出される変更を決定する絶対的な規則というものはありません。</span><span class="sxs-lookup"><span data-stu-id="0991a-126">There is not a golden set of rules that decide what changes are pulled into the LTS branch from Current.</span></span> <span data-ttu-id="0991a-127">一般的には、セキュリティ上の更新や動作を修正するパッチが必要となった場合、LTS 分岐の更新が求められます。</span><span class="sxs-lookup"><span data-stu-id="0991a-127">Typically, necessary security updates and patches that fix expected behaviour are reasons to update the LTS branch.</span></span> <span data-ttu-id="0991a-128">LTS 分岐で最近のデスクトップ開発者オペレーティング システムをサポートする予定もありますが、それは常に可能というわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0991a-128">We also intend to support recent desktop developer operating systems on the LTS branch, though this may not always be possible.</span></span> <span data-ttu-id="0991a-129">特定のリリースでサポートされている API、修正プログラム、オペレーティング システムを理解するには、GitHub でその[リリース ノート](https://github.com/dotnet/core/tree/master/release-notes)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0991a-129">A good way to catch up on what APIs, fixes, and operating systems are supported in a certain release is to browse its [release notes](https://github.com/dotnet/core/tree/master/release-notes) on GitHub.</span></span>

### <a name="further-reading"></a><span data-ttu-id="0991a-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0991a-130">Further Reading</span></span>
* [<span data-ttu-id="0991a-131">.NET Core サポート ライフサイクルのファクト シート</span><span class="sxs-lookup"><span data-stu-id="0991a-131">.NET Core Support Lifecycle Fact Sheet</span></span>](https://www.microsoft.com/net/core/support)
* [<span data-ttu-id="0991a-132">現在サポートされているオペレーティング システムとバージョン</span><span class="sxs-lookup"><span data-stu-id="0991a-132">Currently supported operating systems and versions</span></span>](https://github.com/dotnet/core/blob/master/roadmap.md)
