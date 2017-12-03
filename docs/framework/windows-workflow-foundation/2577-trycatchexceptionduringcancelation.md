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
ms.openlocfilehash: 11781bcab37a5034f3bbfadf2c50cbc1c6d378a2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="01279-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="01279-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="01279-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="01279-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01279-104">ID</span><span class="sxs-lookup"><span data-stu-id="01279-104">ID</span></span>|<span data-ttu-id="01279-105">2577</span><span class="sxs-lookup"><span data-stu-id="01279-105">2577</span></span>|  
|<span data-ttu-id="01279-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="01279-106">Keywords</span></span>|<span data-ttu-id="01279-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="01279-107">WFActivities</span></span>|  
|<span data-ttu-id="01279-108">レベル</span><span class="sxs-lookup"><span data-stu-id="01279-108">Level</span></span>|<span data-ttu-id="01279-109">警告</span><span class="sxs-lookup"><span data-stu-id="01279-109">Warning</span></span>|  
|<span data-ttu-id="01279-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="01279-110">Channel</span></span>|<span data-ttu-id="01279-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="01279-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01279-112">説明</span><span class="sxs-lookup"><span data-stu-id="01279-112">Description</span></span>  
 <span data-ttu-id="01279-113">TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="01279-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01279-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="01279-114">Message</span></span>  
 <span data-ttu-id="01279-115">TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="01279-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01279-116">詳細</span><span class="sxs-lookup"><span data-stu-id="01279-116">Details</span></span>  
  
|<span data-ttu-id="01279-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="01279-117">Data Item Name</span></span>|<span data-ttu-id="01279-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="01279-118">Data Item Type</span></span>|<span data-ttu-id="01279-119">説明</span><span class="sxs-lookup"><span data-stu-id="01279-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01279-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="01279-120">DisplayName</span></span>|<span data-ttu-id="01279-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="01279-121">xs:string</span></span>|<span data-ttu-id="01279-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="01279-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="01279-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01279-123">AppDomain</span></span>|<span data-ttu-id="01279-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="01279-124">xs:string</span></span>|<span data-ttu-id="01279-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="01279-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
