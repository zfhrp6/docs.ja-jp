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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3fb3c780b80172db8770e717f517b97608fcb7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="c26f6-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="c26f6-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="c26f6-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c26f6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c26f6-104">ID</span><span class="sxs-lookup"><span data-stu-id="c26f6-104">ID</span></span>|<span data-ttu-id="c26f6-105">4210</span><span class="sxs-lookup"><span data-stu-id="c26f6-105">4210</span></span>|  
|<span data-ttu-id="c26f6-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c26f6-106">Keywords</span></span>|<span data-ttu-id="c26f6-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c26f6-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c26f6-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c26f6-108">Level</span></span>|<span data-ttu-id="c26f6-109">警告</span><span class="sxs-lookup"><span data-stu-id="c26f6-109">Warning</span></span>|  
|<span data-ttu-id="c26f6-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c26f6-110">Channel</span></span>|<span data-ttu-id="c26f6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c26f6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c26f6-112">説明</span><span class="sxs-lookup"><span data-stu-id="c26f6-112">Description</span></span>  
 <span data-ttu-id="c26f6-113">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c26f6-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c26f6-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c26f6-114">Message</span></span>  
 <span data-ttu-id="c26f6-115">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="c26f6-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c26f6-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c26f6-116">Details</span></span>  
  
|<span data-ttu-id="c26f6-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c26f6-117">Data Item Name</span></span>|<span data-ttu-id="c26f6-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c26f6-118">Data Item Type</span></span>|<span data-ttu-id="c26f6-119">説明</span><span class="sxs-lookup"><span data-stu-id="c26f6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c26f6-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="c26f6-120">ErrorNumber</span></span>|<span data-ttu-id="c26f6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c26f6-121">xs:string</span></span>|<span data-ttu-id="c26f6-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="c26f6-122">The SQL error number.</span></span>|  
|<span data-ttu-id="c26f6-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="c26f6-123">ExceptionMessage</span></span>|<span data-ttu-id="c26f6-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c26f6-124">xs:string</span></span>|<span data-ttu-id="c26f6-125">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="c26f6-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="c26f6-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c26f6-126">AppDomain</span></span>|<span data-ttu-id="c26f6-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c26f6-127">xs:string</span></span>|<span data-ttu-id="c26f6-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c26f6-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
