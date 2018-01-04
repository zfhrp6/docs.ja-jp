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
ms.workload: dotnet
ms.openlocfilehash: 75386b56f7926b9ddb883e0ca212d795898fe6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="54980-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="54980-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="54980-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="54980-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54980-104">ID</span><span class="sxs-lookup"><span data-stu-id="54980-104">ID</span></span>|<span data-ttu-id="54980-105">1132</span><span class="sxs-lookup"><span data-stu-id="54980-105">1132</span></span>|  
|<span data-ttu-id="54980-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="54980-106">Keywords</span></span>|<span data-ttu-id="54980-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="54980-107">WFRuntime</span></span>|  
|<span data-ttu-id="54980-108">レベル</span><span class="sxs-lookup"><span data-stu-id="54980-108">Level</span></span>|<span data-ttu-id="54980-109">情報</span><span class="sxs-lookup"><span data-stu-id="54980-109">Information</span></span>|  
|<span data-ttu-id="54980-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="54980-110">Channel</span></span>|<span data-ttu-id="54980-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="54980-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54980-112">説明</span><span class="sxs-lookup"><span data-stu-id="54980-112">Description</span></span>  
 <span data-ttu-id="54980-113">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="54980-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54980-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="54980-114">Message</span></span>  
 <span data-ttu-id="54980-115">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="54980-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54980-116">詳細</span><span class="sxs-lookup"><span data-stu-id="54980-116">Details</span></span>  
  
|<span data-ttu-id="54980-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="54980-117">Data Item Name</span></span>|<span data-ttu-id="54980-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="54980-118">Data Item Type</span></span>|<span data-ttu-id="54980-119">説明</span><span class="sxs-lookup"><span data-stu-id="54980-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54980-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="54980-120">InvokeMethod</span></span>|<span data-ttu-id="54980-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="54980-121">xs:string</span></span>|<span data-ttu-id="54980-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="54980-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="54980-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54980-123">AppDomain</span></span>|<span data-ttu-id="54980-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="54980-124">xs:string</span></span>|<span data-ttu-id="54980-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="54980-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
