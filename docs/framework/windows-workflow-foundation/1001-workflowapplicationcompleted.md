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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a62a8448319e7b07a3ea302f00f2fa269bf654ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="2e7d8-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="2e7d8-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="2e7d8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2e7d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e7d8-104">ID</span><span class="sxs-lookup"><span data-stu-id="2e7d8-104">ID</span></span>|<span data-ttu-id="2e7d8-105">1001</span><span class="sxs-lookup"><span data-stu-id="2e7d8-105">1001</span></span>|  
|<span data-ttu-id="2e7d8-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2e7d8-106">Keywords</span></span>|<span data-ttu-id="2e7d8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2e7d8-107">WFRuntime</span></span>|  
|<span data-ttu-id="2e7d8-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2e7d8-108">Level</span></span>|<span data-ttu-id="2e7d8-109">情報</span><span class="sxs-lookup"><span data-stu-id="2e7d8-109">Information</span></span>|  
|<span data-ttu-id="2e7d8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2e7d8-110">Channel</span></span>|<span data-ttu-id="2e7d8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2e7d8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2e7d8-112">説明</span><span class="sxs-lookup"><span data-stu-id="2e7d8-112">Description</span></span>  
 <span data-ttu-id="2e7d8-113">ワークフロー アプリケーションが Closed 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="2e7d8-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2e7d8-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2e7d8-114">Message</span></span>  
 <span data-ttu-id="2e7d8-115">WorkflowInstance ID: %1 は Closed 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="2e7d8-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2e7d8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2e7d8-116">Details</span></span>  
  
|<span data-ttu-id="2e7d8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2e7d8-117">Data Item Name</span></span>|<span data-ttu-id="2e7d8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2e7d8-118">Data Item Type</span></span>|<span data-ttu-id="2e7d8-119">説明</span><span class="sxs-lookup"><span data-stu-id="2e7d8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2e7d8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2e7d8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2e7d8-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="2e7d8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2e7d8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2e7d8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2e7d8-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2e7d8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
