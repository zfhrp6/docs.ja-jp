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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01db76802b96bd32e8a01cf86b1e682defe97a06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="137c4-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="137c4-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="137c4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="137c4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="137c4-104">ID</span><span class="sxs-lookup"><span data-stu-id="137c4-104">ID</span></span>|<span data-ttu-id="137c4-105">4208</span><span class="sxs-lookup"><span data-stu-id="137c4-105">4208</span></span>|  
|<span data-ttu-id="137c4-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="137c4-106">Keywords</span></span>|<span data-ttu-id="137c4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="137c4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="137c4-108">レベル</span><span class="sxs-lookup"><span data-stu-id="137c4-108">Level</span></span>|<span data-ttu-id="137c4-109">情報</span><span class="sxs-lookup"><span data-stu-id="137c4-109">Information</span></span>|  
|<span data-ttu-id="137c4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="137c4-110">Channel</span></span>|<span data-ttu-id="137c4-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="137c4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="137c4-112">説明</span><span class="sxs-lookup"><span data-stu-id="137c4-112">Description</span></span>  
 <span data-ttu-id="137c4-113">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="137c4-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="137c4-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="137c4-114">Message</span></span>  
 <span data-ttu-id="137c4-115">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="137c4-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="137c4-116">詳細</span><span class="sxs-lookup"><span data-stu-id="137c4-116">Details</span></span>  
  
|<span data-ttu-id="137c4-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="137c4-117">Data Item Name</span></span>|<span data-ttu-id="137c4-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="137c4-118">Data Item Type</span></span>|<span data-ttu-id="137c4-119">説明</span><span class="sxs-lookup"><span data-stu-id="137c4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="137c4-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="137c4-120">ErrorNumber</span></span>|<span data-ttu-id="137c4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="137c4-121">xs:string</span></span>|<span data-ttu-id="137c4-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="137c4-122">The SQL error number.</span></span>|  
|<span data-ttu-id="137c4-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="137c4-123">AppDomain</span></span>|<span data-ttu-id="137c4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="137c4-124">xs:string</span></span>|<span data-ttu-id="137c4-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="137c4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
