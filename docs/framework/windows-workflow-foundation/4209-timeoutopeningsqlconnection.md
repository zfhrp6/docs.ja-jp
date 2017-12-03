---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="516e4-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="516e4-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="516e4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="516e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="516e4-104">ID</span><span class="sxs-lookup"><span data-stu-id="516e4-104">ID</span></span>|<span data-ttu-id="516e4-105">4209</span><span class="sxs-lookup"><span data-stu-id="516e4-105">4209</span></span>|  
|<span data-ttu-id="516e4-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="516e4-106">Keywords</span></span>|<span data-ttu-id="516e4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="516e4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="516e4-108">レベル</span><span class="sxs-lookup"><span data-stu-id="516e4-108">Level</span></span>|<span data-ttu-id="516e4-109">Error</span><span class="sxs-lookup"><span data-stu-id="516e4-109">Error</span></span>|  
|<span data-ttu-id="516e4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="516e4-110">Channel</span></span>|<span data-ttu-id="516e4-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="516e4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="516e4-112">説明</span><span class="sxs-lookup"><span data-stu-id="516e4-112">Description</span></span>  
 <span data-ttu-id="516e4-113">SQL 接続を開こうとしてタイムアウトが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="516e4-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="516e4-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="516e4-114">Message</span></span>  
 <span data-ttu-id="516e4-115">SQL 接続を開こうとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="516e4-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="516e4-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="516e4-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="516e4-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="516e4-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="516e4-118">詳細</span><span class="sxs-lookup"><span data-stu-id="516e4-118">Details</span></span>  
  
|<span data-ttu-id="516e4-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="516e4-119">Data Item Name</span></span>|<span data-ttu-id="516e4-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="516e4-120">Data Item Type</span></span>|<span data-ttu-id="516e4-121">説明</span><span class="sxs-lookup"><span data-stu-id="516e4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="516e4-122">Timeout</span><span class="sxs-lookup"><span data-stu-id="516e4-122">Timeout</span></span>|<span data-ttu-id="516e4-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="516e4-123">xs:string</span></span>|<span data-ttu-id="516e4-124">SQL 接続を開く場合のタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="516e4-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="516e4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="516e4-125">AppDomain</span></span>|<span data-ttu-id="516e4-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="516e4-126">xs:string</span></span>|<span data-ttu-id="516e4-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="516e4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
