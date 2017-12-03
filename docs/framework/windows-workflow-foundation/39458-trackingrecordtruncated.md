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
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="951cc-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="951cc-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="951cc-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="951cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="951cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="951cc-104">ID</span></span>|<span data-ttu-id="951cc-105">39458</span><span class="sxs-lookup"><span data-stu-id="951cc-105">39458</span></span>|  
|<span data-ttu-id="951cc-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="951cc-106">Keywords</span></span>|<span data-ttu-id="951cc-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="951cc-107">WFTracking</span></span>|  
|<span data-ttu-id="951cc-108">レベル</span><span class="sxs-lookup"><span data-stu-id="951cc-108">Level</span></span>|<span data-ttu-id="951cc-109">警告</span><span class="sxs-lookup"><span data-stu-id="951cc-109">Warning</span></span>|  
|<span data-ttu-id="951cc-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="951cc-110">Channel</span></span>|<span data-ttu-id="951cc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="951cc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="951cc-112">説明</span><span class="sxs-lookup"><span data-stu-id="951cc-112">Description</span></span>  
 <span data-ttu-id="951cc-113">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="951cc-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="951cc-114">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="951cc-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="951cc-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="951cc-115">Message</span></span>  
 <span data-ttu-id="951cc-116">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="951cc-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="951cc-117">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="951cc-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="951cc-118">詳細</span><span class="sxs-lookup"><span data-stu-id="951cc-118">Details</span></span>  
  
|<span data-ttu-id="951cc-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="951cc-119">Data Item Name</span></span>|<span data-ttu-id="951cc-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="951cc-120">Data Item Type</span></span>|<span data-ttu-id="951cc-121">説明</span><span class="sxs-lookup"><span data-stu-id="951cc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="951cc-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="951cc-122">RecordNumber</span></span>|<span data-ttu-id="951cc-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="951cc-123">xs:string</span></span>|<span data-ttu-id="951cc-124">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="951cc-124">The tracking record number.</span></span>|  
|<span data-ttu-id="951cc-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="951cc-125">ProviderId</span></span>|<span data-ttu-id="951cc-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="951cc-126">xs:string</span></span>|<span data-ttu-id="951cc-127">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="951cc-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="951cc-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="951cc-128">AppDomain</span></span>|<span data-ttu-id="951cc-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="951cc-129">xs:string</span></span>|<span data-ttu-id="951cc-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="951cc-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
