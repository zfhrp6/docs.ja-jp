---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="3af7f-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="3af7f-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3af7f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3af7f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3af7f-104">ID</span><span class="sxs-lookup"><span data-stu-id="3af7f-104">ID</span></span>|<span data-ttu-id="3af7f-105">1033</span><span class="sxs-lookup"><span data-stu-id="3af7f-105">1033</span></span>|  
|<span data-ttu-id="3af7f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="3af7f-106">Keywords</span></span>|<span data-ttu-id="3af7f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3af7f-107">WFRuntime</span></span>|  
|<span data-ttu-id="3af7f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="3af7f-108">Level</span></span>|<span data-ttu-id="3af7f-109">詳細</span><span class="sxs-lookup"><span data-stu-id="3af7f-109">Verbose</span></span>|  
|<span data-ttu-id="3af7f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3af7f-110">Channel</span></span>|<span data-ttu-id="3af7f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3af7f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3af7f-112">説明</span><span class="sxs-lookup"><span data-stu-id="3af7f-112">Description</span></span>  
 <span data-ttu-id="3af7f-113">RuntimeWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="3af7f-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3af7f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="3af7f-114">Message</span></span>  
 <span data-ttu-id="3af7f-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="3af7f-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3af7f-116">詳細</span><span class="sxs-lookup"><span data-stu-id="3af7f-116">Details</span></span>  
  
|<span data-ttu-id="3af7f-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3af7f-117">Data Item Name</span></span>|<span data-ttu-id="3af7f-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3af7f-118">Data Item Type</span></span>|<span data-ttu-id="3af7f-119">説明</span><span class="sxs-lookup"><span data-stu-id="3af7f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3af7f-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3af7f-120">Activity</span></span>|<span data-ttu-id="3af7f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3af7f-121">xs:string</span></span>|<span data-ttu-id="3af7f-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3af7f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3af7f-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3af7f-123">DisplayName</span></span>|<span data-ttu-id="3af7f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3af7f-124">xs:string</span></span>|<span data-ttu-id="3af7f-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3af7f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3af7f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3af7f-126">InstanceId</span></span>|<span data-ttu-id="3af7f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3af7f-127">xs:string</span></span>|<span data-ttu-id="3af7f-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3af7f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3af7f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3af7f-129">AppDomain</span></span>|<span data-ttu-id="3af7f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3af7f-130">xs:string</span></span>|<span data-ttu-id="3af7f-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3af7f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
