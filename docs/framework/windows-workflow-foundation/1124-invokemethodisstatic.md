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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4fbeeb37813d4e387fc976b50f22809f7ead8926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="d9b65-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="d9b65-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="d9b65-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d9b65-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9b65-104">ID</span><span class="sxs-lookup"><span data-stu-id="d9b65-104">ID</span></span>|<span data-ttu-id="d9b65-105">1124</span><span class="sxs-lookup"><span data-stu-id="d9b65-105">1124</span></span>|  
|<span data-ttu-id="d9b65-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="d9b65-106">Keywords</span></span>|<span data-ttu-id="d9b65-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d9b65-107">WFRuntime</span></span>|  
|<span data-ttu-id="d9b65-108">レベル</span><span class="sxs-lookup"><span data-stu-id="d9b65-108">Level</span></span>|<span data-ttu-id="d9b65-109">情報</span><span class="sxs-lookup"><span data-stu-id="d9b65-109">Information</span></span>|  
|<span data-ttu-id="d9b65-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d9b65-110">Channel</span></span>|<span data-ttu-id="d9b65-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d9b65-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d9b65-112">説明</span><span class="sxs-lookup"><span data-stu-id="d9b65-112">Description</span></span>  
 <span data-ttu-id="d9b65-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9b65-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d9b65-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="d9b65-114">Message</span></span>  
 <span data-ttu-id="d9b65-115">InvokeMethod '%1' - メソッドは Static です。</span><span class="sxs-lookup"><span data-stu-id="d9b65-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d9b65-116">詳細</span><span class="sxs-lookup"><span data-stu-id="d9b65-116">Details</span></span>  
  
|<span data-ttu-id="d9b65-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d9b65-117">Data Item Name</span></span>|<span data-ttu-id="d9b65-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d9b65-118">Data Item Type</span></span>|<span data-ttu-id="d9b65-119">説明</span><span class="sxs-lookup"><span data-stu-id="d9b65-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d9b65-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="d9b65-120">InvokeMethod</span></span>|<span data-ttu-id="d9b65-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9b65-121">xs:string</span></span>|<span data-ttu-id="d9b65-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d9b65-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="d9b65-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d9b65-123">AppDomain</span></span>|<span data-ttu-id="d9b65-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d9b65-124">xs:string</span></span>|<span data-ttu-id="d9b65-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d9b65-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
