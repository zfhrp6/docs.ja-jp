---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510758"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="17bb7-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="17bb7-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="17bb7-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="17bb7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17bb7-104">ID</span><span class="sxs-lookup"><span data-stu-id="17bb7-104">ID</span></span>|<span data-ttu-id="17bb7-105">1006</span><span class="sxs-lookup"><span data-stu-id="17bb7-105">1006</span></span>|  
|<span data-ttu-id="17bb7-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="17bb7-106">Keywords</span></span>|<span data-ttu-id="17bb7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="17bb7-107">WFRuntime</span></span>|  
|<span data-ttu-id="17bb7-108">レベル</span><span class="sxs-lookup"><span data-stu-id="17bb7-108">Level</span></span>|<span data-ttu-id="17bb7-109">Error</span><span class="sxs-lookup"><span data-stu-id="17bb7-109">Error</span></span>|  
|<span data-ttu-id="17bb7-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="17bb7-110">Channel</span></span>|<span data-ttu-id="17bb7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="17bb7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17bb7-112">説明</span><span class="sxs-lookup"><span data-stu-id="17bb7-112">Description</span></span>  
 <span data-ttu-id="17bb7-113">ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="17bb7-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17bb7-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="17bb7-114">Message</span></span>  
 <span data-ttu-id="17bb7-115">WorkflowInstance Id: '%1' はハンドルされない例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="17bb7-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="17bb7-116">例外の発生元 Activity '%2'、DisplayName: '%3' です。</span><span class="sxs-lookup"><span data-stu-id="17bb7-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="17bb7-117">次の操作が実行されます: %n%n 4 です。</span><span class="sxs-lookup"><span data-stu-id="17bb7-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17bb7-118">説明</span><span class="sxs-lookup"><span data-stu-id="17bb7-118">Details</span></span>  
  
|<span data-ttu-id="17bb7-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="17bb7-119">Data Item Name</span></span>|<span data-ttu-id="17bb7-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="17bb7-120">Data Item Type</span></span>|<span data-ttu-id="17bb7-121">説明</span><span class="sxs-lookup"><span data-stu-id="17bb7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17bb7-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="17bb7-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="17bb7-123">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="17bb7-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="17bb7-124">例外</span><span class="sxs-lookup"><span data-stu-id="17bb7-124">Exception</span></span>|`xs:string`|<span data-ttu-id="17bb7-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="17bb7-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="17bb7-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="17bb7-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="17bb7-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="17bb7-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
