---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509562"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="c87c8-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="c87c8-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="c87c8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c87c8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c87c8-104">ID</span><span class="sxs-lookup"><span data-stu-id="c87c8-104">ID</span></span>|<span data-ttu-id="c87c8-105">1008</span><span class="sxs-lookup"><span data-stu-id="c87c8-105">1008</span></span>|  
|<span data-ttu-id="c87c8-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c87c8-106">Keywords</span></span>|<span data-ttu-id="c87c8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c87c8-107">WFRuntime</span></span>|  
|<span data-ttu-id="c87c8-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c87c8-108">Level</span></span>|<span data-ttu-id="c87c8-109">情報</span><span class="sxs-lookup"><span data-stu-id="c87c8-109">Information</span></span>|  
|<span data-ttu-id="c87c8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c87c8-110">Channel</span></span>|<span data-ttu-id="c87c8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c87c8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c87c8-112">説明</span><span class="sxs-lookup"><span data-stu-id="c87c8-112">Description</span></span>  
 <span data-ttu-id="c87c8-113">ワークフロー アプリケーションがアンロードしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c87c8-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c87c8-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c87c8-114">Message</span></span>  
 <span data-ttu-id="c87c8-115">WorkflowInstance ID: '%1' がアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="c87c8-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c87c8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c87c8-116">Details</span></span>  
  
|<span data-ttu-id="c87c8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c87c8-117">Data Item Name</span></span>|<span data-ttu-id="c87c8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c87c8-118">Data Item Type</span></span>|<span data-ttu-id="c87c8-119">説明</span><span class="sxs-lookup"><span data-stu-id="c87c8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c87c8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c87c8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c87c8-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="c87c8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c87c8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c87c8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c87c8-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c87c8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
