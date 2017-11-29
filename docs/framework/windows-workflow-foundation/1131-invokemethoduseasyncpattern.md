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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f9f8f4e836d5c5b437edcfaff6460c7b97210ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="b0598-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="b0598-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="b0598-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b0598-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0598-104">ID</span><span class="sxs-lookup"><span data-stu-id="b0598-104">ID</span></span>|<span data-ttu-id="b0598-105">1131</span><span class="sxs-lookup"><span data-stu-id="b0598-105">1131</span></span>|  
|<span data-ttu-id="b0598-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b0598-106">Keywords</span></span>|<span data-ttu-id="b0598-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b0598-107">WFRuntime</span></span>|  
|<span data-ttu-id="b0598-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b0598-108">Level</span></span>|<span data-ttu-id="b0598-109">情報</span><span class="sxs-lookup"><span data-stu-id="b0598-109">Information</span></span>|  
|<span data-ttu-id="b0598-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b0598-110">Channel</span></span>|<span data-ttu-id="b0598-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="b0598-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b0598-112">説明</span><span class="sxs-lookup"><span data-stu-id="b0598-112">Description</span></span>  
 <span data-ttu-id="b0598-113">CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。</span><span class="sxs-lookup"><span data-stu-id="b0598-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b0598-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b0598-114">Message</span></span>  
 <span data-ttu-id="b0598-115">InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="b0598-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b0598-116">詳細</span><span class="sxs-lookup"><span data-stu-id="b0598-116">Details</span></span>  
  
|<span data-ttu-id="b0598-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b0598-117">Data Item Name</span></span>|<span data-ttu-id="b0598-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b0598-118">Data Item Type</span></span>|<span data-ttu-id="b0598-119">説明</span><span class="sxs-lookup"><span data-stu-id="b0598-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b0598-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b0598-120">InvokeMethod</span></span>|<span data-ttu-id="b0598-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0598-121">xs:string</span></span>|<span data-ttu-id="b0598-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="b0598-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b0598-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="b0598-123">BeginMethod</span></span>|<span data-ttu-id="b0598-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0598-124">xs:string</span></span>|<span data-ttu-id="b0598-125">begin メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="b0598-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="b0598-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="b0598-126">EndMethod</span></span>|<span data-ttu-id="b0598-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0598-127">xs:string</span></span>|<span data-ttu-id="b0598-128">end メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="b0598-128">The name of the end method.</span></span>|  
|<span data-ttu-id="b0598-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b0598-129">AppDomain</span></span>|<span data-ttu-id="b0598-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="b0598-130">xs:string</span></span>|<span data-ttu-id="b0598-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b0598-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
