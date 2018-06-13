---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509668"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="36aab-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="36aab-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="36aab-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="36aab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36aab-104">ID</span><span class="sxs-lookup"><span data-stu-id="36aab-104">ID</span></span>|<span data-ttu-id="36aab-105">1041</span><span class="sxs-lookup"><span data-stu-id="36aab-105">1041</span></span>|  
|<span data-ttu-id="36aab-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="36aab-106">Keywords</span></span>|<span data-ttu-id="36aab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="36aab-107">WFRuntime</span></span>|  
|<span data-ttu-id="36aab-108">レベル</span><span class="sxs-lookup"><span data-stu-id="36aab-108">Level</span></span>|<span data-ttu-id="36aab-109">情報</span><span class="sxs-lookup"><span data-stu-id="36aab-109">Information</span></span>|  
|<span data-ttu-id="36aab-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="36aab-110">Channel</span></span>|<span data-ttu-id="36aab-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="36aab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="36aab-112">説明</span><span class="sxs-lookup"><span data-stu-id="36aab-112">Description</span></span>  
 <span data-ttu-id="36aab-113">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="36aab-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="36aab-114">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="36aab-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="36aab-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="36aab-115">Message</span></span>  
 <span data-ttu-id="36aab-116">WorkflowApplication Id: '%1' には、アイドル状態のままです。</span><span class="sxs-lookup"><span data-stu-id="36aab-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="36aab-117">次の操作が実行されます: %n%n 2 です。</span><span class="sxs-lookup"><span data-stu-id="36aab-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="36aab-118">説明</span><span class="sxs-lookup"><span data-stu-id="36aab-118">Details</span></span>  
  
|<span data-ttu-id="36aab-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="36aab-119">Data Item Name</span></span>|<span data-ttu-id="36aab-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="36aab-120">Data Item Type</span></span>|<span data-ttu-id="36aab-121">説明</span><span class="sxs-lookup"><span data-stu-id="36aab-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="36aab-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="36aab-122">WorkflowApplicationId</span></span>|<span data-ttu-id="36aab-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="36aab-123">xs:string</span></span>|<span data-ttu-id="36aab-124">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="36aab-124">The workflow application id</span></span>|  
|<span data-ttu-id="36aab-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="36aab-125">ActionTaken</span></span>|<span data-ttu-id="36aab-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="36aab-126">xs:string</span></span>|<span data-ttu-id="36aab-127">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="36aab-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="36aab-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="36aab-128">AppDomain</span></span>|<span data-ttu-id="36aab-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="36aab-129">xs:string</span></span>|<span data-ttu-id="36aab-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="36aab-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
