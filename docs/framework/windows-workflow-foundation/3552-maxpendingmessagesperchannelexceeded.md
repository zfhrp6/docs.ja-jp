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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="39c34-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="39c34-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="39c34-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="39c34-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39c34-104">ID</span><span class="sxs-lookup"><span data-stu-id="39c34-104">ID</span></span>|<span data-ttu-id="39c34-105">3552</span><span class="sxs-lookup"><span data-stu-id="39c34-105">3552</span></span>|  
|<span data-ttu-id="39c34-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="39c34-106">Keywords</span></span>|<span data-ttu-id="39c34-107">クォータ、WFServices</span><span class="sxs-lookup"><span data-stu-id="39c34-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="39c34-108">レベル</span><span class="sxs-lookup"><span data-stu-id="39c34-108">Level</span></span>|<span data-ttu-id="39c34-109">警告</span><span class="sxs-lookup"><span data-stu-id="39c34-109">Warning</span></span>|  
|<span data-ttu-id="39c34-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="39c34-110">Channel</span></span>|<span data-ttu-id="39c34-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="39c34-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="39c34-112">説明</span><span class="sxs-lookup"><span data-stu-id="39c34-112">Description</span></span>  
 <span data-ttu-id="39c34-113">スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="39c34-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="39c34-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="39c34-114">Message</span></span>  
 <span data-ttu-id="39c34-115">スロットル '%1' の 'MaxPendingMessagesPerChannel' 制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="39c34-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="39c34-116">この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。</span><span class="sxs-lookup"><span data-stu-id="39c34-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="39c34-117">詳細</span><span class="sxs-lookup"><span data-stu-id="39c34-117">Details</span></span>  
  
|<span data-ttu-id="39c34-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="39c34-118">Data Item Name</span></span>|<span data-ttu-id="39c34-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="39c34-119">Data Item Type</span></span>|<span data-ttu-id="39c34-120">説明</span><span class="sxs-lookup"><span data-stu-id="39c34-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="39c34-121">Limit</span><span class="sxs-lookup"><span data-stu-id="39c34-121">Limit</span></span>|<span data-ttu-id="39c34-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="39c34-122">xs:string</span></span>|<span data-ttu-id="39c34-123">MaxPendingMessagesPerChannel スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="39c34-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="39c34-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="39c34-124">AppDomain</span></span>|<span data-ttu-id="39c34-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="39c34-125">xs:string</span></span>|<span data-ttu-id="39c34-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="39c34-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
