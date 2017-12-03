---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6930aeed8c3cd224d5d37dcecf357195e78390ed
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="b3999-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="b3999-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="b3999-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b3999-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3999-104">ID</span><span class="sxs-lookup"><span data-stu-id="b3999-104">ID</span></span>|<span data-ttu-id="b3999-105">1003</span><span class="sxs-lookup"><span data-stu-id="b3999-105">1003</span></span>|  
|<span data-ttu-id="b3999-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b3999-106">Keywords</span></span>|<span data-ttu-id="b3999-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b3999-107">WFRuntime</span></span>|  
|<span data-ttu-id="b3999-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b3999-108">Level</span></span>|<span data-ttu-id="b3999-109">情報</span><span class="sxs-lookup"><span data-stu-id="b3999-109">Information</span></span>|  
|<span data-ttu-id="b3999-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b3999-110">Channel</span></span>|<span data-ttu-id="b3999-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b3999-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3999-112">説明</span><span class="sxs-lookup"><span data-stu-id="b3999-112">Description</span></span>  
 <span data-ttu-id="b3999-113">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b3999-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3999-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b3999-114">Message</span></span>  
 <span data-ttu-id="b3999-115">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="b3999-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3999-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b3999-116">Details</span></span>  
  
|<span data-ttu-id="b3999-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b3999-117">Data Item Name</span></span>|<span data-ttu-id="b3999-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b3999-118">Data Item Type</span></span>|<span data-ttu-id="b3999-119">説明</span><span class="sxs-lookup"><span data-stu-id="b3999-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3999-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b3999-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b3999-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="b3999-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b3999-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b3999-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b3999-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b3999-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
