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
ms.openlocfilehash: 30e796dec45035e6b68659400ebbae1357137b27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="78d26-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="78d26-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="78d26-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="78d26-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78d26-104">ID</span><span class="sxs-lookup"><span data-stu-id="78d26-104">ID</span></span>|<span data-ttu-id="78d26-105">401</span><span class="sxs-lookup"><span data-stu-id="78d26-105">401</span></span>|  
|<span data-ttu-id="78d26-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="78d26-106">Keywords</span></span>|<span data-ttu-id="78d26-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="78d26-107">Troubleshooting</span></span>|  
|<span data-ttu-id="78d26-108">レベル</span><span class="sxs-lookup"><span data-stu-id="78d26-108">Level</span></span>|<span data-ttu-id="78d26-109">情報</span><span class="sxs-lookup"><span data-stu-id="78d26-109">Information</span></span>|  
|<span data-ttu-id="78d26-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="78d26-110">Channel</span></span>|<span data-ttu-id="78d26-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="78d26-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="78d26-112">説明</span><span class="sxs-lookup"><span data-stu-id="78d26-112">Description</span></span>  
 <span data-ttu-id="78d26-113">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="78d26-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="78d26-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="78d26-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="78d26-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="78d26-115">Message</span></span>  
 <span data-ttu-id="78d26-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="78d26-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78d26-117">詳細</span><span class="sxs-lookup"><span data-stu-id="78d26-117">Details</span></span>  
  
|<span data-ttu-id="78d26-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="78d26-118">Data Item Name</span></span>|<span data-ttu-id="78d26-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="78d26-119">Data Item Type</span></span>|<span data-ttu-id="78d26-120">説明</span><span class="sxs-lookup"><span data-stu-id="78d26-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="78d26-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="78d26-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="78d26-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="78d26-122">The name of the activity.</span></span>|  
|<span data-ttu-id="78d26-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="78d26-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="78d26-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="78d26-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
