---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="62315-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="62315-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="62315-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="62315-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62315-104">ID</span><span class="sxs-lookup"><span data-stu-id="62315-104">ID</span></span>|<span data-ttu-id="62315-105">1010</span><span class="sxs-lookup"><span data-stu-id="62315-105">1010</span></span>|  
|<span data-ttu-id="62315-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="62315-106">Keywords</span></span>|<span data-ttu-id="62315-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="62315-107">WFRuntime</span></span>|  
|<span data-ttu-id="62315-108">レベル</span><span class="sxs-lookup"><span data-stu-id="62315-108">Level</span></span>|<span data-ttu-id="62315-109">情報</span><span class="sxs-lookup"><span data-stu-id="62315-109">Information</span></span>|  
|<span data-ttu-id="62315-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="62315-110">Channel</span></span>|<span data-ttu-id="62315-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="62315-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62315-112">説明</span><span class="sxs-lookup"><span data-stu-id="62315-112">Description</span></span>  
 <span data-ttu-id="62315-113">アクティビティが実行を完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="62315-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="62315-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="62315-114">Message</span></span>  
 <span data-ttu-id="62315-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' が状態 '%4' で完了しました。</span><span class="sxs-lookup"><span data-stu-id="62315-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62315-116">詳細</span><span class="sxs-lookup"><span data-stu-id="62315-116">Details</span></span>  
  
|<span data-ttu-id="62315-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="62315-117">Data Item Name</span></span>|<span data-ttu-id="62315-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="62315-118">Data Item Type</span></span>|<span data-ttu-id="62315-119">説明</span><span class="sxs-lookup"><span data-stu-id="62315-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62315-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="62315-120">Activity</span></span>|<span data-ttu-id="62315-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="62315-121">xs:string</span></span>|<span data-ttu-id="62315-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="62315-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="62315-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="62315-123">DisplayName</span></span>|<span data-ttu-id="62315-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="62315-124">xs:string</span></span>|<span data-ttu-id="62315-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="62315-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="62315-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="62315-126">InstanceId</span></span>|<span data-ttu-id="62315-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="62315-127">xs:string</span></span>|<span data-ttu-id="62315-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="62315-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="62315-129">状態</span><span class="sxs-lookup"><span data-stu-id="62315-129">State</span></span>|<span data-ttu-id="62315-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="62315-130">xs:string</span></span>|<span data-ttu-id="62315-131">アクティビティの状態。</span><span class="sxs-lookup"><span data-stu-id="62315-131">The state of the activity.</span></span>|  
|<span data-ttu-id="62315-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="62315-132">AppDomain</span></span>|<span data-ttu-id="62315-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="62315-133">xs:string</span></span>|<span data-ttu-id="62315-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="62315-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
