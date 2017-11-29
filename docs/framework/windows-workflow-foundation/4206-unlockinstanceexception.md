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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 349844edb44e547a666f10c8d210d120ebf5a39f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="bdcdc-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="bdcdc-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="bdcdc-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bdcdc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bdcdc-104">ID</span><span class="sxs-lookup"><span data-stu-id="bdcdc-104">ID</span></span>|<span data-ttu-id="bdcdc-105">4206</span><span class="sxs-lookup"><span data-stu-id="bdcdc-105">4206</span></span>|  
|<span data-ttu-id="bdcdc-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bdcdc-106">Keywords</span></span>|<span data-ttu-id="bdcdc-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="bdcdc-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="bdcdc-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bdcdc-108">Level</span></span>|<span data-ttu-id="bdcdc-109">Error</span><span class="sxs-lookup"><span data-stu-id="bdcdc-109">Error</span></span>|  
|<span data-ttu-id="bdcdc-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bdcdc-110">Channel</span></span>|<span data-ttu-id="bdcdc-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bdcdc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bdcdc-112">説明</span><span class="sxs-lookup"><span data-stu-id="bdcdc-112">Description</span></span>  
 <span data-ttu-id="bdcdc-113">インスタンスのロックを解除しようとしているときに例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="bdcdc-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bdcdc-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bdcdc-114">Message</span></span>  
 <span data-ttu-id="bdcdc-115">インスタンスのロックを解除しようとして、例外 %1 が発生しました。</span><span class="sxs-lookup"><span data-stu-id="bdcdc-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bdcdc-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bdcdc-116">Details</span></span>  
  
|<span data-ttu-id="bdcdc-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bdcdc-117">Data Item Name</span></span>|<span data-ttu-id="bdcdc-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bdcdc-118">Data Item Type</span></span>|<span data-ttu-id="bdcdc-119">説明</span><span class="sxs-lookup"><span data-stu-id="bdcdc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bdcdc-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="bdcdc-120">ExceptionMessage</span></span>|<span data-ttu-id="bdcdc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcdc-121">xs:string</span></span>|<span data-ttu-id="bdcdc-122">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="bdcdc-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="bdcdc-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bdcdc-123">AppDomain</span></span>|<span data-ttu-id="bdcdc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bdcdc-124">xs:string</span></span>|<span data-ttu-id="bdcdc-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bdcdc-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
