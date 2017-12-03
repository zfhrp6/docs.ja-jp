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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b86289340c35d24552b1d524a3cceaacb2f0420
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="a65d4-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="a65d4-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="a65d4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a65d4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a65d4-104">ID</span><span class="sxs-lookup"><span data-stu-id="a65d4-104">ID</span></span>|<span data-ttu-id="a65d4-105">3503</span><span class="sxs-lookup"><span data-stu-id="a65d4-105">3503</span></span>|  
|<span data-ttu-id="a65d4-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a65d4-106">Keywords</span></span>|<span data-ttu-id="a65d4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="a65d4-107">WFServices</span></span>|  
|<span data-ttu-id="a65d4-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a65d4-108">Level</span></span>|<span data-ttu-id="a65d4-109">警告</span><span class="sxs-lookup"><span data-stu-id="a65d4-109">Warning</span></span>|  
|<span data-ttu-id="a65d4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a65d4-110">Channel</span></span>|<span data-ttu-id="a65d4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a65d4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a65d4-112">説明</span><span class="sxs-lookup"><span data-stu-id="a65d4-112">Description</span></span>  
 <span data-ttu-id="a65d4-113">重複する CorrelationQuery が見つかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="a65d4-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="a65d4-114">相関の計算時には、重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="a65d4-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a65d4-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a65d4-115">Message</span></span>  
 <span data-ttu-id="a65d4-116">Where='%1' で重複する CorrelationQuery が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="a65d4-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="a65d4-117">相関の計算時には、この重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="a65d4-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a65d4-118">詳細</span><span class="sxs-lookup"><span data-stu-id="a65d4-118">Details</span></span>  
  
|<span data-ttu-id="a65d4-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a65d4-119">Data Item Name</span></span>|<span data-ttu-id="a65d4-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a65d4-120">Data Item Type</span></span>|<span data-ttu-id="a65d4-121">説明</span><span class="sxs-lookup"><span data-stu-id="a65d4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a65d4-122">Where</span><span class="sxs-lookup"><span data-stu-id="a65d4-122">Where</span></span>|<span data-ttu-id="a65d4-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="a65d4-123">xs:string</span></span>|<span data-ttu-id="a65d4-124">関連付けクエリの Where 部分。</span><span class="sxs-lookup"><span data-stu-id="a65d4-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="a65d4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a65d4-125">AppDomain</span></span>|<span data-ttu-id="a65d4-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="a65d4-126">xs:string</span></span>|<span data-ttu-id="a65d4-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a65d4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
