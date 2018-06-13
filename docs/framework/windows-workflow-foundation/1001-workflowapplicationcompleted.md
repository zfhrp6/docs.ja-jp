---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509796"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="32ffc-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="32ffc-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="32ffc-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="32ffc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="32ffc-104">ID</span><span class="sxs-lookup"><span data-stu-id="32ffc-104">ID</span></span>|<span data-ttu-id="32ffc-105">1001</span><span class="sxs-lookup"><span data-stu-id="32ffc-105">1001</span></span>|  
|<span data-ttu-id="32ffc-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="32ffc-106">Keywords</span></span>|<span data-ttu-id="32ffc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="32ffc-107">WFRuntime</span></span>|  
|<span data-ttu-id="32ffc-108">レベル</span><span class="sxs-lookup"><span data-stu-id="32ffc-108">Level</span></span>|<span data-ttu-id="32ffc-109">情報</span><span class="sxs-lookup"><span data-stu-id="32ffc-109">Information</span></span>|  
|<span data-ttu-id="32ffc-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="32ffc-110">Channel</span></span>|<span data-ttu-id="32ffc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="32ffc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="32ffc-112">説明</span><span class="sxs-lookup"><span data-stu-id="32ffc-112">Description</span></span>  
 <span data-ttu-id="32ffc-113">ワークフロー アプリケーションが Closed 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="32ffc-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="32ffc-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="32ffc-114">Message</span></span>  
 <span data-ttu-id="32ffc-115">WorkflowInstance ID: %1 は Closed 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="32ffc-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="32ffc-116">詳細</span><span class="sxs-lookup"><span data-stu-id="32ffc-116">Details</span></span>  
  
|<span data-ttu-id="32ffc-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="32ffc-117">Data Item Name</span></span>|<span data-ttu-id="32ffc-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="32ffc-118">Data Item Type</span></span>|<span data-ttu-id="32ffc-119">説明</span><span class="sxs-lookup"><span data-stu-id="32ffc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="32ffc-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="32ffc-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="32ffc-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="32ffc-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="32ffc-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="32ffc-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="32ffc-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="32ffc-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
