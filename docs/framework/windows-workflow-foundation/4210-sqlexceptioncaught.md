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
ms.openlocfilehash: 7857bb865bb8eea8fc9d1d56c1b6e69c33f7165d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="856c5-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="856c5-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="856c5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="856c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="856c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="856c5-104">ID</span></span>|<span data-ttu-id="856c5-105">4210</span><span class="sxs-lookup"><span data-stu-id="856c5-105">4210</span></span>|  
|<span data-ttu-id="856c5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="856c5-106">Keywords</span></span>|<span data-ttu-id="856c5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="856c5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="856c5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="856c5-108">Level</span></span>|<span data-ttu-id="856c5-109">警告</span><span class="sxs-lookup"><span data-stu-id="856c5-109">Warning</span></span>|  
|<span data-ttu-id="856c5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="856c5-110">Channel</span></span>|<span data-ttu-id="856c5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="856c5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="856c5-112">説明</span><span class="sxs-lookup"><span data-stu-id="856c5-112">Description</span></span>  
 <span data-ttu-id="856c5-113">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="856c5-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="856c5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="856c5-114">Message</span></span>  
 <span data-ttu-id="856c5-115">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="856c5-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="856c5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="856c5-116">Details</span></span>  
  
|<span data-ttu-id="856c5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="856c5-117">Data Item Name</span></span>|<span data-ttu-id="856c5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="856c5-118">Data Item Type</span></span>|<span data-ttu-id="856c5-119">説明</span><span class="sxs-lookup"><span data-stu-id="856c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="856c5-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="856c5-120">ErrorNumber</span></span>|<span data-ttu-id="856c5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="856c5-121">xs:string</span></span>|<span data-ttu-id="856c5-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="856c5-122">The SQL error number.</span></span>|  
|<span data-ttu-id="856c5-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="856c5-123">ExceptionMessage</span></span>|<span data-ttu-id="856c5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="856c5-124">xs:string</span></span>|<span data-ttu-id="856c5-125">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="856c5-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="856c5-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="856c5-126">AppDomain</span></span>|<span data-ttu-id="856c5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="856c5-127">xs:string</span></span>|<span data-ttu-id="856c5-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="856c5-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
