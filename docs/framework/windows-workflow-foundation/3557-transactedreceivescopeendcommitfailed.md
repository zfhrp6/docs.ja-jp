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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="7cadf-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="7cadf-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="7cadf-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7cadf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7cadf-104">ID</span><span class="sxs-lookup"><span data-stu-id="7cadf-104">ID</span></span>|<span data-ttu-id="7cadf-105">3557</span><span class="sxs-lookup"><span data-stu-id="7cadf-105">3557</span></span>|  
|<span data-ttu-id="7cadf-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7cadf-106">Keywords</span></span>|<span data-ttu-id="7cadf-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7cadf-107">WFServices</span></span>|  
|<span data-ttu-id="7cadf-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7cadf-108">Level</span></span>|<span data-ttu-id="7cadf-109">情報</span><span class="sxs-lookup"><span data-stu-id="7cadf-109">Information</span></span>|  
|<span data-ttu-id="7cadf-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7cadf-110">Channel</span></span>|<span data-ttu-id="7cadf-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7cadf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7cadf-112">説明</span><span class="sxs-lookup"><span data-stu-id="7cadf-112">Description</span></span>  
 <span data-ttu-id="7cadf-113">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="7cadf-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7cadf-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7cadf-114">Message</span></span>  
 <span data-ttu-id="7cadf-115">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="7cadf-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7cadf-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7cadf-116">Details</span></span>  
  
|<span data-ttu-id="7cadf-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7cadf-117">Data Item Name</span></span>|<span data-ttu-id="7cadf-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7cadf-118">Data Item Type</span></span>|<span data-ttu-id="7cadf-119">説明</span><span class="sxs-lookup"><span data-stu-id="7cadf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7cadf-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="7cadf-120">TransactionId</span></span>|<span data-ttu-id="7cadf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cadf-121">xs:string</span></span>|<span data-ttu-id="7cadf-122">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="7cadf-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="7cadf-123">例外</span><span class="sxs-lookup"><span data-stu-id="7cadf-123">Exception</span></span>|<span data-ttu-id="7cadf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cadf-124">xs:string</span></span>|<span data-ttu-id="7cadf-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="7cadf-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="7cadf-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7cadf-126">AppDomain</span></span>|<span data-ttu-id="7cadf-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cadf-127">xs:string</span></span>|<span data-ttu-id="7cadf-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7cadf-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
