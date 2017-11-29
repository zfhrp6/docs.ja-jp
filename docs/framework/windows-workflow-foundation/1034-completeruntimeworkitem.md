---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="6912e-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="6912e-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="6912e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6912e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6912e-104">ID</span><span class="sxs-lookup"><span data-stu-id="6912e-104">ID</span></span>|<span data-ttu-id="6912e-105">1034</span><span class="sxs-lookup"><span data-stu-id="6912e-105">1034</span></span>|  
|<span data-ttu-id="6912e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="6912e-106">Keywords</span></span>|<span data-ttu-id="6912e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6912e-107">WFRuntime</span></span>|  
|<span data-ttu-id="6912e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="6912e-108">Level</span></span>|<span data-ttu-id="6912e-109">詳細</span><span class="sxs-lookup"><span data-stu-id="6912e-109">Verbose</span></span>|  
|<span data-ttu-id="6912e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6912e-110">Channel</span></span>|<span data-ttu-id="6912e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="6912e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6912e-112">説明</span><span class="sxs-lookup"><span data-stu-id="6912e-112">Description</span></span>  
 <span data-ttu-id="6912e-113">RuntimeWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6912e-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6912e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6912e-114">Message</span></span>  
 <span data-ttu-id="6912e-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目が完了しました。</span><span class="sxs-lookup"><span data-stu-id="6912e-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6912e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="6912e-116">Details</span></span>  
  
|<span data-ttu-id="6912e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6912e-117">Data Item Name</span></span>|<span data-ttu-id="6912e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6912e-118">Data Item Type</span></span>|<span data-ttu-id="6912e-119">説明</span><span class="sxs-lookup"><span data-stu-id="6912e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6912e-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="6912e-120">Activity</span></span>|<span data-ttu-id="6912e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="6912e-121">xs:string</span></span>|<span data-ttu-id="6912e-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="6912e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="6912e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="6912e-123">DisplayName</span></span>|<span data-ttu-id="6912e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="6912e-124">xs:string</span></span>|<span data-ttu-id="6912e-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="6912e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="6912e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="6912e-126">InstanceId</span></span>|<span data-ttu-id="6912e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="6912e-127">xs:string</span></span>|<span data-ttu-id="6912e-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="6912e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="6912e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6912e-129">AppDomain</span></span>|<span data-ttu-id="6912e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="6912e-130">xs:string</span></span>|<span data-ttu-id="6912e-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6912e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
