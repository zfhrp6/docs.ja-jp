---
title: 4206 - UnlockInstanceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe33e52a67578e42ad9d28adfa2067e8830ab73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="0d1ec-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="0d1ec-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="0d1ec-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0d1ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d1ec-104">ID</span><span class="sxs-lookup"><span data-stu-id="0d1ec-104">ID</span></span>|<span data-ttu-id="0d1ec-105">4206</span><span class="sxs-lookup"><span data-stu-id="0d1ec-105">4206</span></span>|  
|<span data-ttu-id="0d1ec-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="0d1ec-106">Keywords</span></span>|<span data-ttu-id="0d1ec-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0d1ec-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0d1ec-108">レベル</span><span class="sxs-lookup"><span data-stu-id="0d1ec-108">Level</span></span>|<span data-ttu-id="0d1ec-109">Error</span><span class="sxs-lookup"><span data-stu-id="0d1ec-109">Error</span></span>|  
|<span data-ttu-id="0d1ec-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0d1ec-110">Channel</span></span>|<span data-ttu-id="0d1ec-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0d1ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d1ec-112">説明</span><span class="sxs-lookup"><span data-stu-id="0d1ec-112">Description</span></span>  
 <span data-ttu-id="0d1ec-113">インスタンスのロックを解除しようとしているときに例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0d1ec-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d1ec-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="0d1ec-114">Message</span></span>  
 <span data-ttu-id="0d1ec-115">インスタンスのロックを解除しようとして、例外 %1 が発生しました。</span><span class="sxs-lookup"><span data-stu-id="0d1ec-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d1ec-116">詳細</span><span class="sxs-lookup"><span data-stu-id="0d1ec-116">Details</span></span>  
  
|<span data-ttu-id="0d1ec-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0d1ec-117">Data Item Name</span></span>|<span data-ttu-id="0d1ec-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0d1ec-118">Data Item Type</span></span>|<span data-ttu-id="0d1ec-119">説明</span><span class="sxs-lookup"><span data-stu-id="0d1ec-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d1ec-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="0d1ec-120">ExceptionMessage</span></span>|<span data-ttu-id="0d1ec-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d1ec-121">xs:string</span></span>|<span data-ttu-id="0d1ec-122">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="0d1ec-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="0d1ec-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d1ec-123">AppDomain</span></span>|<span data-ttu-id="0d1ec-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0d1ec-124">xs:string</span></span>|<span data-ttu-id="0d1ec-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0d1ec-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
