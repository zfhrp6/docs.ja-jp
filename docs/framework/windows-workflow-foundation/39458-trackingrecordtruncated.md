---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514483"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="6cb30-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="6cb30-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="6cb30-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6cb30-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cb30-104">ID</span><span class="sxs-lookup"><span data-stu-id="6cb30-104">ID</span></span>|<span data-ttu-id="6cb30-105">39458</span><span class="sxs-lookup"><span data-stu-id="6cb30-105">39458</span></span>|  
|<span data-ttu-id="6cb30-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6cb30-106">Keywords</span></span>|<span data-ttu-id="6cb30-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="6cb30-107">WFTracking</span></span>|  
|<span data-ttu-id="6cb30-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6cb30-108">Level</span></span>|<span data-ttu-id="6cb30-109">警告</span><span class="sxs-lookup"><span data-stu-id="6cb30-109">Warning</span></span>|  
|<span data-ttu-id="6cb30-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6cb30-110">Channel</span></span>|<span data-ttu-id="6cb30-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6cb30-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6cb30-112">説明</span><span class="sxs-lookup"><span data-stu-id="6cb30-112">Description</span></span>  
 <span data-ttu-id="6cb30-113">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="6cb30-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="6cb30-114">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="6cb30-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6cb30-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6cb30-115">Message</span></span>  
 <span data-ttu-id="6cb30-116">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="6cb30-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="6cb30-117">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="6cb30-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="6cb30-118">詳細</span><span class="sxs-lookup"><span data-stu-id="6cb30-118">Details</span></span>  
  
|<span data-ttu-id="6cb30-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6cb30-119">Data Item Name</span></span>|<span data-ttu-id="6cb30-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6cb30-120">Data Item Type</span></span>|<span data-ttu-id="6cb30-121">説明</span><span class="sxs-lookup"><span data-stu-id="6cb30-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6cb30-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="6cb30-122">RecordNumber</span></span>|<span data-ttu-id="6cb30-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cb30-123">xs:string</span></span>|<span data-ttu-id="6cb30-124">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="6cb30-124">The tracking record number.</span></span>|  
|<span data-ttu-id="6cb30-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="6cb30-125">ProviderId</span></span>|<span data-ttu-id="6cb30-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cb30-126">xs:string</span></span>|<span data-ttu-id="6cb30-127">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="6cb30-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="6cb30-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6cb30-128">AppDomain</span></span>|<span data-ttu-id="6cb30-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="6cb30-129">xs:string</span></span>|<span data-ttu-id="6cb30-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6cb30-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
