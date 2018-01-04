---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d64d18474ff867ee5679e07c18a288f07185f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="53758-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="53758-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="53758-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="53758-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53758-104">ID</span><span class="sxs-lookup"><span data-stu-id="53758-104">ID</span></span>|<span data-ttu-id="53758-105">1018</span><span class="sxs-lookup"><span data-stu-id="53758-105">1018</span></span>|  
|<span data-ttu-id="53758-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="53758-106">Keywords</span></span>|<span data-ttu-id="53758-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="53758-107">WFRuntime</span></span>|  
|<span data-ttu-id="53758-108">レベル</span><span class="sxs-lookup"><span data-stu-id="53758-108">Level</span></span>|<span data-ttu-id="53758-109">詳細</span><span class="sxs-lookup"><span data-stu-id="53758-109">Verbose</span></span>|  
|<span data-ttu-id="53758-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="53758-110">Channel</span></span>|<span data-ttu-id="53758-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="53758-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="53758-112">説明</span><span class="sxs-lookup"><span data-stu-id="53758-112">Description</span></span>  
 <span data-ttu-id="53758-113">CancelActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="53758-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="53758-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="53758-114">Message</span></span>  
 <span data-ttu-id="53758-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="53758-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="53758-116">詳細</span><span class="sxs-lookup"><span data-stu-id="53758-116">Details</span></span>  
  
|<span data-ttu-id="53758-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="53758-117">Data Item Name</span></span>|<span data-ttu-id="53758-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="53758-118">Data Item Type</span></span>|<span data-ttu-id="53758-119">説明</span><span class="sxs-lookup"><span data-stu-id="53758-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="53758-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="53758-120">Activity</span></span>|<span data-ttu-id="53758-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="53758-121">xs:string</span></span>|<span data-ttu-id="53758-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="53758-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="53758-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="53758-123">DisplayName</span></span>|<span data-ttu-id="53758-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="53758-124">xs:string</span></span>|<span data-ttu-id="53758-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="53758-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="53758-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="53758-126">InstanceId</span></span>|<span data-ttu-id="53758-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="53758-127">xs:string</span></span>|<span data-ttu-id="53758-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="53758-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="53758-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="53758-129">AppDomain</span></span>|<span data-ttu-id="53758-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="53758-130">xs:string</span></span>|<span data-ttu-id="53758-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="53758-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
