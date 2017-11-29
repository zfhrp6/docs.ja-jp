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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10e745ded72caa493119d7e27a5c777b2185b96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="dadc9-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="dadc9-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="dadc9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="dadc9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dadc9-104">ID</span><span class="sxs-lookup"><span data-stu-id="dadc9-104">ID</span></span>|<span data-ttu-id="dadc9-105">403</span><span class="sxs-lookup"><span data-stu-id="dadc9-105">403</span></span>|  
|<span data-ttu-id="dadc9-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="dadc9-106">Keywords</span></span>|<span data-ttu-id="dadc9-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="dadc9-107">Troubleshooting</span></span>|  
|<span data-ttu-id="dadc9-108">レベル</span><span class="sxs-lookup"><span data-stu-id="dadc9-108">Level</span></span>|<span data-ttu-id="dadc9-109">情報</span><span class="sxs-lookup"><span data-stu-id="dadc9-109">Information</span></span>|  
|<span data-ttu-id="dadc9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="dadc9-110">Channel</span></span>|<span data-ttu-id="dadc9-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="dadc9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dadc9-112">説明</span><span class="sxs-lookup"><span data-stu-id="dadc9-112">Description</span></span>  
 <span data-ttu-id="dadc9-113">このイベントは、エンド ツー エンド アクティビティの中断を示します。</span><span class="sxs-lookup"><span data-stu-id="dadc9-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="dadc9-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="dadc9-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dadc9-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="dadc9-115">Message</span></span>  
 <span data-ttu-id="dadc9-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="dadc9-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dadc9-117">詳細</span><span class="sxs-lookup"><span data-stu-id="dadc9-117">Details</span></span>  
  
|<span data-ttu-id="dadc9-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="dadc9-118">Data Item Name</span></span>|<span data-ttu-id="dadc9-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="dadc9-119">Data Item Type</span></span>|<span data-ttu-id="dadc9-120">説明</span><span class="sxs-lookup"><span data-stu-id="dadc9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dadc9-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="dadc9-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="dadc9-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="dadc9-122">The name of the activity.</span></span>|  
|<span data-ttu-id="dadc9-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dadc9-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dadc9-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="dadc9-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
