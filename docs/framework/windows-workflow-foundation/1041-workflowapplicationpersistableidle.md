---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="0159c-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="0159c-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="0159c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0159c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0159c-104">ID</span><span class="sxs-lookup"><span data-stu-id="0159c-104">ID</span></span>|<span data-ttu-id="0159c-105">1041</span><span class="sxs-lookup"><span data-stu-id="0159c-105">1041</span></span>|  
|<span data-ttu-id="0159c-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="0159c-106">Keywords</span></span>|<span data-ttu-id="0159c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0159c-107">WFRuntime</span></span>|  
|<span data-ttu-id="0159c-108">レベル</span><span class="sxs-lookup"><span data-stu-id="0159c-108">Level</span></span>|<span data-ttu-id="0159c-109">情報</span><span class="sxs-lookup"><span data-stu-id="0159c-109">Information</span></span>|  
|<span data-ttu-id="0159c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0159c-110">Channel</span></span>|<span data-ttu-id="0159c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0159c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0159c-112">説明</span><span class="sxs-lookup"><span data-stu-id="0159c-112">Description</span></span>  
 <span data-ttu-id="0159c-113">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="0159c-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="0159c-114">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="0159c-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0159c-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="0159c-115">Message</span></span>  
 <span data-ttu-id="0159c-116">WorkflowApplication Id: '%1' には、アイドル状態のままです。</span><span class="sxs-lookup"><span data-stu-id="0159c-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="0159c-117">次の操作が実行されます: %n%n 2 です。</span><span class="sxs-lookup"><span data-stu-id="0159c-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0159c-118">詳細</span><span class="sxs-lookup"><span data-stu-id="0159c-118">Details</span></span>  
  
|<span data-ttu-id="0159c-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0159c-119">Data Item Name</span></span>|<span data-ttu-id="0159c-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0159c-120">Data Item Type</span></span>|<span data-ttu-id="0159c-121">説明</span><span class="sxs-lookup"><span data-stu-id="0159c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0159c-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="0159c-122">WorkflowApplicationId</span></span>|<span data-ttu-id="0159c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="0159c-123">xs:string</span></span>|<span data-ttu-id="0159c-124">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="0159c-124">The workflow application id</span></span>|  
|<span data-ttu-id="0159c-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="0159c-125">ActionTaken</span></span>|<span data-ttu-id="0159c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="0159c-126">xs:string</span></span>|<span data-ttu-id="0159c-127">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="0159c-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="0159c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0159c-128">AppDomain</span></span>|<span data-ttu-id="0159c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="0159c-129">xs:string</span></span>|<span data-ttu-id="0159c-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0159c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
