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
ms.openlocfilehash: de056ffcdfeb3ea5dee9eaca213fe96ee991d067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="94487-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="94487-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="94487-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="94487-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94487-104">ID</span><span class="sxs-lookup"><span data-stu-id="94487-104">ID</span></span>|<span data-ttu-id="94487-105">39456</span><span class="sxs-lookup"><span data-stu-id="94487-105">39456</span></span>|  
|<span data-ttu-id="94487-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="94487-106">Keywords</span></span>|<span data-ttu-id="94487-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="94487-107">WFTracking</span></span>|  
|<span data-ttu-id="94487-108">レベル</span><span class="sxs-lookup"><span data-stu-id="94487-108">Level</span></span>|<span data-ttu-id="94487-109">警告</span><span class="sxs-lookup"><span data-stu-id="94487-109">Warning</span></span>|  
|<span data-ttu-id="94487-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="94487-110">Channel</span></span>|<span data-ttu-id="94487-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="94487-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="94487-112">説明</span><span class="sxs-lookup"><span data-stu-id="94487-112">Description</span></span>  
 <span data-ttu-id="94487-113">サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="94487-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="94487-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="94487-114">Message</span></span>  
 <span data-ttu-id="94487-115">追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="94487-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="94487-116">詳細</span><span class="sxs-lookup"><span data-stu-id="94487-116">Details</span></span>  
  
|<span data-ttu-id="94487-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="94487-117">Data Item Name</span></span>|<span data-ttu-id="94487-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="94487-118">Data Item Type</span></span>|<span data-ttu-id="94487-119">説明</span><span class="sxs-lookup"><span data-stu-id="94487-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="94487-120">例外</span><span class="sxs-lookup"><span data-stu-id="94487-120">Exception</span></span>|<span data-ttu-id="94487-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="94487-121">xs:string</span></span>|<span data-ttu-id="94487-122">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="94487-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="94487-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="94487-123">AppDomain</span></span>|<span data-ttu-id="94487-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="94487-124">xs:string</span></span>|<span data-ttu-id="94487-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="94487-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
