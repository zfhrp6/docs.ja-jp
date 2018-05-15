---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="0a563-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="0a563-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="0a563-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0a563-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a563-104">ID</span><span class="sxs-lookup"><span data-stu-id="0a563-104">ID</span></span>|<span data-ttu-id="0a563-105">3502</span><span class="sxs-lookup"><span data-stu-id="0a563-105">3502</span></span>|  
|<span data-ttu-id="0a563-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="0a563-106">Keywords</span></span>|<span data-ttu-id="0a563-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0a563-107">WFServices</span></span>|  
|<span data-ttu-id="0a563-108">レベル</span><span class="sxs-lookup"><span data-stu-id="0a563-108">Level</span></span>|<span data-ttu-id="0a563-109">情報</span><span class="sxs-lookup"><span data-stu-id="0a563-109">Information</span></span>|  
|<span data-ttu-id="0a563-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0a563-110">Channel</span></span>|<span data-ttu-id="0a563-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0a563-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a563-112">説明</span><span class="sxs-lookup"><span data-stu-id="0a563-112">Description</span></span>  
 <span data-ttu-id="0a563-113">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="0a563-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0a563-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="0a563-114">Message</span></span>  
 <span data-ttu-id="0a563-115">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="0a563-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="0a563-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="0a563-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0a563-117">詳細</span><span class="sxs-lookup"><span data-stu-id="0a563-117">Details</span></span>  
  
|<span data-ttu-id="0a563-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0a563-118">Data Item Name</span></span>|<span data-ttu-id="0a563-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0a563-119">Data Item Type</span></span>|<span data-ttu-id="0a563-120">説明</span><span class="sxs-lookup"><span data-stu-id="0a563-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0a563-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="0a563-121">OperationName</span></span>|<span data-ttu-id="0a563-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a563-122">xs:string</span></span>|<span data-ttu-id="0a563-123">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="0a563-123">The name of the operation.</span></span>|  
|<span data-ttu-id="0a563-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="0a563-124">ContractName</span></span>|<span data-ttu-id="0a563-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a563-125">xs:string</span></span>|<span data-ttu-id="0a563-126">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="0a563-126">The name of the contract.</span></span>|  
|<span data-ttu-id="0a563-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="0a563-127">IsOneWay</span></span>|<span data-ttu-id="0a563-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a563-128">xs:string</span></span>|<span data-ttu-id="0a563-129">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="0a563-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="0a563-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0a563-130">AppDomain</span></span>|<span data-ttu-id="0a563-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="0a563-131">xs:string</span></span>|<span data-ttu-id="0a563-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0a563-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
