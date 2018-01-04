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
ms.workload: dotnet
ms.openlocfilehash: 1efc32ed0304d5b0d222054e5c65abe279ef93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="3eef1-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="3eef1-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="3eef1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3eef1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3eef1-104">ID</span><span class="sxs-lookup"><span data-stu-id="3eef1-104">ID</span></span>|<span data-ttu-id="3eef1-105">1041</span><span class="sxs-lookup"><span data-stu-id="3eef1-105">1041</span></span>|  
|<span data-ttu-id="3eef1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="3eef1-106">Keywords</span></span>|<span data-ttu-id="3eef1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3eef1-107">WFRuntime</span></span>|  
|<span data-ttu-id="3eef1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="3eef1-108">Level</span></span>|<span data-ttu-id="3eef1-109">情報</span><span class="sxs-lookup"><span data-stu-id="3eef1-109">Information</span></span>|  
|<span data-ttu-id="3eef1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3eef1-110">Channel</span></span>|<span data-ttu-id="3eef1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3eef1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3eef1-112">説明</span><span class="sxs-lookup"><span data-stu-id="3eef1-112">Description</span></span>  
 <span data-ttu-id="3eef1-113">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="3eef1-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="3eef1-114">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="3eef1-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3eef1-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="3eef1-115">Message</span></span>  
 <span data-ttu-id="3eef1-116">WorkflowApplication Id: '%1' には、アイドル状態のままです。</span><span class="sxs-lookup"><span data-stu-id="3eef1-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="3eef1-117">次の操作が実行されます: %n%n 2 です。</span><span class="sxs-lookup"><span data-stu-id="3eef1-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3eef1-118">説明</span><span class="sxs-lookup"><span data-stu-id="3eef1-118">Details</span></span>  
  
|<span data-ttu-id="3eef1-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3eef1-119">Data Item Name</span></span>|<span data-ttu-id="3eef1-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3eef1-120">Data Item Type</span></span>|<span data-ttu-id="3eef1-121">説明</span><span class="sxs-lookup"><span data-stu-id="3eef1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3eef1-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="3eef1-122">WorkflowApplicationId</span></span>|<span data-ttu-id="3eef1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="3eef1-123">xs:string</span></span>|<span data-ttu-id="3eef1-124">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="3eef1-124">The workflow application id</span></span>|  
|<span data-ttu-id="3eef1-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="3eef1-125">ActionTaken</span></span>|<span data-ttu-id="3eef1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="3eef1-126">xs:string</span></span>|<span data-ttu-id="3eef1-127">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="3eef1-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="3eef1-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3eef1-128">AppDomain</span></span>|<span data-ttu-id="3eef1-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="3eef1-129">xs:string</span></span>|<span data-ttu-id="3eef1-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3eef1-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
