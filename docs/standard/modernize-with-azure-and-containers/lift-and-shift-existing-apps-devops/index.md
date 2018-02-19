---
title: "既存のアプリの DevOps のリフト アンド シフト"
description: "Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 08bf7da36714b2c18d96659814bb11df6d9b26fc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="lift-and-shift-existing-apps-devops"></a><span data-ttu-id="e9cce-103">既存のアプリの DevOps のリフト アンド シフト</span><span class="sxs-lookup"><span data-stu-id="e9cce-103">Lift and shift existing apps DevOps</span></span>
> <span data-ttu-id="e9cce-104">ビジョン: 既存の .NET Framework アプリケーションを Cloud DevOps 対応アプリケーションにリフト アンド シフトすると、展開の機敏性が大幅に改善され、短期間で少ない配信コストで出荷できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e9cce-104">Vision: Lift and shift your existing .NET Framework applications to Cloud DevOps-Ready applications to drastically improve your deployment agility, so you can ship faster and lower app delivery costs.</span></span>

<span data-ttu-id="e9cce-105">クラウドやコンテナーなどの新しいテクノロジのメリットを活用するために、既存の .NET アプリケーションを少なくとも部分的に最新化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9cce-105">To take advantage of the benefits of the cloud and new technologies like containers, you should at least partially modernize your existing .NET applications.</span></span> <span data-ttu-id="e9cce-106">最終的に、エンタープライズ アプリケーションを最新化すると、総保有コストが低下します。</span><span class="sxs-lookup"><span data-stu-id="e9cce-106">Ultimately, modernizing your enterprise applications will lower your total cost of ownership.</span></span>

<span data-ttu-id="e9cce-107">アプリを部分的に最新化しても、完全な移行と再構築とは限りません。</span><span class="sxs-lookup"><span data-stu-id="e9cce-107">Partially modernizing an app doesn't necessarily mean a full migration and re-architecture.</span></span> <span data-ttu-id="e9cce-108">簡単かつ高速であるリフト アンド シフト プロセスを使用して、既存のアプリケーションを最初に最新化することができます。</span><span class="sxs-lookup"><span data-stu-id="e9cce-108">You can initially modernize your existing applications by using a lift and shift process that's easy and fast.</span></span> <span data-ttu-id="e9cce-109">Windows および IIS の依存関係がある既存の .NET Framework のバージョンで作成された現在のコード ベースを保守することができます。</span><span class="sxs-lookup"><span data-stu-id="e9cce-109">You can maintain your current code base, written in existing .NET Framework versions, with any Windows and IIS dependencies.</span></span> <span data-ttu-id="e9cce-110">図 4-1 は、Azure アプリケーション最新化成熟度モデル内でのクラウド DevOps 対応アプリの位置付けを示しています。</span><span class="sxs-lookup"><span data-stu-id="e9cce-110">Figure 4-1 highlights how Cloud DevOps-Ready apps are positioned in Azure application modernization maturity models.</span></span>

![クラウド DevOps 対応アプリケーションの位置付け](./media/image1.png)

> <span data-ttu-id="e9cce-112">**図 4-1**</span><span class="sxs-lookup"><span data-stu-id="e9cce-112">**Figure 4-1.**</span></span> <span data-ttu-id="e9cce-113">クラウド DevOps 対応アプリケーションの位置付け</span><span class="sxs-lookup"><span data-stu-id="e9cce-113">Positioning Cloud DevOps-Ready applications</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e9cce-114">[前へ](../migrate-your-relational-databases-to-azure.md)
[次へ](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)</span><span class="sxs-lookup"><span data-stu-id="e9cce-114">[Previous](../migrate-your-relational-databases-to-azure.md)
[Next](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)</span></span>
