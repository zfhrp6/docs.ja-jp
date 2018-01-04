---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="44dda-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="44dda-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="44dda-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="44dda-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44dda-104">ID</span><span class="sxs-lookup"><span data-stu-id="44dda-104">ID</span></span>|<span data-ttu-id="44dda-105">4208</span><span class="sxs-lookup"><span data-stu-id="44dda-105">4208</span></span>|  
|<span data-ttu-id="44dda-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="44dda-106">Keywords</span></span>|<span data-ttu-id="44dda-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="44dda-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="44dda-108">レベル</span><span class="sxs-lookup"><span data-stu-id="44dda-108">Level</span></span>|<span data-ttu-id="44dda-109">情報</span><span class="sxs-lookup"><span data-stu-id="44dda-109">Information</span></span>|  
|<span data-ttu-id="44dda-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="44dda-110">Channel</span></span>|<span data-ttu-id="44dda-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="44dda-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44dda-112">説明</span><span class="sxs-lookup"><span data-stu-id="44dda-112">Description</span></span>  
 <span data-ttu-id="44dda-113">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="44dda-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44dda-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="44dda-114">Message</span></span>  
 <span data-ttu-id="44dda-115">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="44dda-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44dda-116">詳細</span><span class="sxs-lookup"><span data-stu-id="44dda-116">Details</span></span>  
  
|<span data-ttu-id="44dda-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="44dda-117">Data Item Name</span></span>|<span data-ttu-id="44dda-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="44dda-118">Data Item Type</span></span>|<span data-ttu-id="44dda-119">説明</span><span class="sxs-lookup"><span data-stu-id="44dda-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44dda-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="44dda-120">ErrorNumber</span></span>|<span data-ttu-id="44dda-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="44dda-121">xs:string</span></span>|<span data-ttu-id="44dda-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="44dda-122">The SQL error number.</span></span>|  
|<span data-ttu-id="44dda-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44dda-123">AppDomain</span></span>|<span data-ttu-id="44dda-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="44dda-124">xs:string</span></span>|<span data-ttu-id="44dda-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="44dda-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
