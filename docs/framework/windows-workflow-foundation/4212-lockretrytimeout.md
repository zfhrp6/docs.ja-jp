---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="0fd61-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="0fd61-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="0fd61-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0fd61-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fd61-104">ID</span><span class="sxs-lookup"><span data-stu-id="0fd61-104">ID</span></span>|<span data-ttu-id="0fd61-105">4212</span><span class="sxs-lookup"><span data-stu-id="0fd61-105">4212</span></span>|  
|<span data-ttu-id="0fd61-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="0fd61-106">Keywords</span></span>|<span data-ttu-id="0fd61-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0fd61-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0fd61-108">レベル</span><span class="sxs-lookup"><span data-stu-id="0fd61-108">Level</span></span>|<span data-ttu-id="0fd61-109">警告</span><span class="sxs-lookup"><span data-stu-id="0fd61-109">Warning</span></span>|  
|<span data-ttu-id="0fd61-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0fd61-110">Channel</span></span>|<span data-ttu-id="0fd61-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0fd61-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0fd61-112">説明</span><span class="sxs-lookup"><span data-stu-id="0fd61-112">Description</span></span>  
 <span data-ttu-id="0fd61-113">SQL プロバイダーはインスタンス ロックを取得しようとしてタイムアウトを検出しました。</span><span class="sxs-lookup"><span data-stu-id="0fd61-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0fd61-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="0fd61-114">Message</span></span>  
 <span data-ttu-id="0fd61-115">インスタンス ロックを取得しようとしてタイムアウトになりました。</span><span class="sxs-lookup"><span data-stu-id="0fd61-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="0fd61-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="0fd61-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="0fd61-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fd61-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0fd61-118">詳細</span><span class="sxs-lookup"><span data-stu-id="0fd61-118">Details</span></span>  
  
|<span data-ttu-id="0fd61-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0fd61-119">Data Item Name</span></span>|<span data-ttu-id="0fd61-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0fd61-120">Data Item Type</span></span>|<span data-ttu-id="0fd61-121">説明</span><span class="sxs-lookup"><span data-stu-id="0fd61-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0fd61-122">Delay</span><span class="sxs-lookup"><span data-stu-id="0fd61-122">Delay</span></span>|<span data-ttu-id="0fd61-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="0fd61-123">xs:string</span></span>|<span data-ttu-id="0fd61-124">再試行の遅延。</span><span class="sxs-lookup"><span data-stu-id="0fd61-124">The delay between retries.</span></span>|  
|<span data-ttu-id="0fd61-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0fd61-125">AppDomain</span></span>|<span data-ttu-id="0fd61-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="0fd61-126">xs:string</span></span>|<span data-ttu-id="0fd61-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0fd61-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
