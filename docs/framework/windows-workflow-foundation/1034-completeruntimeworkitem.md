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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 743b16232e239929f75e269faa16799a37043495
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="795c9-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="795c9-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="795c9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="795c9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="795c9-104">ID</span><span class="sxs-lookup"><span data-stu-id="795c9-104">ID</span></span>|<span data-ttu-id="795c9-105">1034</span><span class="sxs-lookup"><span data-stu-id="795c9-105">1034</span></span>|  
|<span data-ttu-id="795c9-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="795c9-106">Keywords</span></span>|<span data-ttu-id="795c9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="795c9-107">WFRuntime</span></span>|  
|<span data-ttu-id="795c9-108">レベル</span><span class="sxs-lookup"><span data-stu-id="795c9-108">Level</span></span>|<span data-ttu-id="795c9-109">詳細</span><span class="sxs-lookup"><span data-stu-id="795c9-109">Verbose</span></span>|  
|<span data-ttu-id="795c9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="795c9-110">Channel</span></span>|<span data-ttu-id="795c9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="795c9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="795c9-112">説明</span><span class="sxs-lookup"><span data-stu-id="795c9-112">Description</span></span>  
 <span data-ttu-id="795c9-113">RuntimeWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="795c9-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="795c9-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="795c9-114">Message</span></span>  
 <span data-ttu-id="795c9-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目が完了しました。</span><span class="sxs-lookup"><span data-stu-id="795c9-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="795c9-116">詳細</span><span class="sxs-lookup"><span data-stu-id="795c9-116">Details</span></span>  
  
|<span data-ttu-id="795c9-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="795c9-117">Data Item Name</span></span>|<span data-ttu-id="795c9-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="795c9-118">Data Item Type</span></span>|<span data-ttu-id="795c9-119">説明</span><span class="sxs-lookup"><span data-stu-id="795c9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="795c9-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="795c9-120">Activity</span></span>|<span data-ttu-id="795c9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="795c9-121">xs:string</span></span>|<span data-ttu-id="795c9-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="795c9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="795c9-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="795c9-123">DisplayName</span></span>|<span data-ttu-id="795c9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="795c9-124">xs:string</span></span>|<span data-ttu-id="795c9-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="795c9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="795c9-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="795c9-126">InstanceId</span></span>|<span data-ttu-id="795c9-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="795c9-127">xs:string</span></span>|<span data-ttu-id="795c9-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="795c9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="795c9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="795c9-129">AppDomain</span></span>|<span data-ttu-id="795c9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="795c9-130">xs:string</span></span>|<span data-ttu-id="795c9-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="795c9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
