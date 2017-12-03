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
ms.openlocfilehash: 8ea57cc60f9626763308267a98624c825f8312b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="83ad5-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="83ad5-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="83ad5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83ad5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83ad5-104">ID</span><span class="sxs-lookup"><span data-stu-id="83ad5-104">ID</span></span>|<span data-ttu-id="83ad5-105">3557</span><span class="sxs-lookup"><span data-stu-id="83ad5-105">3557</span></span>|  
|<span data-ttu-id="83ad5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="83ad5-106">Keywords</span></span>|<span data-ttu-id="83ad5-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="83ad5-107">WFServices</span></span>|  
|<span data-ttu-id="83ad5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="83ad5-108">Level</span></span>|<span data-ttu-id="83ad5-109">情報</span><span class="sxs-lookup"><span data-stu-id="83ad5-109">Information</span></span>|  
|<span data-ttu-id="83ad5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="83ad5-110">Channel</span></span>|<span data-ttu-id="83ad5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="83ad5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83ad5-112">説明</span><span class="sxs-lookup"><span data-stu-id="83ad5-112">Description</span></span>  
 <span data-ttu-id="83ad5-113">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="83ad5-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83ad5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="83ad5-114">Message</span></span>  
 <span data-ttu-id="83ad5-115">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="83ad5-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83ad5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="83ad5-116">Details</span></span>  
  
|<span data-ttu-id="83ad5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="83ad5-117">Data Item Name</span></span>|<span data-ttu-id="83ad5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="83ad5-118">Data Item Type</span></span>|<span data-ttu-id="83ad5-119">説明</span><span class="sxs-lookup"><span data-stu-id="83ad5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83ad5-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="83ad5-120">TransactionId</span></span>|<span data-ttu-id="83ad5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="83ad5-121">xs:string</span></span>|<span data-ttu-id="83ad5-122">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="83ad5-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="83ad5-123">例外</span><span class="sxs-lookup"><span data-stu-id="83ad5-123">Exception</span></span>|<span data-ttu-id="83ad5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="83ad5-124">xs:string</span></span>|<span data-ttu-id="83ad5-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="83ad5-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="83ad5-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83ad5-126">AppDomain</span></span>|<span data-ttu-id="83ad5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="83ad5-127">xs:string</span></span>|<span data-ttu-id="83ad5-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="83ad5-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
