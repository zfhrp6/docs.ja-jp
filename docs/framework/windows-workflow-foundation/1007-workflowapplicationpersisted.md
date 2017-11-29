---
title: 1007 - WorkflowApplicationPersisted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f8aa98aec96843fb6ef169c2b168d1984ccdda5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="aec1d-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="aec1d-102">1007 - WorkflowApplicationPersisted</span></span>
## <a name="properties"></a><span data-ttu-id="aec1d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aec1d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aec1d-104">ID</span><span class="sxs-lookup"><span data-stu-id="aec1d-104">ID</span></span>|<span data-ttu-id="aec1d-105">1007</span><span class="sxs-lookup"><span data-stu-id="aec1d-105">1007</span></span>|  
|<span data-ttu-id="aec1d-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="aec1d-106">Keywords</span></span>|<span data-ttu-id="aec1d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aec1d-107">WFRuntime</span></span>|  
|<span data-ttu-id="aec1d-108">レベル</span><span class="sxs-lookup"><span data-stu-id="aec1d-108">Level</span></span>|<span data-ttu-id="aec1d-109">情報</span><span class="sxs-lookup"><span data-stu-id="aec1d-109">Information</span></span>|  
|<span data-ttu-id="aec1d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="aec1d-110">Channel</span></span>|<span data-ttu-id="aec1d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="aec1d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aec1d-112">説明</span><span class="sxs-lookup"><span data-stu-id="aec1d-112">Description</span></span>  
 <span data-ttu-id="aec1d-113">ワークフロー アプリケーションが永続化されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="aec1d-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aec1d-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="aec1d-114">Message</span></span>  
 <span data-ttu-id="aec1d-115">WorkflowApplication ID: %1 が永続化されました。</span><span class="sxs-lookup"><span data-stu-id="aec1d-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aec1d-116">詳細</span><span class="sxs-lookup"><span data-stu-id="aec1d-116">Details</span></span>  
  
|<span data-ttu-id="aec1d-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="aec1d-117">Data Item Name</span></span>|<span data-ttu-id="aec1d-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="aec1d-118">Data Item Type</span></span>|<span data-ttu-id="aec1d-119">説明</span><span class="sxs-lookup"><span data-stu-id="aec1d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aec1d-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="aec1d-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="aec1d-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="aec1d-121">The workflow application id</span></span>|  
|<span data-ttu-id="aec1d-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aec1d-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aec1d-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="aec1d-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
