---
title: 1103 - WorkflowActivitySuspend
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a55cd953b294ca5e8a90f6ade666c55b51dc1e58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1103---workflowactivitysuspend"></a><span data-ttu-id="b371a-102">1103 - WorkflowActivitySuspend</span><span class="sxs-lookup"><span data-stu-id="b371a-102">1103 - WorkflowActivitySuspend</span></span>
## <a name="properties"></a><span data-ttu-id="b371a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b371a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b371a-104">ID</span><span class="sxs-lookup"><span data-stu-id="b371a-104">ID</span></span>|<span data-ttu-id="b371a-105">1103</span><span class="sxs-lookup"><span data-stu-id="b371a-105">1103</span></span>|  
|<span data-ttu-id="b371a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b371a-106">Keywords</span></span>|<span data-ttu-id="b371a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b371a-107">WFRuntime</span></span>|  
|<span data-ttu-id="b371a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b371a-108">Level</span></span>|<span data-ttu-id="b371a-109">情報</span><span class="sxs-lookup"><span data-stu-id="b371a-109">Information</span></span>|  
|<span data-ttu-id="b371a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b371a-110">Channel</span></span>|<span data-ttu-id="b371a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b371a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b371a-112">説明</span><span class="sxs-lookup"><span data-stu-id="b371a-112">Description</span></span>  
 <span data-ttu-id="b371a-113">ワークフロー アクティビティが中断されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="b371a-113">Indicates a workflow activity has been suspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b371a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b371a-114">Message</span></span>  
 <span data-ttu-id="b371a-115">WorkflowInstance ID: '%1' E2E アクティビティ</span><span class="sxs-lookup"><span data-stu-id="b371a-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="b371a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b371a-116">Details</span></span>  
  
|<span data-ttu-id="b371a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b371a-117">Data Item Name</span></span>|<span data-ttu-id="b371a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b371a-118">Data Item Type</span></span>|<span data-ttu-id="b371a-119">説明</span><span class="sxs-lookup"><span data-stu-id="b371a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b371a-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b371a-120">WorkflowInstanceId</span></span>|<span data-ttu-id="b371a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b371a-121">xs:string</span></span>|<span data-ttu-id="b371a-122">ワークフロー インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="b371a-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="b371a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b371a-123">AppDomain</span></span>|<span data-ttu-id="b371a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b371a-124">xs:string</span></span>|<span data-ttu-id="b371a-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b371a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
