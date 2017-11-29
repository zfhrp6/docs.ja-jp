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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="43213-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="43213-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="43213-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="43213-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43213-104">ID</span><span class="sxs-lookup"><span data-stu-id="43213-104">ID</span></span>|<span data-ttu-id="43213-105">1008</span><span class="sxs-lookup"><span data-stu-id="43213-105">1008</span></span>|  
|<span data-ttu-id="43213-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="43213-106">Keywords</span></span>|<span data-ttu-id="43213-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="43213-107">WFRuntime</span></span>|  
|<span data-ttu-id="43213-108">レベル</span><span class="sxs-lookup"><span data-stu-id="43213-108">Level</span></span>|<span data-ttu-id="43213-109">情報</span><span class="sxs-lookup"><span data-stu-id="43213-109">Information</span></span>|  
|<span data-ttu-id="43213-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="43213-110">Channel</span></span>|<span data-ttu-id="43213-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="43213-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43213-112">説明</span><span class="sxs-lookup"><span data-stu-id="43213-112">Description</span></span>  
 <span data-ttu-id="43213-113">ワークフロー アプリケーションがアンロードしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="43213-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43213-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="43213-114">Message</span></span>  
 <span data-ttu-id="43213-115">WorkflowInstance ID: '%1' がアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="43213-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43213-116">詳細</span><span class="sxs-lookup"><span data-stu-id="43213-116">Details</span></span>  
  
|<span data-ttu-id="43213-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="43213-117">Data Item Name</span></span>|<span data-ttu-id="43213-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="43213-118">Data Item Type</span></span>|<span data-ttu-id="43213-119">説明</span><span class="sxs-lookup"><span data-stu-id="43213-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43213-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="43213-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="43213-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="43213-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="43213-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43213-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="43213-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="43213-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
