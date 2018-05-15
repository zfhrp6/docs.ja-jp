---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="a1c05-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="a1c05-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="a1c05-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1c05-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1c05-104">ID</span><span class="sxs-lookup"><span data-stu-id="a1c05-104">ID</span></span>|<span data-ttu-id="a1c05-105">1101</span><span class="sxs-lookup"><span data-stu-id="a1c05-105">1101</span></span>|  
|<span data-ttu-id="a1c05-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a1c05-106">Keywords</span></span>|<span data-ttu-id="a1c05-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a1c05-107">WFRuntime</span></span>|  
|<span data-ttu-id="a1c05-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a1c05-108">Level</span></span>|<span data-ttu-id="a1c05-109">情報</span><span class="sxs-lookup"><span data-stu-id="a1c05-109">Information</span></span>|  
|<span data-ttu-id="a1c05-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a1c05-110">Channel</span></span>|<span data-ttu-id="a1c05-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a1c05-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1c05-112">説明</span><span class="sxs-lookup"><span data-stu-id="a1c05-112">Description</span></span>  
 <span data-ttu-id="a1c05-113">ワークフロー アクティビティが開始されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="a1c05-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1c05-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a1c05-114">Message</span></span>  
 <span data-ttu-id="a1c05-115">WorkflowInstance ID: '%1' E2E アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a1c05-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1c05-116">詳細</span><span class="sxs-lookup"><span data-stu-id="a1c05-116">Details</span></span>  
  
|<span data-ttu-id="a1c05-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a1c05-117">Data Item Name</span></span>|<span data-ttu-id="a1c05-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a1c05-118">Data Item Type</span></span>|<span data-ttu-id="a1c05-119">説明</span><span class="sxs-lookup"><span data-stu-id="a1c05-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1c05-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a1c05-120">WorkflowInstanceId</span></span>|<span data-ttu-id="a1c05-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1c05-121">xs:string</span></span>|<span data-ttu-id="a1c05-122">ワークフロー インスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a1c05-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="a1c05-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a1c05-123">AppDomain</span></span>|<span data-ttu-id="a1c05-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1c05-124">xs:string</span></span>|<span data-ttu-id="a1c05-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a1c05-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
