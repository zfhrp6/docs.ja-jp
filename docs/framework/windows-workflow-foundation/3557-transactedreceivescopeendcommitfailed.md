---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="31508-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="31508-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="31508-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="31508-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31508-104">ID</span><span class="sxs-lookup"><span data-stu-id="31508-104">ID</span></span>|<span data-ttu-id="31508-105">3557</span><span class="sxs-lookup"><span data-stu-id="31508-105">3557</span></span>|  
|<span data-ttu-id="31508-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="31508-106">Keywords</span></span>|<span data-ttu-id="31508-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="31508-107">WFServices</span></span>|  
|<span data-ttu-id="31508-108">レベル</span><span class="sxs-lookup"><span data-stu-id="31508-108">Level</span></span>|<span data-ttu-id="31508-109">情報</span><span class="sxs-lookup"><span data-stu-id="31508-109">Information</span></span>|  
|<span data-ttu-id="31508-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="31508-110">Channel</span></span>|<span data-ttu-id="31508-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="31508-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="31508-112">説明</span><span class="sxs-lookup"><span data-stu-id="31508-112">Description</span></span>  
 <span data-ttu-id="31508-113">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="31508-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="31508-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="31508-114">Message</span></span>  
 <span data-ttu-id="31508-115">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="31508-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31508-116">詳細</span><span class="sxs-lookup"><span data-stu-id="31508-116">Details</span></span>  
  
|<span data-ttu-id="31508-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="31508-117">Data Item Name</span></span>|<span data-ttu-id="31508-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="31508-118">Data Item Type</span></span>|<span data-ttu-id="31508-119">説明</span><span class="sxs-lookup"><span data-stu-id="31508-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="31508-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="31508-120">TransactionId</span></span>|<span data-ttu-id="31508-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="31508-121">xs:string</span></span>|<span data-ttu-id="31508-122">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="31508-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="31508-123">例外</span><span class="sxs-lookup"><span data-stu-id="31508-123">Exception</span></span>|<span data-ttu-id="31508-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="31508-124">xs:string</span></span>|<span data-ttu-id="31508-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="31508-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="31508-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="31508-126">AppDomain</span></span>|<span data-ttu-id="31508-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="31508-127">xs:string</span></span>|<span data-ttu-id="31508-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="31508-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
