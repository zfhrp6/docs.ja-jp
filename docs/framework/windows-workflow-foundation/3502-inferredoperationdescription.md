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
ms.workload: dotnet
ms.openlocfilehash: e2c2464cd8c6f0c16946847a5503270453d5b019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="572fe-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="572fe-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="572fe-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="572fe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="572fe-104">ID</span><span class="sxs-lookup"><span data-stu-id="572fe-104">ID</span></span>|<span data-ttu-id="572fe-105">3502</span><span class="sxs-lookup"><span data-stu-id="572fe-105">3502</span></span>|  
|<span data-ttu-id="572fe-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="572fe-106">Keywords</span></span>|<span data-ttu-id="572fe-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="572fe-107">WFServices</span></span>|  
|<span data-ttu-id="572fe-108">レベル</span><span class="sxs-lookup"><span data-stu-id="572fe-108">Level</span></span>|<span data-ttu-id="572fe-109">情報</span><span class="sxs-lookup"><span data-stu-id="572fe-109">Information</span></span>|  
|<span data-ttu-id="572fe-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="572fe-110">Channel</span></span>|<span data-ttu-id="572fe-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="572fe-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="572fe-112">説明</span><span class="sxs-lookup"><span data-stu-id="572fe-112">Description</span></span>  
 <span data-ttu-id="572fe-113">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="572fe-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="572fe-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="572fe-114">Message</span></span>  
 <span data-ttu-id="572fe-115">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="572fe-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="572fe-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="572fe-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="572fe-117">詳細</span><span class="sxs-lookup"><span data-stu-id="572fe-117">Details</span></span>  
  
|<span data-ttu-id="572fe-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="572fe-118">Data Item Name</span></span>|<span data-ttu-id="572fe-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="572fe-119">Data Item Type</span></span>|<span data-ttu-id="572fe-120">説明</span><span class="sxs-lookup"><span data-stu-id="572fe-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="572fe-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="572fe-121">OperationName</span></span>|<span data-ttu-id="572fe-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="572fe-122">xs:string</span></span>|<span data-ttu-id="572fe-123">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="572fe-123">The name of the operation.</span></span>|  
|<span data-ttu-id="572fe-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="572fe-124">ContractName</span></span>|<span data-ttu-id="572fe-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="572fe-125">xs:string</span></span>|<span data-ttu-id="572fe-126">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="572fe-126">The name of the contract.</span></span>|  
|<span data-ttu-id="572fe-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="572fe-127">IsOneWay</span></span>|<span data-ttu-id="572fe-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="572fe-128">xs:string</span></span>|<span data-ttu-id="572fe-129">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="572fe-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="572fe-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="572fe-130">AppDomain</span></span>|<span data-ttu-id="572fe-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="572fe-131">xs:string</span></span>|<span data-ttu-id="572fe-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="572fe-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
