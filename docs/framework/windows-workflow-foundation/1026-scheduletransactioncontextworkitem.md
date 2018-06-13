---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 6d0b43208f86c52e8863d4415a64466b0531832c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510284"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="af8ac-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="af8ac-102">1026 - ScheduleTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="af8ac-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="af8ac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af8ac-104">ID</span><span class="sxs-lookup"><span data-stu-id="af8ac-104">ID</span></span>|<span data-ttu-id="af8ac-105">1026</span><span class="sxs-lookup"><span data-stu-id="af8ac-105">1026</span></span>|  
|<span data-ttu-id="af8ac-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="af8ac-106">Keywords</span></span>|<span data-ttu-id="af8ac-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af8ac-107">WFRuntime</span></span>|  
|<span data-ttu-id="af8ac-108">レベル</span><span class="sxs-lookup"><span data-stu-id="af8ac-108">Level</span></span>|<span data-ttu-id="af8ac-109">詳細</span><span class="sxs-lookup"><span data-stu-id="af8ac-109">Verbose</span></span>|  
|<span data-ttu-id="af8ac-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="af8ac-110">Channel</span></span>|<span data-ttu-id="af8ac-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="af8ac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af8ac-112">説明</span><span class="sxs-lookup"><span data-stu-id="af8ac-112">Description</span></span>  
 <span data-ttu-id="af8ac-113">TransactionContextWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="af8ac-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af8ac-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="af8ac-114">Message</span></span>  
 <span data-ttu-id="af8ac-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="af8ac-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af8ac-116">詳細</span><span class="sxs-lookup"><span data-stu-id="af8ac-116">Details</span></span>  
  
|<span data-ttu-id="af8ac-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="af8ac-117">Data Item Name</span></span>|<span data-ttu-id="af8ac-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="af8ac-118">Data Item Type</span></span>|<span data-ttu-id="af8ac-119">説明</span><span class="sxs-lookup"><span data-stu-id="af8ac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af8ac-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="af8ac-120">Activity</span></span>|<span data-ttu-id="af8ac-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="af8ac-121">xs:string</span></span>|<span data-ttu-id="af8ac-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="af8ac-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="af8ac-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="af8ac-123">DisplayName</span></span>|<span data-ttu-id="af8ac-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="af8ac-124">xs:string</span></span>|<span data-ttu-id="af8ac-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="af8ac-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="af8ac-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="af8ac-126">InstanceId</span></span>|<span data-ttu-id="af8ac-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="af8ac-127">xs:string</span></span>|<span data-ttu-id="af8ac-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="af8ac-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="af8ac-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="af8ac-129">AppDomain</span></span>|<span data-ttu-id="af8ac-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="af8ac-130">xs:string</span></span>|<span data-ttu-id="af8ac-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="af8ac-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
