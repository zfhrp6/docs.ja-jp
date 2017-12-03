---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93a6a400576df84faae3cd58940462255b0073c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="2580a-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="2580a-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="2580a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2580a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2580a-104">ID</span><span class="sxs-lookup"><span data-stu-id="2580a-104">ID</span></span>|<span data-ttu-id="2580a-105">1002</span><span class="sxs-lookup"><span data-stu-id="2580a-105">1002</span></span>|  
|<span data-ttu-id="2580a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2580a-106">Keywords</span></span>|<span data-ttu-id="2580a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2580a-107">WFRuntime</span></span>|  
|<span data-ttu-id="2580a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2580a-108">Level</span></span>|<span data-ttu-id="2580a-109">情報</span><span class="sxs-lookup"><span data-stu-id="2580a-109">Information</span></span>|  
|<span data-ttu-id="2580a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2580a-110">Channel</span></span>|<span data-ttu-id="2580a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2580a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2580a-112">説明</span><span class="sxs-lookup"><span data-stu-id="2580a-112">Description</span></span>  
 <span data-ttu-id="2580a-113">例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="2580a-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2580a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2580a-114">Message</span></span>  
 <span data-ttu-id="2580a-115">WorkflowApplication ID: %1 は中止されました。</span><span class="sxs-lookup"><span data-stu-id="2580a-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="2580a-116">例外により Faulted 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="2580a-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2580a-117">詳細</span><span class="sxs-lookup"><span data-stu-id="2580a-117">Details</span></span>  
  
|<span data-ttu-id="2580a-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2580a-118">Data Item Name</span></span>|<span data-ttu-id="2580a-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2580a-119">Data Item Type</span></span>|<span data-ttu-id="2580a-120">説明</span><span class="sxs-lookup"><span data-stu-id="2580a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2580a-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="2580a-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="2580a-122">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="2580a-122">The workflow application id</span></span>|  
|<span data-ttu-id="2580a-123">例外</span><span class="sxs-lookup"><span data-stu-id="2580a-123">Exception</span></span>|`xs:string`|<span data-ttu-id="2580a-124">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="2580a-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="2580a-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2580a-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2580a-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2580a-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
