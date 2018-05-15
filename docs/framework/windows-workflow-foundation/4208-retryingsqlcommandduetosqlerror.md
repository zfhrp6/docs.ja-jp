---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="77aa3-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="77aa3-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="77aa3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="77aa3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77aa3-104">ID</span><span class="sxs-lookup"><span data-stu-id="77aa3-104">ID</span></span>|<span data-ttu-id="77aa3-105">4208</span><span class="sxs-lookup"><span data-stu-id="77aa3-105">4208</span></span>|  
|<span data-ttu-id="77aa3-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="77aa3-106">Keywords</span></span>|<span data-ttu-id="77aa3-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="77aa3-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="77aa3-108">レベル</span><span class="sxs-lookup"><span data-stu-id="77aa3-108">Level</span></span>|<span data-ttu-id="77aa3-109">情報</span><span class="sxs-lookup"><span data-stu-id="77aa3-109">Information</span></span>|  
|<span data-ttu-id="77aa3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="77aa3-110">Channel</span></span>|<span data-ttu-id="77aa3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="77aa3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77aa3-112">説明</span><span class="sxs-lookup"><span data-stu-id="77aa3-112">Description</span></span>  
 <span data-ttu-id="77aa3-113">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="77aa3-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77aa3-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="77aa3-114">Message</span></span>  
 <span data-ttu-id="77aa3-115">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="77aa3-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="77aa3-116">詳細</span><span class="sxs-lookup"><span data-stu-id="77aa3-116">Details</span></span>  
  
|<span data-ttu-id="77aa3-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="77aa3-117">Data Item Name</span></span>|<span data-ttu-id="77aa3-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="77aa3-118">Data Item Type</span></span>|<span data-ttu-id="77aa3-119">説明</span><span class="sxs-lookup"><span data-stu-id="77aa3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77aa3-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="77aa3-120">ErrorNumber</span></span>|<span data-ttu-id="77aa3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="77aa3-121">xs:string</span></span>|<span data-ttu-id="77aa3-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="77aa3-122">The SQL error number.</span></span>|  
|<span data-ttu-id="77aa3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="77aa3-123">AppDomain</span></span>|<span data-ttu-id="77aa3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="77aa3-124">xs:string</span></span>|<span data-ttu-id="77aa3-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="77aa3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
