---
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: 0b3c290ad06eda6921626c0d7a1c8ec854c30e7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509718"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="df588-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="df588-102">1007 - WorkflowApplicationPersisted</span></span>
## <a name="properties"></a><span data-ttu-id="df588-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="df588-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="df588-104">ID</span><span class="sxs-lookup"><span data-stu-id="df588-104">ID</span></span>|<span data-ttu-id="df588-105">1007</span><span class="sxs-lookup"><span data-stu-id="df588-105">1007</span></span>|  
|<span data-ttu-id="df588-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="df588-106">Keywords</span></span>|<span data-ttu-id="df588-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="df588-107">WFRuntime</span></span>|  
|<span data-ttu-id="df588-108">レベル</span><span class="sxs-lookup"><span data-stu-id="df588-108">Level</span></span>|<span data-ttu-id="df588-109">情報</span><span class="sxs-lookup"><span data-stu-id="df588-109">Information</span></span>|  
|<span data-ttu-id="df588-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="df588-110">Channel</span></span>|<span data-ttu-id="df588-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="df588-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="df588-112">説明</span><span class="sxs-lookup"><span data-stu-id="df588-112">Description</span></span>  
 <span data-ttu-id="df588-113">ワークフロー アプリケーションが永続化されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="df588-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="df588-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="df588-114">Message</span></span>  
 <span data-ttu-id="df588-115">WorkflowApplication ID: %1 が永続化されました。</span><span class="sxs-lookup"><span data-stu-id="df588-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="df588-116">詳細</span><span class="sxs-lookup"><span data-stu-id="df588-116">Details</span></span>  
  
|<span data-ttu-id="df588-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="df588-117">Data Item Name</span></span>|<span data-ttu-id="df588-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="df588-118">Data Item Type</span></span>|<span data-ttu-id="df588-119">説明</span><span class="sxs-lookup"><span data-stu-id="df588-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="df588-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="df588-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="df588-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="df588-121">The workflow application id</span></span>|  
|<span data-ttu-id="df588-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="df588-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="df588-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="df588-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
