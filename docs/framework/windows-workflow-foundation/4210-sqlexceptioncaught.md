---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbcb566574e38e3c4688c16bd29a33ff7048bfa4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="57dc2-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="57dc2-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="57dc2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="57dc2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57dc2-104">ID</span><span class="sxs-lookup"><span data-stu-id="57dc2-104">ID</span></span>|<span data-ttu-id="57dc2-105">4210</span><span class="sxs-lookup"><span data-stu-id="57dc2-105">4210</span></span>|  
|<span data-ttu-id="57dc2-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="57dc2-106">Keywords</span></span>|<span data-ttu-id="57dc2-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="57dc2-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="57dc2-108">レベル</span><span class="sxs-lookup"><span data-stu-id="57dc2-108">Level</span></span>|<span data-ttu-id="57dc2-109">警告</span><span class="sxs-lookup"><span data-stu-id="57dc2-109">Warning</span></span>|  
|<span data-ttu-id="57dc2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="57dc2-110">Channel</span></span>|<span data-ttu-id="57dc2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="57dc2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="57dc2-112">説明</span><span class="sxs-lookup"><span data-stu-id="57dc2-112">Description</span></span>  
 <span data-ttu-id="57dc2-113">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="57dc2-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="57dc2-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="57dc2-114">Message</span></span>  
 <span data-ttu-id="57dc2-115">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="57dc2-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="57dc2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="57dc2-116">Details</span></span>  
  
|<span data-ttu-id="57dc2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="57dc2-117">Data Item Name</span></span>|<span data-ttu-id="57dc2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="57dc2-118">Data Item Type</span></span>|<span data-ttu-id="57dc2-119">説明</span><span class="sxs-lookup"><span data-stu-id="57dc2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="57dc2-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="57dc2-120">ErrorNumber</span></span>|<span data-ttu-id="57dc2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="57dc2-121">xs:string</span></span>|<span data-ttu-id="57dc2-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="57dc2-122">The SQL error number.</span></span>|  
|<span data-ttu-id="57dc2-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="57dc2-123">ExceptionMessage</span></span>|<span data-ttu-id="57dc2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="57dc2-124">xs:string</span></span>|<span data-ttu-id="57dc2-125">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="57dc2-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="57dc2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="57dc2-126">AppDomain</span></span>|<span data-ttu-id="57dc2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="57dc2-127">xs:string</span></span>|<span data-ttu-id="57dc2-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="57dc2-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
