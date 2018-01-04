---
title: 402 - StartSignpostEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62587e6aa15ef57d5fee349795dfd60bb52812d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="a2278-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="a2278-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="a2278-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a2278-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2278-104">ID</span><span class="sxs-lookup"><span data-stu-id="a2278-104">ID</span></span>|<span data-ttu-id="a2278-105">402</span><span class="sxs-lookup"><span data-stu-id="a2278-105">402</span></span>|  
|<span data-ttu-id="a2278-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a2278-106">Keywords</span></span>|<span data-ttu-id="a2278-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a2278-107">Troubleshooting</span></span>|  
|<span data-ttu-id="a2278-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a2278-108">Level</span></span>|<span data-ttu-id="a2278-109">情報</span><span class="sxs-lookup"><span data-stu-id="a2278-109">Information</span></span>|  
|<span data-ttu-id="a2278-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a2278-110">Channel</span></span>|<span data-ttu-id="a2278-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a2278-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a2278-112">説明</span><span class="sxs-lookup"><span data-stu-id="a2278-112">Description</span></span>  
 <span data-ttu-id="a2278-113">このイベントは、エンド ツー エンド アクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="a2278-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="a2278-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="a2278-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a2278-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a2278-115">Message</span></span>  
 <span data-ttu-id="a2278-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="a2278-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a2278-117">詳細</span><span class="sxs-lookup"><span data-stu-id="a2278-117">Details</span></span>  
  
|<span data-ttu-id="a2278-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a2278-118">Data Item Name</span></span>|<span data-ttu-id="a2278-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a2278-119">Data Item Type</span></span>|<span data-ttu-id="a2278-120">説明</span><span class="sxs-lookup"><span data-stu-id="a2278-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a2278-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="a2278-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="a2278-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="a2278-122">The name of the activity.</span></span>|  
|<span data-ttu-id="a2278-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a2278-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a2278-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a2278-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
