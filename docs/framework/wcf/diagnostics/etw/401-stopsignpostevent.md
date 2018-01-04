---
title: 401- StopSignPostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 058cae31c70e2c415e27870af1a0064b84a70b12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="16cb8-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="16cb8-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="16cb8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="16cb8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16cb8-104">ID</span><span class="sxs-lookup"><span data-stu-id="16cb8-104">ID</span></span>|<span data-ttu-id="16cb8-105">401</span><span class="sxs-lookup"><span data-stu-id="16cb8-105">401</span></span>|  
|<span data-ttu-id="16cb8-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="16cb8-106">Keywords</span></span>|<span data-ttu-id="16cb8-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="16cb8-107">Troubleshooting</span></span>|  
|<span data-ttu-id="16cb8-108">レベル</span><span class="sxs-lookup"><span data-stu-id="16cb8-108">Level</span></span>|<span data-ttu-id="16cb8-109">情報</span><span class="sxs-lookup"><span data-stu-id="16cb8-109">Information</span></span>|  
|<span data-ttu-id="16cb8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="16cb8-110">Channel</span></span>|<span data-ttu-id="16cb8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="16cb8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16cb8-112">説明</span><span class="sxs-lookup"><span data-stu-id="16cb8-112">Description</span></span>  
 <span data-ttu-id="16cb8-113">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="16cb8-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="16cb8-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="16cb8-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16cb8-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="16cb8-115">Message</span></span>  
 <span data-ttu-id="16cb8-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="16cb8-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16cb8-117">詳細</span><span class="sxs-lookup"><span data-stu-id="16cb8-117">Details</span></span>  
  
|<span data-ttu-id="16cb8-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="16cb8-118">Data Item Name</span></span>|<span data-ttu-id="16cb8-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="16cb8-119">Data Item Type</span></span>|<span data-ttu-id="16cb8-120">説明</span><span class="sxs-lookup"><span data-stu-id="16cb8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16cb8-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="16cb8-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="16cb8-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="16cb8-122">The name of the activity.</span></span>|  
|<span data-ttu-id="16cb8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16cb8-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="16cb8-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="16cb8-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
