---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a632d59ddd75b375ff5e828a9f35aeecb0118f1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="4cd36-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4cd36-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4cd36-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4cd36-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4cd36-104">ID</span><span class="sxs-lookup"><span data-stu-id="4cd36-104">ID</span></span>|<span data-ttu-id="4cd36-105">1017</span><span class="sxs-lookup"><span data-stu-id="4cd36-105">1017</span></span>|  
|<span data-ttu-id="4cd36-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="4cd36-106">Keywords</span></span>|<span data-ttu-id="4cd36-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4cd36-107">WFRuntime</span></span>|  
|<span data-ttu-id="4cd36-108">レベル</span><span class="sxs-lookup"><span data-stu-id="4cd36-108">Level</span></span>|<span data-ttu-id="4cd36-109">詳細</span><span class="sxs-lookup"><span data-stu-id="4cd36-109">Verbose</span></span>|  
|<span data-ttu-id="4cd36-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4cd36-110">Channel</span></span>|<span data-ttu-id="4cd36-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4cd36-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4cd36-112">説明</span><span class="sxs-lookup"><span data-stu-id="4cd36-112">Description</span></span>  
 <span data-ttu-id="4cd36-113">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4cd36-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4cd36-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="4cd36-114">Message</span></span>  
 <span data-ttu-id="4cd36-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="4cd36-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4cd36-116">詳細</span><span class="sxs-lookup"><span data-stu-id="4cd36-116">Details</span></span>  
  
|<span data-ttu-id="4cd36-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4cd36-117">Data Item Name</span></span>|<span data-ttu-id="4cd36-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4cd36-118">Data Item Type</span></span>|<span data-ttu-id="4cd36-119">説明</span><span class="sxs-lookup"><span data-stu-id="4cd36-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4cd36-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="4cd36-120">Activity</span></span>|<span data-ttu-id="4cd36-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd36-121">xs:string</span></span>|<span data-ttu-id="4cd36-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4cd36-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4cd36-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4cd36-123">DisplayName</span></span>|<span data-ttu-id="4cd36-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd36-124">xs:string</span></span>|<span data-ttu-id="4cd36-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4cd36-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4cd36-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4cd36-126">InstanceId</span></span>|<span data-ttu-id="4cd36-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd36-127">xs:string</span></span>|<span data-ttu-id="4cd36-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4cd36-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4cd36-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4cd36-129">AppDomain</span></span>|<span data-ttu-id="4cd36-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd36-130">xs:string</span></span>|<span data-ttu-id="4cd36-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4cd36-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
