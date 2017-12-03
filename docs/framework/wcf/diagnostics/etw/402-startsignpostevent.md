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
ms.openlocfilehash: 2ade357acdebc6222e59bf5b15725a1edc97dc43
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="bd8b4-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="bd8b4-102">402 - StartSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="bd8b4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bd8b4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd8b4-104">ID</span><span class="sxs-lookup"><span data-stu-id="bd8b4-104">ID</span></span>|<span data-ttu-id="bd8b4-105">402</span><span class="sxs-lookup"><span data-stu-id="bd8b4-105">402</span></span>|  
|<span data-ttu-id="bd8b4-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bd8b4-106">Keywords</span></span>|<span data-ttu-id="bd8b4-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bd8b4-107">Troubleshooting</span></span>|  
|<span data-ttu-id="bd8b4-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bd8b4-108">Level</span></span>|<span data-ttu-id="bd8b4-109">情報</span><span class="sxs-lookup"><span data-stu-id="bd8b4-109">Information</span></span>|  
|<span data-ttu-id="bd8b4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bd8b4-110">Channel</span></span>|<span data-ttu-id="bd8b4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bd8b4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bd8b4-112">説明</span><span class="sxs-lookup"><span data-stu-id="bd8b4-112">Description</span></span>  
 <span data-ttu-id="bd8b4-113">このイベントは、エンド ツー エンド アクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="bd8b4-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="bd8b4-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="bd8b4-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bd8b4-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bd8b4-115">Message</span></span>  
 <span data-ttu-id="bd8b4-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="bd8b4-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bd8b4-117">詳細</span><span class="sxs-lookup"><span data-stu-id="bd8b4-117">Details</span></span>  
  
|<span data-ttu-id="bd8b4-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bd8b4-118">Data Item Name</span></span>|<span data-ttu-id="bd8b4-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bd8b4-119">Data Item Type</span></span>|<span data-ttu-id="bd8b4-120">説明</span><span class="sxs-lookup"><span data-stu-id="bd8b4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bd8b4-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="bd8b4-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="bd8b4-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="bd8b4-122">The name of the activity.</span></span>|  
|<span data-ttu-id="bd8b4-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bd8b4-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bd8b4-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bd8b4-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
