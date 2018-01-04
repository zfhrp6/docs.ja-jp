---
title: 403 - SuspendSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee1daab843ad0a2161d13b86bcd657b7236ddaa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="fea51-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="fea51-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="fea51-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fea51-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fea51-104">ID</span><span class="sxs-lookup"><span data-stu-id="fea51-104">ID</span></span>|<span data-ttu-id="fea51-105">403</span><span class="sxs-lookup"><span data-stu-id="fea51-105">403</span></span>|  
|<span data-ttu-id="fea51-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fea51-106">Keywords</span></span>|<span data-ttu-id="fea51-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fea51-107">Troubleshooting</span></span>|  
|<span data-ttu-id="fea51-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fea51-108">Level</span></span>|<span data-ttu-id="fea51-109">情報</span><span class="sxs-lookup"><span data-stu-id="fea51-109">Information</span></span>|  
|<span data-ttu-id="fea51-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fea51-110">Channel</span></span>|<span data-ttu-id="fea51-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="fea51-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fea51-112">説明</span><span class="sxs-lookup"><span data-stu-id="fea51-112">Description</span></span>  
 <span data-ttu-id="fea51-113">このイベントは、エンド ツー エンド アクティビティの中断を示します。</span><span class="sxs-lookup"><span data-stu-id="fea51-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="fea51-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="fea51-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fea51-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fea51-115">Message</span></span>  
 <span data-ttu-id="fea51-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="fea51-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fea51-117">詳細</span><span class="sxs-lookup"><span data-stu-id="fea51-117">Details</span></span>  
  
|<span data-ttu-id="fea51-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fea51-118">Data Item Name</span></span>|<span data-ttu-id="fea51-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fea51-119">Data Item Type</span></span>|<span data-ttu-id="fea51-120">説明</span><span class="sxs-lookup"><span data-stu-id="fea51-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fea51-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="fea51-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="fea51-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="fea51-122">The name of the activity.</span></span>|  
|<span data-ttu-id="fea51-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fea51-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fea51-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fea51-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
