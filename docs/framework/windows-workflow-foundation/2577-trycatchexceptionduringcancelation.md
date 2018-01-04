---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="736f0-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="736f0-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="736f0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="736f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="736f0-104">ID</span><span class="sxs-lookup"><span data-stu-id="736f0-104">ID</span></span>|<span data-ttu-id="736f0-105">2577</span><span class="sxs-lookup"><span data-stu-id="736f0-105">2577</span></span>|  
|<span data-ttu-id="736f0-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="736f0-106">Keywords</span></span>|<span data-ttu-id="736f0-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="736f0-107">WFActivities</span></span>|  
|<span data-ttu-id="736f0-108">レベル</span><span class="sxs-lookup"><span data-stu-id="736f0-108">Level</span></span>|<span data-ttu-id="736f0-109">警告</span><span class="sxs-lookup"><span data-stu-id="736f0-109">Warning</span></span>|  
|<span data-ttu-id="736f0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="736f0-110">Channel</span></span>|<span data-ttu-id="736f0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="736f0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="736f0-112">説明</span><span class="sxs-lookup"><span data-stu-id="736f0-112">Description</span></span>  
 <span data-ttu-id="736f0-113">TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="736f0-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="736f0-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="736f0-114">Message</span></span>  
 <span data-ttu-id="736f0-115">TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="736f0-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="736f0-116">詳細</span><span class="sxs-lookup"><span data-stu-id="736f0-116">Details</span></span>  
  
|<span data-ttu-id="736f0-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="736f0-117">Data Item Name</span></span>|<span data-ttu-id="736f0-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="736f0-118">Data Item Type</span></span>|<span data-ttu-id="736f0-119">説明</span><span class="sxs-lookup"><span data-stu-id="736f0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="736f0-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="736f0-120">DisplayName</span></span>|<span data-ttu-id="736f0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="736f0-121">xs:string</span></span>|<span data-ttu-id="736f0-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="736f0-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="736f0-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="736f0-123">AppDomain</span></span>|<span data-ttu-id="736f0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="736f0-124">xs:string</span></span>|<span data-ttu-id="736f0-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="736f0-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
