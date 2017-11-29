---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a03809be5e5d61c505e295e2f769a0298f770f7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="14a6a-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="14a6a-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="14a6a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="14a6a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14a6a-104">ID</span><span class="sxs-lookup"><span data-stu-id="14a6a-104">ID</span></span>|<span data-ttu-id="14a6a-105">1006</span><span class="sxs-lookup"><span data-stu-id="14a6a-105">1006</span></span>|  
|<span data-ttu-id="14a6a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="14a6a-106">Keywords</span></span>|<span data-ttu-id="14a6a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="14a6a-107">WFRuntime</span></span>|  
|<span data-ttu-id="14a6a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="14a6a-108">Level</span></span>|<span data-ttu-id="14a6a-109">Error</span><span class="sxs-lookup"><span data-stu-id="14a6a-109">Error</span></span>|  
|<span data-ttu-id="14a6a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="14a6a-110">Channel</span></span>|<span data-ttu-id="14a6a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="14a6a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14a6a-112">説明</span><span class="sxs-lookup"><span data-stu-id="14a6a-112">Description</span></span>  
 <span data-ttu-id="14a6a-113">ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="14a6a-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14a6a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="14a6a-114">Message</span></span>  
 <span data-ttu-id="14a6a-115">WorkflowInstance Id: '%1' はハンドルされない例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="14a6a-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="14a6a-116">例外の発生元 Activity '%2'、DisplayName: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="14a6a-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="14a6a-117">次の操作が実行されます: %n%n 4 です。</span><span class="sxs-lookup"><span data-stu-id="14a6a-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14a6a-118">詳細</span><span class="sxs-lookup"><span data-stu-id="14a6a-118">Details</span></span>  
  
|<span data-ttu-id="14a6a-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="14a6a-119">Data Item Name</span></span>|<span data-ttu-id="14a6a-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="14a6a-120">Data Item Type</span></span>|<span data-ttu-id="14a6a-121">説明</span><span class="sxs-lookup"><span data-stu-id="14a6a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14a6a-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="14a6a-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="14a6a-123">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="14a6a-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="14a6a-124">例外</span><span class="sxs-lookup"><span data-stu-id="14a6a-124">Exception</span></span>|`xs:string`|<span data-ttu-id="14a6a-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="14a6a-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="14a6a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14a6a-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="14a6a-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="14a6a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
