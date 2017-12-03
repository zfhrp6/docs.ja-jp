---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="88b98-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="88b98-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="88b98-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="88b98-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88b98-104">ID</span><span class="sxs-lookup"><span data-stu-id="88b98-104">ID</span></span>|<span data-ttu-id="88b98-105">3552</span><span class="sxs-lookup"><span data-stu-id="88b98-105">3552</span></span>|  
|<span data-ttu-id="88b98-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="88b98-106">Keywords</span></span>|<span data-ttu-id="88b98-107">クォータ、WFServices</span><span class="sxs-lookup"><span data-stu-id="88b98-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="88b98-108">レベル</span><span class="sxs-lookup"><span data-stu-id="88b98-108">Level</span></span>|<span data-ttu-id="88b98-109">警告</span><span class="sxs-lookup"><span data-stu-id="88b98-109">Warning</span></span>|  
|<span data-ttu-id="88b98-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="88b98-110">Channel</span></span>|<span data-ttu-id="88b98-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="88b98-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="88b98-112">説明</span><span class="sxs-lookup"><span data-stu-id="88b98-112">Description</span></span>  
 <span data-ttu-id="88b98-113">スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="88b98-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="88b98-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="88b98-114">Message</span></span>  
 <span data-ttu-id="88b98-115">スロットル '%1' の 'MaxPendingMessagesPerChannel' 制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="88b98-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="88b98-116">この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。</span><span class="sxs-lookup"><span data-stu-id="88b98-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="88b98-117">詳細</span><span class="sxs-lookup"><span data-stu-id="88b98-117">Details</span></span>  
  
|<span data-ttu-id="88b98-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="88b98-118">Data Item Name</span></span>|<span data-ttu-id="88b98-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="88b98-119">Data Item Type</span></span>|<span data-ttu-id="88b98-120">説明</span><span class="sxs-lookup"><span data-stu-id="88b98-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="88b98-121">Limit</span><span class="sxs-lookup"><span data-stu-id="88b98-121">Limit</span></span>|<span data-ttu-id="88b98-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="88b98-122">xs:string</span></span>|<span data-ttu-id="88b98-123">MaxPendingMessagesPerChannel スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="88b98-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="88b98-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="88b98-124">AppDomain</span></span>|<span data-ttu-id="88b98-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="88b98-125">xs:string</span></span>|<span data-ttu-id="88b98-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="88b98-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
