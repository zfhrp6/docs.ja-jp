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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="7e648-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="7e648-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="7e648-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7e648-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e648-104">ID</span><span class="sxs-lookup"><span data-stu-id="7e648-104">ID</span></span>|<span data-ttu-id="7e648-105">1041</span><span class="sxs-lookup"><span data-stu-id="7e648-105">1041</span></span>|  
|<span data-ttu-id="7e648-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7e648-106">Keywords</span></span>|<span data-ttu-id="7e648-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7e648-107">WFRuntime</span></span>|  
|<span data-ttu-id="7e648-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7e648-108">Level</span></span>|<span data-ttu-id="7e648-109">情報</span><span class="sxs-lookup"><span data-stu-id="7e648-109">Information</span></span>|  
|<span data-ttu-id="7e648-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7e648-110">Channel</span></span>|<span data-ttu-id="7e648-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7e648-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7e648-112">説明</span><span class="sxs-lookup"><span data-stu-id="7e648-112">Description</span></span>  
 <span data-ttu-id="7e648-113">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="7e648-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="7e648-114">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="7e648-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7e648-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7e648-115">Message</span></span>  
 <span data-ttu-id="7e648-116">WorkflowApplication Id: '%1' には、アイドル状態のままです。</span><span class="sxs-lookup"><span data-stu-id="7e648-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="7e648-117">次の操作が実行されます: %n%n 2 です。</span><span class="sxs-lookup"><span data-stu-id="7e648-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7e648-118">詳細</span><span class="sxs-lookup"><span data-stu-id="7e648-118">Details</span></span>  
  
|<span data-ttu-id="7e648-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7e648-119">Data Item Name</span></span>|<span data-ttu-id="7e648-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7e648-120">Data Item Type</span></span>|<span data-ttu-id="7e648-121">説明</span><span class="sxs-lookup"><span data-stu-id="7e648-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7e648-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="7e648-122">WorkflowApplicationId</span></span>|<span data-ttu-id="7e648-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e648-123">xs:string</span></span>|<span data-ttu-id="7e648-124">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="7e648-124">The workflow application id</span></span>|  
|<span data-ttu-id="7e648-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="7e648-125">ActionTaken</span></span>|<span data-ttu-id="7e648-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e648-126">xs:string</span></span>|<span data-ttu-id="7e648-127">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="7e648-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="7e648-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e648-128">AppDomain</span></span>|<span data-ttu-id="7e648-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="7e648-129">xs:string</span></span>|<span data-ttu-id="7e648-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7e648-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
