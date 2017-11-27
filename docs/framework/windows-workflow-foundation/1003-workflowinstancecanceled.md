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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b287c99453724f855a51e9a1b8068337dd5e373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="48a16-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="48a16-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="48a16-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="48a16-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48a16-104">ID</span><span class="sxs-lookup"><span data-stu-id="48a16-104">ID</span></span>|<span data-ttu-id="48a16-105">1003</span><span class="sxs-lookup"><span data-stu-id="48a16-105">1003</span></span>|  
|<span data-ttu-id="48a16-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="48a16-106">Keywords</span></span>|<span data-ttu-id="48a16-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="48a16-107">WFRuntime</span></span>|  
|<span data-ttu-id="48a16-108">レベル</span><span class="sxs-lookup"><span data-stu-id="48a16-108">Level</span></span>|<span data-ttu-id="48a16-109">情報</span><span class="sxs-lookup"><span data-stu-id="48a16-109">Information</span></span>|  
|<span data-ttu-id="48a16-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="48a16-110">Channel</span></span>|<span data-ttu-id="48a16-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="48a16-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="48a16-112">説明</span><span class="sxs-lookup"><span data-stu-id="48a16-112">Description</span></span>  
 <span data-ttu-id="48a16-113">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="48a16-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="48a16-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="48a16-114">Message</span></span>  
 <span data-ttu-id="48a16-115">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="48a16-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="48a16-116">詳細</span><span class="sxs-lookup"><span data-stu-id="48a16-116">Details</span></span>  
  
|<span data-ttu-id="48a16-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="48a16-117">Data Item Name</span></span>|<span data-ttu-id="48a16-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="48a16-118">Data Item Type</span></span>|<span data-ttu-id="48a16-119">説明</span><span class="sxs-lookup"><span data-stu-id="48a16-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="48a16-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="48a16-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="48a16-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="48a16-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="48a16-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="48a16-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="48a16-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="48a16-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
