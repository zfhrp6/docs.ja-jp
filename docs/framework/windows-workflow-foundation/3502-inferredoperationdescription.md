---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 144ab1a4a2fd313dc7817846e3e0118145cd3f8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="1872d-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="1872d-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="1872d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1872d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1872d-104">ID</span><span class="sxs-lookup"><span data-stu-id="1872d-104">ID</span></span>|<span data-ttu-id="1872d-105">3502</span><span class="sxs-lookup"><span data-stu-id="1872d-105">3502</span></span>|  
|<span data-ttu-id="1872d-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1872d-106">Keywords</span></span>|<span data-ttu-id="1872d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1872d-107">WFServices</span></span>|  
|<span data-ttu-id="1872d-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1872d-108">Level</span></span>|<span data-ttu-id="1872d-109">情報</span><span class="sxs-lookup"><span data-stu-id="1872d-109">Information</span></span>|  
|<span data-ttu-id="1872d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1872d-110">Channel</span></span>|<span data-ttu-id="1872d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1872d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1872d-112">説明</span><span class="sxs-lookup"><span data-stu-id="1872d-112">Description</span></span>  
 <span data-ttu-id="1872d-113">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="1872d-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1872d-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1872d-114">Message</span></span>  
 <span data-ttu-id="1872d-115">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="1872d-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="1872d-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="1872d-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1872d-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1872d-117">Details</span></span>  
  
|<span data-ttu-id="1872d-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1872d-118">Data Item Name</span></span>|<span data-ttu-id="1872d-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1872d-119">Data Item Type</span></span>|<span data-ttu-id="1872d-120">説明</span><span class="sxs-lookup"><span data-stu-id="1872d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1872d-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="1872d-121">OperationName</span></span>|<span data-ttu-id="1872d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1872d-122">xs:string</span></span>|<span data-ttu-id="1872d-123">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="1872d-123">The name of the operation.</span></span>|  
|<span data-ttu-id="1872d-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="1872d-124">ContractName</span></span>|<span data-ttu-id="1872d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1872d-125">xs:string</span></span>|<span data-ttu-id="1872d-126">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="1872d-126">The name of the contract.</span></span>|  
|<span data-ttu-id="1872d-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="1872d-127">IsOneWay</span></span>|<span data-ttu-id="1872d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1872d-128">xs:string</span></span>|<span data-ttu-id="1872d-129">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1872d-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="1872d-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1872d-130">AppDomain</span></span>|<span data-ttu-id="1872d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1872d-131">xs:string</span></span>|<span data-ttu-id="1872d-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1872d-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
