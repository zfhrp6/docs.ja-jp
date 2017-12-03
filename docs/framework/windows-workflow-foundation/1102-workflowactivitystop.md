---
title: 1102 - WorkflowActivityStop
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e6f70af8df131767dd528774f9098f30e7223d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1102---workflowactivitystop"></a><span data-ttu-id="8b9b1-102">1102 - WorkflowActivityStop</span><span class="sxs-lookup"><span data-stu-id="8b9b1-102">1102 - WorkflowActivityStop</span></span>
## <a name="properties"></a><span data-ttu-id="8b9b1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8b9b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b9b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="8b9b1-104">ID</span></span>|<span data-ttu-id="8b9b1-105">1102</span><span class="sxs-lookup"><span data-stu-id="8b9b1-105">1102</span></span>|  
|<span data-ttu-id="8b9b1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8b9b1-106">Keywords</span></span>|<span data-ttu-id="8b9b1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8b9b1-107">WFRuntime</span></span>|  
|<span data-ttu-id="8b9b1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8b9b1-108">Level</span></span>|<span data-ttu-id="8b9b1-109">情報</span><span class="sxs-lookup"><span data-stu-id="8b9b1-109">Information</span></span>|  
|<span data-ttu-id="8b9b1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8b9b1-110">Channel</span></span>|<span data-ttu-id="8b9b1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8b9b1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b9b1-112">説明</span><span class="sxs-lookup"><span data-stu-id="8b9b1-112">Description</span></span>  
 <span data-ttu-id="8b9b1-113">ワークフロー アクティビティが中止されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="8b9b1-113">Indicates a workflow activity has stopped.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b9b1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8b9b1-114">Message</span></span>  
 <span data-ttu-id="8b9b1-115">WorkflowInstance ID: '%1' E2E アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8b9b1-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b9b1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8b9b1-116">Details</span></span>  
  
|<span data-ttu-id="8b9b1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8b9b1-117">Data Item Name</span></span>|<span data-ttu-id="8b9b1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8b9b1-118">Data Item Type</span></span>|<span data-ttu-id="8b9b1-119">説明</span><span class="sxs-lookup"><span data-stu-id="8b9b1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b9b1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="8b9b1-120">WorkflowInstanceId</span></span>|<span data-ttu-id="8b9b1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b9b1-121">xs:string</span></span>|<span data-ttu-id="8b9b1-122">ワークフロー インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8b9b1-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="8b9b1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b9b1-123">AppDomain</span></span>|<span data-ttu-id="8b9b1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8b9b1-124">xs:string</span></span>|<span data-ttu-id="8b9b1-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8b9b1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
