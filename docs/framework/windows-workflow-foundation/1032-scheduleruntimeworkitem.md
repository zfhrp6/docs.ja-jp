---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: 505b852d54e256b2c2bfff8d90944dd4e993e0c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510248"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="026df-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="026df-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="026df-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="026df-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="026df-104">ID</span><span class="sxs-lookup"><span data-stu-id="026df-104">ID</span></span>|<span data-ttu-id="026df-105">1032</span><span class="sxs-lookup"><span data-stu-id="026df-105">1032</span></span>|  
|<span data-ttu-id="026df-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="026df-106">Keywords</span></span>|<span data-ttu-id="026df-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="026df-107">WFRuntime</span></span>|  
|<span data-ttu-id="026df-108">レベル</span><span class="sxs-lookup"><span data-stu-id="026df-108">Level</span></span>|<span data-ttu-id="026df-109">詳細</span><span class="sxs-lookup"><span data-stu-id="026df-109">Verbose</span></span>|  
|<span data-ttu-id="026df-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="026df-110">Channel</span></span>|<span data-ttu-id="026df-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="026df-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="026df-112">説明</span><span class="sxs-lookup"><span data-stu-id="026df-112">Description</span></span>  
 <span data-ttu-id="026df-113">RuntimeWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="026df-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="026df-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="026df-114">Message</span></span>  
 <span data-ttu-id="026df-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="026df-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="026df-116">詳細</span><span class="sxs-lookup"><span data-stu-id="026df-116">Details</span></span>  
  
|<span data-ttu-id="026df-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="026df-117">Data Item Name</span></span>|<span data-ttu-id="026df-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="026df-118">Data Item Type</span></span>|<span data-ttu-id="026df-119">説明</span><span class="sxs-lookup"><span data-stu-id="026df-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="026df-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="026df-120">Activity</span></span>|<span data-ttu-id="026df-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="026df-121">xs:string</span></span>|<span data-ttu-id="026df-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="026df-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="026df-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="026df-123">DisplayName</span></span>|<span data-ttu-id="026df-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="026df-124">xs:string</span></span>|<span data-ttu-id="026df-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="026df-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="026df-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="026df-126">InstanceId</span></span>|<span data-ttu-id="026df-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="026df-127">xs:string</span></span>|<span data-ttu-id="026df-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="026df-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="026df-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="026df-129">AppDomain</span></span>|<span data-ttu-id="026df-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="026df-130">xs:string</span></span>|<span data-ttu-id="026df-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="026df-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
