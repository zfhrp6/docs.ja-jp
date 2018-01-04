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
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="7ce77-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="7ce77-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="7ce77-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7ce77-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ce77-104">ID</span><span class="sxs-lookup"><span data-stu-id="7ce77-104">ID</span></span>|<span data-ttu-id="7ce77-105">1003</span><span class="sxs-lookup"><span data-stu-id="7ce77-105">1003</span></span>|  
|<span data-ttu-id="7ce77-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7ce77-106">Keywords</span></span>|<span data-ttu-id="7ce77-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7ce77-107">WFRuntime</span></span>|  
|<span data-ttu-id="7ce77-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7ce77-108">Level</span></span>|<span data-ttu-id="7ce77-109">情報</span><span class="sxs-lookup"><span data-stu-id="7ce77-109">Information</span></span>|  
|<span data-ttu-id="7ce77-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7ce77-110">Channel</span></span>|<span data-ttu-id="7ce77-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7ce77-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7ce77-112">説明</span><span class="sxs-lookup"><span data-stu-id="7ce77-112">Description</span></span>  
 <span data-ttu-id="7ce77-113">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7ce77-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7ce77-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7ce77-114">Message</span></span>  
 <span data-ttu-id="7ce77-115">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="7ce77-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7ce77-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7ce77-116">Details</span></span>  
  
|<span data-ttu-id="7ce77-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7ce77-117">Data Item Name</span></span>|<span data-ttu-id="7ce77-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7ce77-118">Data Item Type</span></span>|<span data-ttu-id="7ce77-119">説明</span><span class="sxs-lookup"><span data-stu-id="7ce77-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7ce77-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7ce77-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="7ce77-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="7ce77-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="7ce77-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7ce77-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7ce77-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7ce77-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
