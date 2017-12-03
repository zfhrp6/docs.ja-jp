---
title: 1124 - InvokeMethodIsStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce4d3948ed00c8f72c2a3e8967f7d88ab02d59d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="3b85e-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="3b85e-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="3b85e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3b85e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b85e-104">ID</span><span class="sxs-lookup"><span data-stu-id="3b85e-104">ID</span></span>|<span data-ttu-id="3b85e-105">1124</span><span class="sxs-lookup"><span data-stu-id="3b85e-105">1124</span></span>|  
|<span data-ttu-id="3b85e-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="3b85e-106">Keywords</span></span>|<span data-ttu-id="3b85e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3b85e-107">WFRuntime</span></span>|  
|<span data-ttu-id="3b85e-108">レベル</span><span class="sxs-lookup"><span data-stu-id="3b85e-108">Level</span></span>|<span data-ttu-id="3b85e-109">情報</span><span class="sxs-lookup"><span data-stu-id="3b85e-109">Information</span></span>|  
|<span data-ttu-id="3b85e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3b85e-110">Channel</span></span>|<span data-ttu-id="3b85e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3b85e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3b85e-112">説明</span><span class="sxs-lookup"><span data-stu-id="3b85e-112">Description</span></span>  
 <span data-ttu-id="3b85e-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="3b85e-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3b85e-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="3b85e-114">Message</span></span>  
 <span data-ttu-id="3b85e-115">InvokeMethod '%1' - メソッドは Static です。</span><span class="sxs-lookup"><span data-stu-id="3b85e-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3b85e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="3b85e-116">Details</span></span>  
  
|<span data-ttu-id="3b85e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3b85e-117">Data Item Name</span></span>|<span data-ttu-id="3b85e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3b85e-118">Data Item Type</span></span>|<span data-ttu-id="3b85e-119">説明</span><span class="sxs-lookup"><span data-stu-id="3b85e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3b85e-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="3b85e-120">InvokeMethod</span></span>|<span data-ttu-id="3b85e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3b85e-121">xs:string</span></span>|<span data-ttu-id="3b85e-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3b85e-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="3b85e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3b85e-123">AppDomain</span></span>|<span data-ttu-id="3b85e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3b85e-124">xs:string</span></span>|<span data-ttu-id="3b85e-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3b85e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
