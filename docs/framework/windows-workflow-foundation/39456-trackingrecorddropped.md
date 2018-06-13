---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510706"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="85128-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="85128-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="85128-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="85128-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85128-104">ID</span><span class="sxs-lookup"><span data-stu-id="85128-104">ID</span></span>|<span data-ttu-id="85128-105">39456</span><span class="sxs-lookup"><span data-stu-id="85128-105">39456</span></span>|  
|<span data-ttu-id="85128-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="85128-106">Keywords</span></span>|<span data-ttu-id="85128-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="85128-107">WFTracking</span></span>|  
|<span data-ttu-id="85128-108">レベル</span><span class="sxs-lookup"><span data-stu-id="85128-108">Level</span></span>|<span data-ttu-id="85128-109">警告</span><span class="sxs-lookup"><span data-stu-id="85128-109">Warning</span></span>|  
|<span data-ttu-id="85128-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="85128-110">Channel</span></span>|<span data-ttu-id="85128-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="85128-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="85128-112">説明</span><span class="sxs-lookup"><span data-stu-id="85128-112">Description</span></span>  
 <span data-ttu-id="85128-113">サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="85128-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="85128-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="85128-114">Message</span></span>  
 <span data-ttu-id="85128-115">追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="85128-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="85128-116">詳細</span><span class="sxs-lookup"><span data-stu-id="85128-116">Details</span></span>  
  
|<span data-ttu-id="85128-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="85128-117">Data Item Name</span></span>|<span data-ttu-id="85128-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="85128-118">Data Item Type</span></span>|<span data-ttu-id="85128-119">説明</span><span class="sxs-lookup"><span data-stu-id="85128-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="85128-120">例外</span><span class="sxs-lookup"><span data-stu-id="85128-120">Exception</span></span>|<span data-ttu-id="85128-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="85128-121">xs:string</span></span>|<span data-ttu-id="85128-122">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="85128-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="85128-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="85128-123">AppDomain</span></span>|<span data-ttu-id="85128-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="85128-124">xs:string</span></span>|<span data-ttu-id="85128-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="85128-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
