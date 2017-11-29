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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97a2f68ed921ccc251e1dc316d633d2520efc643
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="fd932-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="fd932-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="fd932-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fd932-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fd932-104">ID</span><span class="sxs-lookup"><span data-stu-id="fd932-104">ID</span></span>|<span data-ttu-id="fd932-105">4207</span><span class="sxs-lookup"><span data-stu-id="fd932-105">4207</span></span>|  
|<span data-ttu-id="fd932-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="fd932-106">Keywords</span></span>|<span data-ttu-id="fd932-107">クオータ、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="fd932-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="fd932-108">レベル</span><span class="sxs-lookup"><span data-stu-id="fd932-108">Level</span></span>|<span data-ttu-id="fd932-109">情報</span><span class="sxs-lookup"><span data-stu-id="fd932-109">Information</span></span>|  
|<span data-ttu-id="fd932-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="fd932-110">Channel</span></span>|<span data-ttu-id="fd932-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="fd932-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fd932-112">説明</span><span class="sxs-lookup"><span data-stu-id="fd932-112">Description</span></span>  
 <span data-ttu-id="fd932-113">再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fd932-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fd932-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="fd932-114">Message</span></span>  
 <span data-ttu-id="fd932-115">SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="fd932-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fd932-116">詳細</span><span class="sxs-lookup"><span data-stu-id="fd932-116">Details</span></span>  
  
|<span data-ttu-id="fd932-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="fd932-117">Data Item Name</span></span>|<span data-ttu-id="fd932-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="fd932-118">Data Item Type</span></span>|<span data-ttu-id="fd932-119">説明</span><span class="sxs-lookup"><span data-stu-id="fd932-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fd932-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fd932-120">AppDomain</span></span>|<span data-ttu-id="fd932-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="fd932-121">xs:string</span></span>|<span data-ttu-id="fd932-122">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="fd932-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
