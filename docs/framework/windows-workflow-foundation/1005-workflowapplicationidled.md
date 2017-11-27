---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="520d9-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="520d9-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="520d9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="520d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="520d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="520d9-104">ID</span></span>|<span data-ttu-id="520d9-105">1005</span><span class="sxs-lookup"><span data-stu-id="520d9-105">1005</span></span>|  
|<span data-ttu-id="520d9-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="520d9-106">Keywords</span></span>|<span data-ttu-id="520d9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="520d9-107">WFRuntime</span></span>|  
|<span data-ttu-id="520d9-108">レベル</span><span class="sxs-lookup"><span data-stu-id="520d9-108">Level</span></span>|<span data-ttu-id="520d9-109">情報</span><span class="sxs-lookup"><span data-stu-id="520d9-109">Information</span></span>|  
|<span data-ttu-id="520d9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="520d9-110">Channel</span></span>|<span data-ttu-id="520d9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="520d9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="520d9-112">説明</span><span class="sxs-lookup"><span data-stu-id="520d9-112">Description</span></span>  
 <span data-ttu-id="520d9-113">ワークフロー アプリケーションがアイドル状態になったことを示します。</span><span class="sxs-lookup"><span data-stu-id="520d9-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="520d9-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="520d9-114">Message</span></span>  
 <span data-ttu-id="520d9-115">WorkflowApplication ID: '%1' がアイドル状態になりました。</span><span class="sxs-lookup"><span data-stu-id="520d9-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="520d9-116">詳細</span><span class="sxs-lookup"><span data-stu-id="520d9-116">Details</span></span>  
  
|<span data-ttu-id="520d9-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="520d9-117">Data Item Name</span></span>|<span data-ttu-id="520d9-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="520d9-118">Data Item Type</span></span>|<span data-ttu-id="520d9-119">説明</span><span class="sxs-lookup"><span data-stu-id="520d9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="520d9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="520d9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="520d9-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="520d9-121">The workflow application id</span></span>|  
|<span data-ttu-id="520d9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="520d9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="520d9-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="520d9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
