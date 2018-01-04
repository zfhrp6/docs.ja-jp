---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d12549d201ac621361bd6a517df6c6b53ab7aec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="4c5ad-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="4c5ad-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="4c5ad-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4c5ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c5ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="4c5ad-104">ID</span></span>|<span data-ttu-id="4c5ad-105">39458</span><span class="sxs-lookup"><span data-stu-id="4c5ad-105">39458</span></span>|  
|<span data-ttu-id="4c5ad-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="4c5ad-106">Keywords</span></span>|<span data-ttu-id="4c5ad-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="4c5ad-107">WFTracking</span></span>|  
|<span data-ttu-id="4c5ad-108">レベル</span><span class="sxs-lookup"><span data-stu-id="4c5ad-108">Level</span></span>|<span data-ttu-id="4c5ad-109">警告</span><span class="sxs-lookup"><span data-stu-id="4c5ad-109">Warning</span></span>|  
|<span data-ttu-id="4c5ad-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4c5ad-110">Channel</span></span>|<span data-ttu-id="4c5ad-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4c5ad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4c5ad-112">説明</span><span class="sxs-lookup"><span data-stu-id="4c5ad-112">Description</span></span>  
 <span data-ttu-id="4c5ad-113">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="4c5ad-114">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4c5ad-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="4c5ad-115">Message</span></span>  
 <span data-ttu-id="4c5ad-116">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="4c5ad-117">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="4c5ad-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="4c5ad-118">詳細</span><span class="sxs-lookup"><span data-stu-id="4c5ad-118">Details</span></span>  
  
|<span data-ttu-id="4c5ad-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4c5ad-119">Data Item Name</span></span>|<span data-ttu-id="4c5ad-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4c5ad-120">Data Item Type</span></span>|<span data-ttu-id="4c5ad-121">説明</span><span class="sxs-lookup"><span data-stu-id="4c5ad-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4c5ad-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="4c5ad-122">RecordNumber</span></span>|<span data-ttu-id="4c5ad-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c5ad-123">xs:string</span></span>|<span data-ttu-id="4c5ad-124">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-124">The tracking record number.</span></span>|  
|<span data-ttu-id="4c5ad-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="4c5ad-125">ProviderId</span></span>|<span data-ttu-id="4c5ad-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c5ad-126">xs:string</span></span>|<span data-ttu-id="4c5ad-127">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="4c5ad-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4c5ad-128">AppDomain</span></span>|<span data-ttu-id="4c5ad-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="4c5ad-129">xs:string</span></span>|<span data-ttu-id="4c5ad-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4c5ad-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
