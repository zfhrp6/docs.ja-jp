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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="560d2-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="560d2-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="560d2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="560d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="560d2-104">ID</span><span class="sxs-lookup"><span data-stu-id="560d2-104">ID</span></span>|<span data-ttu-id="560d2-105">39458</span><span class="sxs-lookup"><span data-stu-id="560d2-105">39458</span></span>|  
|<span data-ttu-id="560d2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="560d2-106">Keywords</span></span>|<span data-ttu-id="560d2-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="560d2-107">WFTracking</span></span>|  
|<span data-ttu-id="560d2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="560d2-108">Level</span></span>|<span data-ttu-id="560d2-109">警告</span><span class="sxs-lookup"><span data-stu-id="560d2-109">Warning</span></span>|  
|<span data-ttu-id="560d2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="560d2-110">Channel</span></span>|<span data-ttu-id="560d2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="560d2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="560d2-112">説明</span><span class="sxs-lookup"><span data-stu-id="560d2-112">Description</span></span>  
 <span data-ttu-id="560d2-113">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="560d2-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="560d2-114">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="560d2-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="560d2-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="560d2-115">Message</span></span>  
 <span data-ttu-id="560d2-116">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="560d2-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="560d2-117">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="560d2-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="560d2-118">詳細</span><span class="sxs-lookup"><span data-stu-id="560d2-118">Details</span></span>  
  
|<span data-ttu-id="560d2-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="560d2-119">Data Item Name</span></span>|<span data-ttu-id="560d2-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="560d2-120">Data Item Type</span></span>|<span data-ttu-id="560d2-121">説明</span><span class="sxs-lookup"><span data-stu-id="560d2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="560d2-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="560d2-122">RecordNumber</span></span>|<span data-ttu-id="560d2-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="560d2-123">xs:string</span></span>|<span data-ttu-id="560d2-124">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="560d2-124">The tracking record number.</span></span>|  
|<span data-ttu-id="560d2-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="560d2-125">ProviderId</span></span>|<span data-ttu-id="560d2-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="560d2-126">xs:string</span></span>|<span data-ttu-id="560d2-127">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="560d2-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="560d2-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="560d2-128">AppDomain</span></span>|<span data-ttu-id="560d2-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="560d2-129">xs:string</span></span>|<span data-ttu-id="560d2-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="560d2-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
