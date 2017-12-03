---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1708cba44a4afc22635a039f7868a9ffbf41fc37
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="2315e-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="2315e-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="2315e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2315e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2315e-104">ID</span><span class="sxs-lookup"><span data-stu-id="2315e-104">ID</span></span>|<span data-ttu-id="2315e-105">4207</span><span class="sxs-lookup"><span data-stu-id="2315e-105">4207</span></span>|  
|<span data-ttu-id="2315e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2315e-106">Keywords</span></span>|<span data-ttu-id="2315e-107">クオータ、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="2315e-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="2315e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2315e-108">Level</span></span>|<span data-ttu-id="2315e-109">情報</span><span class="sxs-lookup"><span data-stu-id="2315e-109">Information</span></span>|  
|<span data-ttu-id="2315e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2315e-110">Channel</span></span>|<span data-ttu-id="2315e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2315e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2315e-112">説明</span><span class="sxs-lookup"><span data-stu-id="2315e-112">Description</span></span>  
 <span data-ttu-id="2315e-113">再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="2315e-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2315e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2315e-114">Message</span></span>  
 <span data-ttu-id="2315e-115">SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="2315e-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2315e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2315e-116">Details</span></span>  
  
|<span data-ttu-id="2315e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2315e-117">Data Item Name</span></span>|<span data-ttu-id="2315e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2315e-118">Data Item Type</span></span>|<span data-ttu-id="2315e-119">説明</span><span class="sxs-lookup"><span data-stu-id="2315e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2315e-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2315e-120">AppDomain</span></span>|<span data-ttu-id="2315e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2315e-121">xs:string</span></span>|<span data-ttu-id="2315e-122">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2315e-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
