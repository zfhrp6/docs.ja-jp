---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a1021d7d23b8e9c25684da567b769c24380a8a0a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="243eb-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="243eb-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="243eb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="243eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="243eb-104">ID</span><span class="sxs-lookup"><span data-stu-id="243eb-104">ID</span></span>|<span data-ttu-id="243eb-105">1126</span><span class="sxs-lookup"><span data-stu-id="243eb-105">1126</span></span>|  
|<span data-ttu-id="243eb-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="243eb-106">Keywords</span></span>|<span data-ttu-id="243eb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="243eb-107">WFRuntime</span></span>|  
|<span data-ttu-id="243eb-108">レベル</span><span class="sxs-lookup"><span data-stu-id="243eb-108">Level</span></span>|<span data-ttu-id="243eb-109">情報</span><span class="sxs-lookup"><span data-stu-id="243eb-109">Information</span></span>|  
|<span data-ttu-id="243eb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="243eb-110">Channel</span></span>|<span data-ttu-id="243eb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="243eb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="243eb-112">説明</span><span class="sxs-lookup"><span data-stu-id="243eb-112">Description</span></span>  
 <span data-ttu-id="243eb-113">InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="243eb-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="243eb-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="243eb-114">Message</span></span>  
 <span data-ttu-id="243eb-115">アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="243eb-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="243eb-116">%2</span><span class="sxs-lookup"><span data-stu-id="243eb-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="243eb-117">詳細</span><span class="sxs-lookup"><span data-stu-id="243eb-117">Details</span></span>  
  
|<span data-ttu-id="243eb-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="243eb-118">Data Item Name</span></span>|<span data-ttu-id="243eb-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="243eb-119">Data Item Type</span></span>|<span data-ttu-id="243eb-120">説明</span><span class="sxs-lookup"><span data-stu-id="243eb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="243eb-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="243eb-121">InvokeMethod</span></span>|<span data-ttu-id="243eb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="243eb-122">xs:string</span></span>|<span data-ttu-id="243eb-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="243eb-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="243eb-124">例外</span><span class="sxs-lookup"><span data-stu-id="243eb-124">Exception</span></span>|<span data-ttu-id="243eb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="243eb-125">xs:string</span></span>|<span data-ttu-id="243eb-126">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="243eb-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="243eb-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="243eb-127">AppDomain</span></span>|<span data-ttu-id="243eb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="243eb-128">xs:string</span></span>|<span data-ttu-id="243eb-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="243eb-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
