---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26491c1e2b20f4285aaedbcd12947cad3562f041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="e8832-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="e8832-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="e8832-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e8832-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e8832-104">ID</span><span class="sxs-lookup"><span data-stu-id="e8832-104">ID</span></span>|<span data-ttu-id="e8832-105">1008</span><span class="sxs-lookup"><span data-stu-id="e8832-105">1008</span></span>|  
|<span data-ttu-id="e8832-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="e8832-106">Keywords</span></span>|<span data-ttu-id="e8832-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e8832-107">WFRuntime</span></span>|  
|<span data-ttu-id="e8832-108">レベル</span><span class="sxs-lookup"><span data-stu-id="e8832-108">Level</span></span>|<span data-ttu-id="e8832-109">情報</span><span class="sxs-lookup"><span data-stu-id="e8832-109">Information</span></span>|  
|<span data-ttu-id="e8832-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e8832-110">Channel</span></span>|<span data-ttu-id="e8832-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e8832-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e8832-112">説明</span><span class="sxs-lookup"><span data-stu-id="e8832-112">Description</span></span>  
 <span data-ttu-id="e8832-113">ワークフロー アプリケーションがアンロードしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="e8832-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e8832-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="e8832-114">Message</span></span>  
 <span data-ttu-id="e8832-115">WorkflowInstance ID: '%1' がアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="e8832-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e8832-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e8832-116">Details</span></span>  
  
|<span data-ttu-id="e8832-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e8832-117">Data Item Name</span></span>|<span data-ttu-id="e8832-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e8832-118">Data Item Type</span></span>|<span data-ttu-id="e8832-119">説明</span><span class="sxs-lookup"><span data-stu-id="e8832-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e8832-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e8832-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e8832-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="e8832-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e8832-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e8832-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e8832-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e8832-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
