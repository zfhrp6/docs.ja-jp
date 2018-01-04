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
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="18f59-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="18f59-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="18f59-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="18f59-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18f59-104">ID</span><span class="sxs-lookup"><span data-stu-id="18f59-104">ID</span></span>|<span data-ttu-id="18f59-105">1126</span><span class="sxs-lookup"><span data-stu-id="18f59-105">1126</span></span>|  
|<span data-ttu-id="18f59-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="18f59-106">Keywords</span></span>|<span data-ttu-id="18f59-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="18f59-107">WFRuntime</span></span>|  
|<span data-ttu-id="18f59-108">レベル</span><span class="sxs-lookup"><span data-stu-id="18f59-108">Level</span></span>|<span data-ttu-id="18f59-109">情報</span><span class="sxs-lookup"><span data-stu-id="18f59-109">Information</span></span>|  
|<span data-ttu-id="18f59-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="18f59-110">Channel</span></span>|<span data-ttu-id="18f59-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="18f59-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="18f59-112">説明</span><span class="sxs-lookup"><span data-stu-id="18f59-112">Description</span></span>  
 <span data-ttu-id="18f59-113">InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="18f59-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="18f59-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="18f59-114">Message</span></span>  
 <span data-ttu-id="18f59-115">アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="18f59-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="18f59-116">%2</span><span class="sxs-lookup"><span data-stu-id="18f59-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="18f59-117">詳細</span><span class="sxs-lookup"><span data-stu-id="18f59-117">Details</span></span>  
  
|<span data-ttu-id="18f59-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="18f59-118">Data Item Name</span></span>|<span data-ttu-id="18f59-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="18f59-119">Data Item Type</span></span>|<span data-ttu-id="18f59-120">説明</span><span class="sxs-lookup"><span data-stu-id="18f59-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="18f59-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="18f59-121">InvokeMethod</span></span>|<span data-ttu-id="18f59-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="18f59-122">xs:string</span></span>|<span data-ttu-id="18f59-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="18f59-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="18f59-124">例外</span><span class="sxs-lookup"><span data-stu-id="18f59-124">Exception</span></span>|<span data-ttu-id="18f59-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="18f59-125">xs:string</span></span>|<span data-ttu-id="18f59-126">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="18f59-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="18f59-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="18f59-127">AppDomain</span></span>|<span data-ttu-id="18f59-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="18f59-128">xs:string</span></span>|<span data-ttu-id="18f59-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="18f59-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
