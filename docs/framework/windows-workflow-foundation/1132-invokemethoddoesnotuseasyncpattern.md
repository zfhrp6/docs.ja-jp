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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="333fa-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="333fa-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="333fa-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="333fa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="333fa-104">ID</span><span class="sxs-lookup"><span data-stu-id="333fa-104">ID</span></span>|<span data-ttu-id="333fa-105">1132</span><span class="sxs-lookup"><span data-stu-id="333fa-105">1132</span></span>|  
|<span data-ttu-id="333fa-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="333fa-106">Keywords</span></span>|<span data-ttu-id="333fa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="333fa-107">WFRuntime</span></span>|  
|<span data-ttu-id="333fa-108">レベル</span><span class="sxs-lookup"><span data-stu-id="333fa-108">Level</span></span>|<span data-ttu-id="333fa-109">情報</span><span class="sxs-lookup"><span data-stu-id="333fa-109">Information</span></span>|  
|<span data-ttu-id="333fa-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="333fa-110">Channel</span></span>|<span data-ttu-id="333fa-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="333fa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="333fa-112">説明</span><span class="sxs-lookup"><span data-stu-id="333fa-112">Description</span></span>  
 <span data-ttu-id="333fa-113">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="333fa-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="333fa-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="333fa-114">Message</span></span>  
 <span data-ttu-id="333fa-115">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="333fa-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="333fa-116">詳細</span><span class="sxs-lookup"><span data-stu-id="333fa-116">Details</span></span>  
  
|<span data-ttu-id="333fa-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="333fa-117">Data Item Name</span></span>|<span data-ttu-id="333fa-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="333fa-118">Data Item Type</span></span>|<span data-ttu-id="333fa-119">説明</span><span class="sxs-lookup"><span data-stu-id="333fa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="333fa-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="333fa-120">InvokeMethod</span></span>|<span data-ttu-id="333fa-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="333fa-121">xs:string</span></span>|<span data-ttu-id="333fa-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="333fa-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="333fa-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="333fa-123">AppDomain</span></span>|<span data-ttu-id="333fa-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="333fa-124">xs:string</span></span>|<span data-ttu-id="333fa-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="333fa-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
