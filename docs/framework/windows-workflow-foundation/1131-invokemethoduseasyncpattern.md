---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512667"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="2f2be-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="2f2be-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="2f2be-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2f2be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f2be-104">ID</span><span class="sxs-lookup"><span data-stu-id="2f2be-104">ID</span></span>|<span data-ttu-id="2f2be-105">1131</span><span class="sxs-lookup"><span data-stu-id="2f2be-105">1131</span></span>|  
|<span data-ttu-id="2f2be-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2f2be-106">Keywords</span></span>|<span data-ttu-id="2f2be-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2f2be-107">WFRuntime</span></span>|  
|<span data-ttu-id="2f2be-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2f2be-108">Level</span></span>|<span data-ttu-id="2f2be-109">情報</span><span class="sxs-lookup"><span data-stu-id="2f2be-109">Information</span></span>|  
|<span data-ttu-id="2f2be-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2f2be-110">Channel</span></span>|<span data-ttu-id="2f2be-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2f2be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f2be-112">説明</span><span class="sxs-lookup"><span data-stu-id="2f2be-112">Description</span></span>  
 <span data-ttu-id="2f2be-113">CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。</span><span class="sxs-lookup"><span data-stu-id="2f2be-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f2be-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2f2be-114">Message</span></span>  
 <span data-ttu-id="2f2be-115">InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f2be-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f2be-116">詳細</span><span class="sxs-lookup"><span data-stu-id="2f2be-116">Details</span></span>  
  
|<span data-ttu-id="2f2be-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2f2be-117">Data Item Name</span></span>|<span data-ttu-id="2f2be-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2f2be-118">Data Item Type</span></span>|<span data-ttu-id="2f2be-119">説明</span><span class="sxs-lookup"><span data-stu-id="2f2be-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f2be-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="2f2be-120">InvokeMethod</span></span>|<span data-ttu-id="2f2be-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f2be-121">xs:string</span></span>|<span data-ttu-id="2f2be-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="2f2be-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="2f2be-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="2f2be-123">BeginMethod</span></span>|<span data-ttu-id="2f2be-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f2be-124">xs:string</span></span>|<span data-ttu-id="2f2be-125">begin メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2f2be-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="2f2be-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="2f2be-126">EndMethod</span></span>|<span data-ttu-id="2f2be-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f2be-127">xs:string</span></span>|<span data-ttu-id="2f2be-128">end メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="2f2be-128">The name of the end method.</span></span>|  
|<span data-ttu-id="2f2be-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2f2be-129">AppDomain</span></span>|<span data-ttu-id="2f2be-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="2f2be-130">xs:string</span></span>|<span data-ttu-id="2f2be-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2f2be-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
