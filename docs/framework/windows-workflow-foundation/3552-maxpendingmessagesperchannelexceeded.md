---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511232"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="76359-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="76359-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="76359-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="76359-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="76359-104">ID</span><span class="sxs-lookup"><span data-stu-id="76359-104">ID</span></span>|<span data-ttu-id="76359-105">3552</span><span class="sxs-lookup"><span data-stu-id="76359-105">3552</span></span>|  
|<span data-ttu-id="76359-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="76359-106">Keywords</span></span>|<span data-ttu-id="76359-107">クォータ、WFServices</span><span class="sxs-lookup"><span data-stu-id="76359-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="76359-108">レベル</span><span class="sxs-lookup"><span data-stu-id="76359-108">Level</span></span>|<span data-ttu-id="76359-109">警告</span><span class="sxs-lookup"><span data-stu-id="76359-109">Warning</span></span>|  
|<span data-ttu-id="76359-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="76359-110">Channel</span></span>|<span data-ttu-id="76359-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="76359-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="76359-112">説明</span><span class="sxs-lookup"><span data-stu-id="76359-112">Description</span></span>  
 <span data-ttu-id="76359-113">スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="76359-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="76359-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="76359-114">Message</span></span>  
 <span data-ttu-id="76359-115">スロットル '%1' の 'MaxPendingMessagesPerChannel' 制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="76359-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="76359-116">この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。</span><span class="sxs-lookup"><span data-stu-id="76359-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="76359-117">詳細</span><span class="sxs-lookup"><span data-stu-id="76359-117">Details</span></span>  
  
|<span data-ttu-id="76359-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="76359-118">Data Item Name</span></span>|<span data-ttu-id="76359-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="76359-119">Data Item Type</span></span>|<span data-ttu-id="76359-120">説明</span><span class="sxs-lookup"><span data-stu-id="76359-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="76359-121">Limit</span><span class="sxs-lookup"><span data-stu-id="76359-121">Limit</span></span>|<span data-ttu-id="76359-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="76359-122">xs:string</span></span>|<span data-ttu-id="76359-123">MaxPendingMessagesPerChannel スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="76359-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="76359-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="76359-124">AppDomain</span></span>|<span data-ttu-id="76359-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="76359-125">xs:string</span></span>|<span data-ttu-id="76359-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="76359-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
