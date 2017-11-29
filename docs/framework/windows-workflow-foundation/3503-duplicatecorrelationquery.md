---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="c2379-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="c2379-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="c2379-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c2379-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2379-104">ID</span><span class="sxs-lookup"><span data-stu-id="c2379-104">ID</span></span>|<span data-ttu-id="c2379-105">3503</span><span class="sxs-lookup"><span data-stu-id="c2379-105">3503</span></span>|  
|<span data-ttu-id="c2379-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c2379-106">Keywords</span></span>|<span data-ttu-id="c2379-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c2379-107">WFServices</span></span>|  
|<span data-ttu-id="c2379-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c2379-108">Level</span></span>|<span data-ttu-id="c2379-109">警告</span><span class="sxs-lookup"><span data-stu-id="c2379-109">Warning</span></span>|  
|<span data-ttu-id="c2379-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c2379-110">Channel</span></span>|<span data-ttu-id="c2379-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c2379-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c2379-112">説明</span><span class="sxs-lookup"><span data-stu-id="c2379-112">Description</span></span>  
 <span data-ttu-id="c2379-113">重複する CorrelationQuery が見つかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="c2379-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="c2379-114">相関の計算時には、重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c2379-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c2379-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c2379-115">Message</span></span>  
 <span data-ttu-id="c2379-116">Where='%1' で重複する CorrelationQuery が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="c2379-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="c2379-117">相関の計算時には、この重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c2379-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c2379-118">詳細</span><span class="sxs-lookup"><span data-stu-id="c2379-118">Details</span></span>  
  
|<span data-ttu-id="c2379-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c2379-119">Data Item Name</span></span>|<span data-ttu-id="c2379-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c2379-120">Data Item Type</span></span>|<span data-ttu-id="c2379-121">説明</span><span class="sxs-lookup"><span data-stu-id="c2379-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c2379-122">Where</span><span class="sxs-lookup"><span data-stu-id="c2379-122">Where</span></span>|<span data-ttu-id="c2379-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2379-123">xs:string</span></span>|<span data-ttu-id="c2379-124">関連付けクエリの Where 部分。</span><span class="sxs-lookup"><span data-stu-id="c2379-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="c2379-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c2379-125">AppDomain</span></span>|<span data-ttu-id="c2379-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="c2379-126">xs:string</span></span>|<span data-ttu-id="c2379-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c2379-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
