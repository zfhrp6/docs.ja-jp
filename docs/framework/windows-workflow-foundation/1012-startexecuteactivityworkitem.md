---
title: 1012 - StartExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a3b03e8ac24bc1652b88b71e8c25862a07c194f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="7f427-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7f427-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7f427-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7f427-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f427-104">ID</span><span class="sxs-lookup"><span data-stu-id="7f427-104">ID</span></span>|<span data-ttu-id="7f427-105">1012</span><span class="sxs-lookup"><span data-stu-id="7f427-105">1012</span></span>|  
|<span data-ttu-id="7f427-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7f427-106">Keywords</span></span>|<span data-ttu-id="7f427-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7f427-107">WFRuntime</span></span>|  
|<span data-ttu-id="7f427-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7f427-108">Level</span></span>|<span data-ttu-id="7f427-109">詳細</span><span class="sxs-lookup"><span data-stu-id="7f427-109">Verbose</span></span>|  
|<span data-ttu-id="7f427-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7f427-110">Channel</span></span>|<span data-ttu-id="7f427-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7f427-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7f427-112">説明</span><span class="sxs-lookup"><span data-stu-id="7f427-112">Description</span></span>  
 <span data-ttu-id="7f427-113">ExecuteActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="7f427-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7f427-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7f427-114">Message</span></span>  
 <span data-ttu-id="7f427-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="7f427-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7f427-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7f427-116">Details</span></span>  
  
|<span data-ttu-id="7f427-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7f427-117">Data Item Name</span></span>|<span data-ttu-id="7f427-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7f427-118">Data Item Type</span></span>|<span data-ttu-id="7f427-119">説明</span><span class="sxs-lookup"><span data-stu-id="7f427-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7f427-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="7f427-120">Activity</span></span>|<span data-ttu-id="7f427-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f427-121">xs:string</span></span>|<span data-ttu-id="7f427-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="7f427-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7f427-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="7f427-123">DisplayName</span></span>|<span data-ttu-id="7f427-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f427-124">xs:string</span></span>|<span data-ttu-id="7f427-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="7f427-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7f427-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7f427-126">InstanceId</span></span>|<span data-ttu-id="7f427-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f427-127">xs:string</span></span>|<span data-ttu-id="7f427-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="7f427-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7f427-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7f427-129">AppDomain</span></span>|<span data-ttu-id="7f427-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="7f427-130">xs:string</span></span>|<span data-ttu-id="7f427-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7f427-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
