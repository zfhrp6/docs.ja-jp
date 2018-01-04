---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 739357df85ceb73e246adcb2b09f88d270d853ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="bbe14-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="bbe14-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="bbe14-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bbe14-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bbe14-104">ID</span><span class="sxs-lookup"><span data-stu-id="bbe14-104">ID</span></span>|<span data-ttu-id="bbe14-105">1131</span><span class="sxs-lookup"><span data-stu-id="bbe14-105">1131</span></span>|  
|<span data-ttu-id="bbe14-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bbe14-106">Keywords</span></span>|<span data-ttu-id="bbe14-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bbe14-107">WFRuntime</span></span>|  
|<span data-ttu-id="bbe14-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bbe14-108">Level</span></span>|<span data-ttu-id="bbe14-109">情報</span><span class="sxs-lookup"><span data-stu-id="bbe14-109">Information</span></span>|  
|<span data-ttu-id="bbe14-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bbe14-110">Channel</span></span>|<span data-ttu-id="bbe14-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bbe14-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bbe14-112">説明</span><span class="sxs-lookup"><span data-stu-id="bbe14-112">Description</span></span>  
 <span data-ttu-id="bbe14-113">CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。</span><span class="sxs-lookup"><span data-stu-id="bbe14-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bbe14-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bbe14-114">Message</span></span>  
 <span data-ttu-id="bbe14-115">InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="bbe14-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bbe14-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bbe14-116">Details</span></span>  
  
|<span data-ttu-id="bbe14-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bbe14-117">Data Item Name</span></span>|<span data-ttu-id="bbe14-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bbe14-118">Data Item Type</span></span>|<span data-ttu-id="bbe14-119">説明</span><span class="sxs-lookup"><span data-stu-id="bbe14-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bbe14-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="bbe14-120">InvokeMethod</span></span>|<span data-ttu-id="bbe14-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bbe14-121">xs:string</span></span>|<span data-ttu-id="bbe14-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bbe14-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="bbe14-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="bbe14-123">BeginMethod</span></span>|<span data-ttu-id="bbe14-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bbe14-124">xs:string</span></span>|<span data-ttu-id="bbe14-125">begin メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="bbe14-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="bbe14-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="bbe14-126">EndMethod</span></span>|<span data-ttu-id="bbe14-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bbe14-127">xs:string</span></span>|<span data-ttu-id="bbe14-128">end メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="bbe14-128">The name of the end method.</span></span>|  
|<span data-ttu-id="bbe14-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bbe14-129">AppDomain</span></span>|<span data-ttu-id="bbe14-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bbe14-130">xs:string</span></span>|<span data-ttu-id="bbe14-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bbe14-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
