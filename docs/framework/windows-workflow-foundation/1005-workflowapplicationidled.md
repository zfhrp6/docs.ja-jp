---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="98a4e-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="98a4e-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="98a4e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="98a4e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="98a4e-104">ID</span><span class="sxs-lookup"><span data-stu-id="98a4e-104">ID</span></span>|<span data-ttu-id="98a4e-105">1005</span><span class="sxs-lookup"><span data-stu-id="98a4e-105">1005</span></span>|  
|<span data-ttu-id="98a4e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="98a4e-106">Keywords</span></span>|<span data-ttu-id="98a4e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="98a4e-107">WFRuntime</span></span>|  
|<span data-ttu-id="98a4e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="98a4e-108">Level</span></span>|<span data-ttu-id="98a4e-109">情報</span><span class="sxs-lookup"><span data-stu-id="98a4e-109">Information</span></span>|  
|<span data-ttu-id="98a4e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="98a4e-110">Channel</span></span>|<span data-ttu-id="98a4e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="98a4e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="98a4e-112">説明</span><span class="sxs-lookup"><span data-stu-id="98a4e-112">Description</span></span>  
 <span data-ttu-id="98a4e-113">ワークフロー アプリケーションがアイドル状態になったことを示します。</span><span class="sxs-lookup"><span data-stu-id="98a4e-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="98a4e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="98a4e-114">Message</span></span>  
 <span data-ttu-id="98a4e-115">WorkflowApplication ID: '%1' がアイドル状態になりました。</span><span class="sxs-lookup"><span data-stu-id="98a4e-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="98a4e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="98a4e-116">Details</span></span>  
  
|<span data-ttu-id="98a4e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="98a4e-117">Data Item Name</span></span>|<span data-ttu-id="98a4e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="98a4e-118">Data Item Type</span></span>|<span data-ttu-id="98a4e-119">説明</span><span class="sxs-lookup"><span data-stu-id="98a4e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="98a4e-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="98a4e-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="98a4e-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="98a4e-121">The workflow application id</span></span>|  
|<span data-ttu-id="98a4e-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="98a4e-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="98a4e-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="98a4e-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
