---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="01447-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="01447-102">2577 - TryCatchExceptionDuringCancelation</span></span>
## <a name="properties"></a><span data-ttu-id="01447-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="01447-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01447-104">ID</span><span class="sxs-lookup"><span data-stu-id="01447-104">ID</span></span>|<span data-ttu-id="01447-105">2577</span><span class="sxs-lookup"><span data-stu-id="01447-105">2577</span></span>|  
|<span data-ttu-id="01447-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="01447-106">Keywords</span></span>|<span data-ttu-id="01447-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="01447-107">WFActivities</span></span>|  
|<span data-ttu-id="01447-108">レベル</span><span class="sxs-lookup"><span data-stu-id="01447-108">Level</span></span>|<span data-ttu-id="01447-109">警告</span><span class="sxs-lookup"><span data-stu-id="01447-109">Warning</span></span>|  
|<span data-ttu-id="01447-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="01447-110">Channel</span></span>|<span data-ttu-id="01447-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="01447-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01447-112">説明</span><span class="sxs-lookup"><span data-stu-id="01447-112">Description</span></span>  
 <span data-ttu-id="01447-113">TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="01447-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01447-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="01447-114">Message</span></span>  
 <span data-ttu-id="01447-115">TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="01447-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="01447-116">詳細</span><span class="sxs-lookup"><span data-stu-id="01447-116">Details</span></span>  
  
|<span data-ttu-id="01447-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="01447-117">Data Item Name</span></span>|<span data-ttu-id="01447-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="01447-118">Data Item Type</span></span>|<span data-ttu-id="01447-119">説明</span><span class="sxs-lookup"><span data-stu-id="01447-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01447-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="01447-120">DisplayName</span></span>|<span data-ttu-id="01447-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="01447-121">xs:string</span></span>|<span data-ttu-id="01447-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="01447-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="01447-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01447-123">AppDomain</span></span>|<span data-ttu-id="01447-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="01447-124">xs:string</span></span>|<span data-ttu-id="01447-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="01447-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
