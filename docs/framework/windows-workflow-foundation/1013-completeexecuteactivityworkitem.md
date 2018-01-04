---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dc72081d2e9b89a9979651bb02b6c06448e30e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="417ea-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="417ea-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="417ea-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="417ea-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="417ea-104">ID</span><span class="sxs-lookup"><span data-stu-id="417ea-104">ID</span></span>|<span data-ttu-id="417ea-105">1013</span><span class="sxs-lookup"><span data-stu-id="417ea-105">1013</span></span>|  
|<span data-ttu-id="417ea-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="417ea-106">Keywords</span></span>|<span data-ttu-id="417ea-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="417ea-107">WFRuntime</span></span>|  
|<span data-ttu-id="417ea-108">レベル</span><span class="sxs-lookup"><span data-stu-id="417ea-108">Level</span></span>|<span data-ttu-id="417ea-109">詳細</span><span class="sxs-lookup"><span data-stu-id="417ea-109">Verbose</span></span>|  
|<span data-ttu-id="417ea-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="417ea-110">Channel</span></span>|<span data-ttu-id="417ea-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="417ea-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="417ea-112">説明</span><span class="sxs-lookup"><span data-stu-id="417ea-112">Description</span></span>  
 <span data-ttu-id="417ea-113">ExecuteActivityWorkItem が完了したことを示します</span><span class="sxs-lookup"><span data-stu-id="417ea-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="417ea-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="417ea-114">Message</span></span>  
 <span data-ttu-id="417ea-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="417ea-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="417ea-116">詳細</span><span class="sxs-lookup"><span data-stu-id="417ea-116">Details</span></span>  
  
|<span data-ttu-id="417ea-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="417ea-117">Data Item Name</span></span>|<span data-ttu-id="417ea-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="417ea-118">Data Item Type</span></span>|<span data-ttu-id="417ea-119">説明</span><span class="sxs-lookup"><span data-stu-id="417ea-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="417ea-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="417ea-120">Activity</span></span>|<span data-ttu-id="417ea-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="417ea-121">xs:string</span></span>|<span data-ttu-id="417ea-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="417ea-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="417ea-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="417ea-123">DisplayName</span></span>|<span data-ttu-id="417ea-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="417ea-124">xs:string</span></span>|<span data-ttu-id="417ea-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="417ea-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="417ea-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="417ea-126">InstanceId</span></span>|<span data-ttu-id="417ea-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="417ea-127">xs:string</span></span>|<span data-ttu-id="417ea-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="417ea-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="417ea-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="417ea-129">AppDomain</span></span>|<span data-ttu-id="417ea-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="417ea-130">xs:string</span></span>|<span data-ttu-id="417ea-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="417ea-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
