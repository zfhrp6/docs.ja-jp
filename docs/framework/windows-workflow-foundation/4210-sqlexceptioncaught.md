---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 2493014e80e79ac2935c1bcc685147a74e48fb47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512074"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="8ab0a-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="8ab0a-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="8ab0a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ab0a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ab0a-104">ID</span><span class="sxs-lookup"><span data-stu-id="8ab0a-104">ID</span></span>|<span data-ttu-id="8ab0a-105">4210</span><span class="sxs-lookup"><span data-stu-id="8ab0a-105">4210</span></span>|  
|<span data-ttu-id="8ab0a-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8ab0a-106">Keywords</span></span>|<span data-ttu-id="8ab0a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8ab0a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8ab0a-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8ab0a-108">Level</span></span>|<span data-ttu-id="8ab0a-109">警告</span><span class="sxs-lookup"><span data-stu-id="8ab0a-109">Warning</span></span>|  
|<span data-ttu-id="8ab0a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8ab0a-110">Channel</span></span>|<span data-ttu-id="8ab0a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8ab0a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ab0a-112">説明</span><span class="sxs-lookup"><span data-stu-id="8ab0a-112">Description</span></span>  
 <span data-ttu-id="8ab0a-113">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8ab0a-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ab0a-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8ab0a-114">Message</span></span>  
 <span data-ttu-id="8ab0a-115">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="8ab0a-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ab0a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8ab0a-116">Details</span></span>  
  
|<span data-ttu-id="8ab0a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8ab0a-117">Data Item Name</span></span>|<span data-ttu-id="8ab0a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8ab0a-118">Data Item Type</span></span>|<span data-ttu-id="8ab0a-119">説明</span><span class="sxs-lookup"><span data-stu-id="8ab0a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ab0a-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="8ab0a-120">ErrorNumber</span></span>|<span data-ttu-id="8ab0a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ab0a-121">xs:string</span></span>|<span data-ttu-id="8ab0a-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="8ab0a-122">The SQL error number.</span></span>|  
|<span data-ttu-id="8ab0a-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="8ab0a-123">ExceptionMessage</span></span>|<span data-ttu-id="8ab0a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ab0a-124">xs:string</span></span>|<span data-ttu-id="8ab0a-125">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="8ab0a-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="8ab0a-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8ab0a-126">AppDomain</span></span>|<span data-ttu-id="8ab0a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ab0a-127">xs:string</span></span>|<span data-ttu-id="8ab0a-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8ab0a-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
