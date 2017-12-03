---
title: 1001 - WorkflowApplicationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12b20ef893db12892636d73eeea2976f12bfccf9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="69e16-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="69e16-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="69e16-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="69e16-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69e16-104">ID</span><span class="sxs-lookup"><span data-stu-id="69e16-104">ID</span></span>|<span data-ttu-id="69e16-105">1001</span><span class="sxs-lookup"><span data-stu-id="69e16-105">1001</span></span>|  
|<span data-ttu-id="69e16-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="69e16-106">Keywords</span></span>|<span data-ttu-id="69e16-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="69e16-107">WFRuntime</span></span>|  
|<span data-ttu-id="69e16-108">レベル</span><span class="sxs-lookup"><span data-stu-id="69e16-108">Level</span></span>|<span data-ttu-id="69e16-109">情報</span><span class="sxs-lookup"><span data-stu-id="69e16-109">Information</span></span>|  
|<span data-ttu-id="69e16-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="69e16-110">Channel</span></span>|<span data-ttu-id="69e16-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="69e16-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69e16-112">説明</span><span class="sxs-lookup"><span data-stu-id="69e16-112">Description</span></span>  
 <span data-ttu-id="69e16-113">ワークフロー アプリケーションが Closed 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="69e16-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69e16-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="69e16-114">Message</span></span>  
 <span data-ttu-id="69e16-115">WorkflowInstance ID: %1 は Closed 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="69e16-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69e16-116">詳細</span><span class="sxs-lookup"><span data-stu-id="69e16-116">Details</span></span>  
  
|<span data-ttu-id="69e16-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="69e16-117">Data Item Name</span></span>|<span data-ttu-id="69e16-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="69e16-118">Data Item Type</span></span>|<span data-ttu-id="69e16-119">説明</span><span class="sxs-lookup"><span data-stu-id="69e16-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69e16-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="69e16-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="69e16-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="69e16-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="69e16-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="69e16-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="69e16-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="69e16-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
