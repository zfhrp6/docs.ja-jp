---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509770"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="cbd78-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="cbd78-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="cbd78-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cbd78-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cbd78-104">ID</span><span class="sxs-lookup"><span data-stu-id="cbd78-104">ID</span></span>|<span data-ttu-id="cbd78-105">1003</span><span class="sxs-lookup"><span data-stu-id="cbd78-105">1003</span></span>|  
|<span data-ttu-id="cbd78-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="cbd78-106">Keywords</span></span>|<span data-ttu-id="cbd78-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cbd78-107">WFRuntime</span></span>|  
|<span data-ttu-id="cbd78-108">レベル</span><span class="sxs-lookup"><span data-stu-id="cbd78-108">Level</span></span>|<span data-ttu-id="cbd78-109">情報</span><span class="sxs-lookup"><span data-stu-id="cbd78-109">Information</span></span>|  
|<span data-ttu-id="cbd78-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="cbd78-110">Channel</span></span>|<span data-ttu-id="cbd78-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cbd78-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cbd78-112">説明</span><span class="sxs-lookup"><span data-stu-id="cbd78-112">Description</span></span>  
 <span data-ttu-id="cbd78-113">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cbd78-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cbd78-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="cbd78-114">Message</span></span>  
 <span data-ttu-id="cbd78-115">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="cbd78-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cbd78-116">詳細</span><span class="sxs-lookup"><span data-stu-id="cbd78-116">Details</span></span>  
  
|<span data-ttu-id="cbd78-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cbd78-117">Data Item Name</span></span>|<span data-ttu-id="cbd78-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cbd78-118">Data Item Type</span></span>|<span data-ttu-id="cbd78-119">説明</span><span class="sxs-lookup"><span data-stu-id="cbd78-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cbd78-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cbd78-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cbd78-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="cbd78-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cbd78-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cbd78-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cbd78-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cbd78-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
