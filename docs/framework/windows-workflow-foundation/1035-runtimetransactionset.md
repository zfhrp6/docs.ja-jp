---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510035"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="884bd-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="884bd-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="884bd-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="884bd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="884bd-104">ID</span><span class="sxs-lookup"><span data-stu-id="884bd-104">ID</span></span>|<span data-ttu-id="884bd-105">1035</span><span class="sxs-lookup"><span data-stu-id="884bd-105">1035</span></span>|  
|<span data-ttu-id="884bd-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="884bd-106">Keywords</span></span>|<span data-ttu-id="884bd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="884bd-107">WFRuntime</span></span>|  
|<span data-ttu-id="884bd-108">レベル</span><span class="sxs-lookup"><span data-stu-id="884bd-108">Level</span></span>|<span data-ttu-id="884bd-109">詳細</span><span class="sxs-lookup"><span data-stu-id="884bd-109">Verbose</span></span>|  
|<span data-ttu-id="884bd-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="884bd-110">Channel</span></span>|<span data-ttu-id="884bd-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="884bd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="884bd-112">説明</span><span class="sxs-lookup"><span data-stu-id="884bd-112">Description</span></span>  
 <span data-ttu-id="884bd-113">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="884bd-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="884bd-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="884bd-114">Message</span></span>  
 <span data-ttu-id="884bd-115">Activity '%1'、DisplayName によってランタイム トランザクションが設定されました: '%2'、InstanceId: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="884bd-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="884bd-116">実行の分離 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' です。</span><span class="sxs-lookup"><span data-stu-id="884bd-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="884bd-117">説明</span><span class="sxs-lookup"><span data-stu-id="884bd-117">Details</span></span>  
  
|<span data-ttu-id="884bd-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="884bd-118">Data Item Name</span></span>|<span data-ttu-id="884bd-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="884bd-119">Data Item Type</span></span>|<span data-ttu-id="884bd-120">説明</span><span class="sxs-lookup"><span data-stu-id="884bd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="884bd-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="884bd-121">Activity</span></span>|<span data-ttu-id="884bd-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-122">xs:string</span></span>|<span data-ttu-id="884bd-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="884bd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="884bd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="884bd-124">DisplayName</span></span>|<span data-ttu-id="884bd-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-125">xs:string</span></span>|<span data-ttu-id="884bd-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="884bd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="884bd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="884bd-127">InstanceId</span></span>|<span data-ttu-id="884bd-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-128">xs:string</span></span>|<span data-ttu-id="884bd-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="884bd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="884bd-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="884bd-130">IsolatedActivity</span></span>|<span data-ttu-id="884bd-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-131">xs:string</span></span>|<span data-ttu-id="884bd-132">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="884bd-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="884bd-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="884bd-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="884bd-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-134">xs:string</span></span>|<span data-ttu-id="884bd-135">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="884bd-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="884bd-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="884bd-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="884bd-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-137">xs:string</span></span>|<span data-ttu-id="884bd-138">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="884bd-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="884bd-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="884bd-139">AppDomain</span></span>|<span data-ttu-id="884bd-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="884bd-140">xs:string</span></span>|<span data-ttu-id="884bd-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="884bd-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
