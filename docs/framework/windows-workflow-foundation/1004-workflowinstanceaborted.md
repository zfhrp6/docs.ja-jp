---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="692a1-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="692a1-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="692a1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="692a1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="692a1-104">ID</span><span class="sxs-lookup"><span data-stu-id="692a1-104">ID</span></span>|<span data-ttu-id="692a1-105">1004</span><span class="sxs-lookup"><span data-stu-id="692a1-105">1004</span></span>|  
|<span data-ttu-id="692a1-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="692a1-106">Keywords</span></span>|<span data-ttu-id="692a1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="692a1-107">WFRuntime</span></span>|  
|<span data-ttu-id="692a1-108">レベル</span><span class="sxs-lookup"><span data-stu-id="692a1-108">Level</span></span>|<span data-ttu-id="692a1-109">情報</span><span class="sxs-lookup"><span data-stu-id="692a1-109">Information</span></span>|  
|<span data-ttu-id="692a1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="692a1-110">Channel</span></span>|<span data-ttu-id="692a1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="692a1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="692a1-112">説明</span><span class="sxs-lookup"><span data-stu-id="692a1-112">Description</span></span>  
 <span data-ttu-id="692a1-113">ワークフロー インスタンスが例外で中断されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="692a1-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="692a1-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="692a1-114">Message</span></span>  
 <span data-ttu-id="692a1-115">WorkflowInstance ID: '%1' は例外により中止されました。</span><span class="sxs-lookup"><span data-stu-id="692a1-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="692a1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="692a1-116">Details</span></span>  
  
|<span data-ttu-id="692a1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="692a1-117">Data Item Name</span></span>|<span data-ttu-id="692a1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="692a1-118">Data Item Type</span></span>|<span data-ttu-id="692a1-119">説明</span><span class="sxs-lookup"><span data-stu-id="692a1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="692a1-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="692a1-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="692a1-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="692a1-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="692a1-122">例外</span><span class="sxs-lookup"><span data-stu-id="692a1-122">Exception</span></span>|`xs:string`|<span data-ttu-id="692a1-123">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="692a1-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="692a1-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="692a1-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="692a1-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="692a1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
