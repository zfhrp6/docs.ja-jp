---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="d04e3-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="d04e3-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="d04e3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d04e3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d04e3-104">ID</span><span class="sxs-lookup"><span data-stu-id="d04e3-104">ID</span></span>|<span data-ttu-id="d04e3-105">1132</span><span class="sxs-lookup"><span data-stu-id="d04e3-105">1132</span></span>|  
|<span data-ttu-id="d04e3-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d04e3-106">Keywords</span></span>|<span data-ttu-id="d04e3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d04e3-107">WFRuntime</span></span>|  
|<span data-ttu-id="d04e3-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d04e3-108">Level</span></span>|<span data-ttu-id="d04e3-109">情報</span><span class="sxs-lookup"><span data-stu-id="d04e3-109">Information</span></span>|  
|<span data-ttu-id="d04e3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d04e3-110">Channel</span></span>|<span data-ttu-id="d04e3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d04e3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d04e3-112">説明</span><span class="sxs-lookup"><span data-stu-id="d04e3-112">Description</span></span>  
 <span data-ttu-id="d04e3-113">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d04e3-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d04e3-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d04e3-114">Message</span></span>  
 <span data-ttu-id="d04e3-115">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="d04e3-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d04e3-116">詳細</span><span class="sxs-lookup"><span data-stu-id="d04e3-116">Details</span></span>  
  
|<span data-ttu-id="d04e3-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d04e3-117">Data Item Name</span></span>|<span data-ttu-id="d04e3-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d04e3-118">Data Item Type</span></span>|<span data-ttu-id="d04e3-119">説明</span><span class="sxs-lookup"><span data-stu-id="d04e3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d04e3-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d04e3-120">InvokeMethod</span></span>|<span data-ttu-id="d04e3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d04e3-121">xs:string</span></span>|<span data-ttu-id="d04e3-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d04e3-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d04e3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d04e3-123">AppDomain</span></span>|<span data-ttu-id="d04e3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d04e3-124">xs:string</span></span>|<span data-ttu-id="d04e3-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d04e3-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
