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
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="90390-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="90390-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="90390-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="90390-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90390-104">ID</span><span class="sxs-lookup"><span data-stu-id="90390-104">ID</span></span>|<span data-ttu-id="90390-105">4208</span><span class="sxs-lookup"><span data-stu-id="90390-105">4208</span></span>|  
|<span data-ttu-id="90390-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="90390-106">Keywords</span></span>|<span data-ttu-id="90390-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="90390-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="90390-108">レベル</span><span class="sxs-lookup"><span data-stu-id="90390-108">Level</span></span>|<span data-ttu-id="90390-109">情報</span><span class="sxs-lookup"><span data-stu-id="90390-109">Information</span></span>|  
|<span data-ttu-id="90390-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="90390-110">Channel</span></span>|<span data-ttu-id="90390-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="90390-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90390-112">説明</span><span class="sxs-lookup"><span data-stu-id="90390-112">Description</span></span>  
 <span data-ttu-id="90390-113">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="90390-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="90390-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="90390-114">Message</span></span>  
 <span data-ttu-id="90390-115">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="90390-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="90390-116">詳細</span><span class="sxs-lookup"><span data-stu-id="90390-116">Details</span></span>  
  
|<span data-ttu-id="90390-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="90390-117">Data Item Name</span></span>|<span data-ttu-id="90390-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="90390-118">Data Item Type</span></span>|<span data-ttu-id="90390-119">説明</span><span class="sxs-lookup"><span data-stu-id="90390-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="90390-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="90390-120">ErrorNumber</span></span>|<span data-ttu-id="90390-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="90390-121">xs:string</span></span>|<span data-ttu-id="90390-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="90390-122">The SQL error number.</span></span>|  
|<span data-ttu-id="90390-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="90390-123">AppDomain</span></span>|<span data-ttu-id="90390-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="90390-124">xs:string</span></span>|<span data-ttu-id="90390-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="90390-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
