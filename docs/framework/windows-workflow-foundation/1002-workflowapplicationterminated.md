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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="b6413-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="b6413-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="b6413-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b6413-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6413-104">ID</span><span class="sxs-lookup"><span data-stu-id="b6413-104">ID</span></span>|<span data-ttu-id="b6413-105">1002</span><span class="sxs-lookup"><span data-stu-id="b6413-105">1002</span></span>|  
|<span data-ttu-id="b6413-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b6413-106">Keywords</span></span>|<span data-ttu-id="b6413-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b6413-107">WFRuntime</span></span>|  
|<span data-ttu-id="b6413-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b6413-108">Level</span></span>|<span data-ttu-id="b6413-109">情報</span><span class="sxs-lookup"><span data-stu-id="b6413-109">Information</span></span>|  
|<span data-ttu-id="b6413-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b6413-110">Channel</span></span>|<span data-ttu-id="b6413-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b6413-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b6413-112">説明</span><span class="sxs-lookup"><span data-stu-id="b6413-112">Description</span></span>  
 <span data-ttu-id="b6413-113">例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b6413-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b6413-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b6413-114">Message</span></span>  
 <span data-ttu-id="b6413-115">WorkflowApplication ID: %1 は中止されました。</span><span class="sxs-lookup"><span data-stu-id="b6413-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="b6413-116">例外により Faulted 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="b6413-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b6413-117">詳細</span><span class="sxs-lookup"><span data-stu-id="b6413-117">Details</span></span>  
  
|<span data-ttu-id="b6413-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b6413-118">Data Item Name</span></span>|<span data-ttu-id="b6413-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b6413-119">Data Item Type</span></span>|<span data-ttu-id="b6413-120">説明</span><span class="sxs-lookup"><span data-stu-id="b6413-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b6413-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="b6413-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="b6413-122">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="b6413-122">The workflow application id</span></span>|  
|<span data-ttu-id="b6413-123">例外</span><span class="sxs-lookup"><span data-stu-id="b6413-123">Exception</span></span>|`xs:string`|<span data-ttu-id="b6413-124">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="b6413-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="b6413-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b6413-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b6413-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b6413-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
