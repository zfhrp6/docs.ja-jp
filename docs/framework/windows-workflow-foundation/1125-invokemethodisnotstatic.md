---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="cb783-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="cb783-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="cb783-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cb783-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb783-104">ID</span><span class="sxs-lookup"><span data-stu-id="cb783-104">ID</span></span>|<span data-ttu-id="cb783-105">1125</span><span class="sxs-lookup"><span data-stu-id="cb783-105">1125</span></span>|  
|<span data-ttu-id="cb783-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="cb783-106">Keywords</span></span>|<span data-ttu-id="cb783-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cb783-107">WFRuntime</span></span>|  
|<span data-ttu-id="cb783-108">レベル</span><span class="sxs-lookup"><span data-stu-id="cb783-108">Level</span></span>|<span data-ttu-id="cb783-109">情報</span><span class="sxs-lookup"><span data-stu-id="cb783-109">Information</span></span>|  
|<span data-ttu-id="cb783-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="cb783-110">Channel</span></span>|<span data-ttu-id="cb783-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cb783-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb783-112">説明</span><span class="sxs-lookup"><span data-stu-id="cb783-112">Description</span></span>  
 <span data-ttu-id="cb783-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="cb783-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb783-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="cb783-114">Message</span></span>  
 <span data-ttu-id="cb783-115">InvokeMethod '%1' - メソッドは Static ではありません。</span><span class="sxs-lookup"><span data-stu-id="cb783-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb783-116">詳細</span><span class="sxs-lookup"><span data-stu-id="cb783-116">Details</span></span>  
  
|<span data-ttu-id="cb783-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cb783-117">Data Item Name</span></span>|<span data-ttu-id="cb783-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cb783-118">Data Item Type</span></span>|<span data-ttu-id="cb783-119">説明</span><span class="sxs-lookup"><span data-stu-id="cb783-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb783-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="cb783-120">InvokeMethod</span></span>|<span data-ttu-id="cb783-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb783-121">xs:string</span></span>|<span data-ttu-id="cb783-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="cb783-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="cb783-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cb783-123">AppDomain</span></span>|<span data-ttu-id="cb783-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cb783-124">xs:string</span></span>|<span data-ttu-id="cb783-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cb783-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
