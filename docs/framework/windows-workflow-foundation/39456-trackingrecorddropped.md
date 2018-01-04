---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 592d7c0a3725dcb50f7911a198c9dc9b7199a0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="b8e95-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="b8e95-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="b8e95-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b8e95-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8e95-104">ID</span><span class="sxs-lookup"><span data-stu-id="b8e95-104">ID</span></span>|<span data-ttu-id="b8e95-105">39456</span><span class="sxs-lookup"><span data-stu-id="b8e95-105">39456</span></span>|  
|<span data-ttu-id="b8e95-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b8e95-106">Keywords</span></span>|<span data-ttu-id="b8e95-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="b8e95-107">WFTracking</span></span>|  
|<span data-ttu-id="b8e95-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b8e95-108">Level</span></span>|<span data-ttu-id="b8e95-109">警告</span><span class="sxs-lookup"><span data-stu-id="b8e95-109">Warning</span></span>|  
|<span data-ttu-id="b8e95-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b8e95-110">Channel</span></span>|<span data-ttu-id="b8e95-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b8e95-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8e95-112">説明</span><span class="sxs-lookup"><span data-stu-id="b8e95-112">Description</span></span>  
 <span data-ttu-id="b8e95-113">サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="b8e95-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8e95-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b8e95-114">Message</span></span>  
 <span data-ttu-id="b8e95-115">追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="b8e95-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8e95-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b8e95-116">Details</span></span>  
  
|<span data-ttu-id="b8e95-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b8e95-117">Data Item Name</span></span>|<span data-ttu-id="b8e95-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b8e95-118">Data Item Type</span></span>|<span data-ttu-id="b8e95-119">説明</span><span class="sxs-lookup"><span data-stu-id="b8e95-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8e95-120">例外</span><span class="sxs-lookup"><span data-stu-id="b8e95-120">Exception</span></span>|<span data-ttu-id="b8e95-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8e95-121">xs:string</span></span>|<span data-ttu-id="b8e95-122">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="b8e95-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="b8e95-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8e95-123">AppDomain</span></span>|<span data-ttu-id="b8e95-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8e95-124">xs:string</span></span>|<span data-ttu-id="b8e95-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b8e95-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
