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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 934c2947e86b429e9b990c273f22c0511f209a53
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="d5920-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="d5920-102">1125 - InvokeMethodIsNotStatic</span></span>
## <a name="properties"></a><span data-ttu-id="d5920-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d5920-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5920-104">ID</span><span class="sxs-lookup"><span data-stu-id="d5920-104">ID</span></span>|<span data-ttu-id="d5920-105">1125</span><span class="sxs-lookup"><span data-stu-id="d5920-105">1125</span></span>|  
|<span data-ttu-id="d5920-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d5920-106">Keywords</span></span>|<span data-ttu-id="d5920-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d5920-107">WFRuntime</span></span>|  
|<span data-ttu-id="d5920-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d5920-108">Level</span></span>|<span data-ttu-id="d5920-109">情報</span><span class="sxs-lookup"><span data-stu-id="d5920-109">Information</span></span>|  
|<span data-ttu-id="d5920-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d5920-110">Channel</span></span>|<span data-ttu-id="d5920-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d5920-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5920-112">説明</span><span class="sxs-lookup"><span data-stu-id="d5920-112">Description</span></span>  
 <span data-ttu-id="d5920-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="d5920-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d5920-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d5920-114">Message</span></span>  
 <span data-ttu-id="d5920-115">InvokeMethod '%1' - メソッドは Static ではありません。</span><span class="sxs-lookup"><span data-stu-id="d5920-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d5920-116">詳細</span><span class="sxs-lookup"><span data-stu-id="d5920-116">Details</span></span>  
  
|<span data-ttu-id="d5920-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d5920-117">Data Item Name</span></span>|<span data-ttu-id="d5920-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d5920-118">Data Item Type</span></span>|<span data-ttu-id="d5920-119">説明</span><span class="sxs-lookup"><span data-stu-id="d5920-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d5920-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d5920-120">InvokeMethod</span></span>|<span data-ttu-id="d5920-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5920-121">xs:string</span></span>|<span data-ttu-id="d5920-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d5920-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d5920-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d5920-123">AppDomain</span></span>|<span data-ttu-id="d5920-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d5920-124">xs:string</span></span>|<span data-ttu-id="d5920-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d5920-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
