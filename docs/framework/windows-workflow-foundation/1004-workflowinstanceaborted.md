---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="93c77-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="93c77-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="93c77-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="93c77-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93c77-104">ID</span><span class="sxs-lookup"><span data-stu-id="93c77-104">ID</span></span>|<span data-ttu-id="93c77-105">1004</span><span class="sxs-lookup"><span data-stu-id="93c77-105">1004</span></span>|  
|<span data-ttu-id="93c77-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="93c77-106">Keywords</span></span>|<span data-ttu-id="93c77-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="93c77-107">WFRuntime</span></span>|  
|<span data-ttu-id="93c77-108">レベル</span><span class="sxs-lookup"><span data-stu-id="93c77-108">Level</span></span>|<span data-ttu-id="93c77-109">情報</span><span class="sxs-lookup"><span data-stu-id="93c77-109">Information</span></span>|  
|<span data-ttu-id="93c77-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="93c77-110">Channel</span></span>|<span data-ttu-id="93c77-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="93c77-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93c77-112">説明</span><span class="sxs-lookup"><span data-stu-id="93c77-112">Description</span></span>  
 <span data-ttu-id="93c77-113">ワークフロー インスタンスが例外で中断されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="93c77-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93c77-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="93c77-114">Message</span></span>  
 <span data-ttu-id="93c77-115">WorkflowInstance ID: '%1' は例外により中止されました。</span><span class="sxs-lookup"><span data-stu-id="93c77-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93c77-116">詳細</span><span class="sxs-lookup"><span data-stu-id="93c77-116">Details</span></span>  
  
|<span data-ttu-id="93c77-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="93c77-117">Data Item Name</span></span>|<span data-ttu-id="93c77-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="93c77-118">Data Item Type</span></span>|<span data-ttu-id="93c77-119">説明</span><span class="sxs-lookup"><span data-stu-id="93c77-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93c77-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="93c77-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="93c77-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="93c77-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="93c77-122">例外</span><span class="sxs-lookup"><span data-stu-id="93c77-122">Exception</span></span>|`xs:string`|<span data-ttu-id="93c77-123">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="93c77-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="93c77-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="93c77-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="93c77-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="93c77-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
