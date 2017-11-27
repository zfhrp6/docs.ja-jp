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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="353f8-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="353f8-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="353f8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="353f8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="353f8-104">ID</span><span class="sxs-lookup"><span data-stu-id="353f8-104">ID</span></span>|<span data-ttu-id="353f8-105">3502</span><span class="sxs-lookup"><span data-stu-id="353f8-105">3502</span></span>|  
|<span data-ttu-id="353f8-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="353f8-106">Keywords</span></span>|<span data-ttu-id="353f8-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="353f8-107">WFServices</span></span>|  
|<span data-ttu-id="353f8-108">レベル</span><span class="sxs-lookup"><span data-stu-id="353f8-108">Level</span></span>|<span data-ttu-id="353f8-109">情報</span><span class="sxs-lookup"><span data-stu-id="353f8-109">Information</span></span>|  
|<span data-ttu-id="353f8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="353f8-110">Channel</span></span>|<span data-ttu-id="353f8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="353f8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="353f8-112">説明</span><span class="sxs-lookup"><span data-stu-id="353f8-112">Description</span></span>  
 <span data-ttu-id="353f8-113">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="353f8-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="353f8-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="353f8-114">Message</span></span>  
 <span data-ttu-id="353f8-115">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="353f8-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="353f8-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="353f8-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="353f8-117">詳細</span><span class="sxs-lookup"><span data-stu-id="353f8-117">Details</span></span>  
  
|<span data-ttu-id="353f8-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="353f8-118">Data Item Name</span></span>|<span data-ttu-id="353f8-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="353f8-119">Data Item Type</span></span>|<span data-ttu-id="353f8-120">説明</span><span class="sxs-lookup"><span data-stu-id="353f8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="353f8-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="353f8-121">OperationName</span></span>|<span data-ttu-id="353f8-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="353f8-122">xs:string</span></span>|<span data-ttu-id="353f8-123">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="353f8-123">The name of the operation.</span></span>|  
|<span data-ttu-id="353f8-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="353f8-124">ContractName</span></span>|<span data-ttu-id="353f8-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="353f8-125">xs:string</span></span>|<span data-ttu-id="353f8-126">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="353f8-126">The name of the contract.</span></span>|  
|<span data-ttu-id="353f8-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="353f8-127">IsOneWay</span></span>|<span data-ttu-id="353f8-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="353f8-128">xs:string</span></span>|<span data-ttu-id="353f8-129">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="353f8-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="353f8-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="353f8-130">AppDomain</span></span>|<span data-ttu-id="353f8-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="353f8-131">xs:string</span></span>|<span data-ttu-id="353f8-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="353f8-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
