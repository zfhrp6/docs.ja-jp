---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509617"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="22047-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="22047-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="22047-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="22047-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22047-104">ID</span><span class="sxs-lookup"><span data-stu-id="22047-104">ID</span></span>|<span data-ttu-id="22047-105">1011</span><span class="sxs-lookup"><span data-stu-id="22047-105">1011</span></span>|  
|<span data-ttu-id="22047-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="22047-106">Keywords</span></span>|<span data-ttu-id="22047-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="22047-107">WFRuntime</span></span>|  
|<span data-ttu-id="22047-108">レベル</span><span class="sxs-lookup"><span data-stu-id="22047-108">Level</span></span>|<span data-ttu-id="22047-109">詳細</span><span class="sxs-lookup"><span data-stu-id="22047-109">Verbose</span></span>|  
|<span data-ttu-id="22047-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="22047-110">Channel</span></span>|<span data-ttu-id="22047-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="22047-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="22047-112">説明</span><span class="sxs-lookup"><span data-stu-id="22047-112">Description</span></span>  
 <span data-ttu-id="22047-113">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="22047-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="22047-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="22047-114">Message</span></span>  
 <span data-ttu-id="22047-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="22047-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="22047-116">詳細</span><span class="sxs-lookup"><span data-stu-id="22047-116">Details</span></span>  
  
|<span data-ttu-id="22047-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="22047-117">Data Item Name</span></span>|<span data-ttu-id="22047-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="22047-118">Data Item Type</span></span>|<span data-ttu-id="22047-119">説明</span><span class="sxs-lookup"><span data-stu-id="22047-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="22047-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="22047-120">Activity</span></span>|<span data-ttu-id="22047-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="22047-121">xs:string</span></span>|<span data-ttu-id="22047-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="22047-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="22047-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="22047-123">DisplayName</span></span>|<span data-ttu-id="22047-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="22047-124">xs:string</span></span>|<span data-ttu-id="22047-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="22047-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="22047-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="22047-126">InstanceId</span></span>|<span data-ttu-id="22047-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="22047-127">xs:string</span></span>|<span data-ttu-id="22047-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="22047-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="22047-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="22047-129">AppDomain</span></span>|<span data-ttu-id="22047-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="22047-130">xs:string</span></span>|<span data-ttu-id="22047-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="22047-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
