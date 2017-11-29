---
title: 1150 - CompensationState
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5debccf664768b84a7b213cd012b484df8fe3ef8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1150---compensationstate"></a><span data-ttu-id="baf5b-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="baf5b-102">1150 - CompensationState</span></span>
## <a name="properties"></a><span data-ttu-id="baf5b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="baf5b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="baf5b-104">ID</span><span class="sxs-lookup"><span data-stu-id="baf5b-104">ID</span></span>|<span data-ttu-id="baf5b-105">1150</span><span class="sxs-lookup"><span data-stu-id="baf5b-105">1150</span></span>|  
|<span data-ttu-id="baf5b-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="baf5b-106">Keywords</span></span>|<span data-ttu-id="baf5b-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="baf5b-107">WFActivities</span></span>|  
|<span data-ttu-id="baf5b-108">レベル</span><span class="sxs-lookup"><span data-stu-id="baf5b-108">Level</span></span>|<span data-ttu-id="baf5b-109">情報</span><span class="sxs-lookup"><span data-stu-id="baf5b-109">Information</span></span>|  
|<span data-ttu-id="baf5b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="baf5b-110">Channel</span></span>|<span data-ttu-id="baf5b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="baf5b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="baf5b-112">説明</span><span class="sxs-lookup"><span data-stu-id="baf5b-112">Description</span></span>  
 <span data-ttu-id="baf5b-113">CompensableActivity の状態の変更を示します。</span><span class="sxs-lookup"><span data-stu-id="baf5b-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="baf5b-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="baf5b-114">Message</span></span>  
 <span data-ttu-id="baf5b-115">CompensableActivity '%1' は '%2' 状態です。</span><span class="sxs-lookup"><span data-stu-id="baf5b-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="baf5b-116">詳細</span><span class="sxs-lookup"><span data-stu-id="baf5b-116">Details</span></span>  
  
|<span data-ttu-id="baf5b-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="baf5b-117">Data Item Name</span></span>|<span data-ttu-id="baf5b-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="baf5b-118">Data Item Type</span></span>|<span data-ttu-id="baf5b-119">説明</span><span class="sxs-lookup"><span data-stu-id="baf5b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="baf5b-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="baf5b-120">DisplayName</span></span>|<span data-ttu-id="baf5b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="baf5b-121">xs:string</span></span>|<span data-ttu-id="baf5b-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="baf5b-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="baf5b-123">状態</span><span class="sxs-lookup"><span data-stu-id="baf5b-123">State</span></span>|<span data-ttu-id="baf5b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="baf5b-124">xs:string</span></span>|<span data-ttu-id="baf5b-125">補正の状態。</span><span class="sxs-lookup"><span data-stu-id="baf5b-125">The compensation state.</span></span>|  
|<span data-ttu-id="baf5b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="baf5b-126">AppDomain</span></span>|<span data-ttu-id="baf5b-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="baf5b-127">xs:string</span></span>|<span data-ttu-id="baf5b-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="baf5b-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
