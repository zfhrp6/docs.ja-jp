---
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="9cf49-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="9cf49-102">1124 - InvokeMethodIsStatic</span></span>
## <a name="properties"></a><span data-ttu-id="9cf49-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9cf49-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cf49-104">ID</span><span class="sxs-lookup"><span data-stu-id="9cf49-104">ID</span></span>|<span data-ttu-id="9cf49-105">1124</span><span class="sxs-lookup"><span data-stu-id="9cf49-105">1124</span></span>|  
|<span data-ttu-id="9cf49-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="9cf49-106">Keywords</span></span>|<span data-ttu-id="9cf49-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9cf49-107">WFRuntime</span></span>|  
|<span data-ttu-id="9cf49-108">レベル</span><span class="sxs-lookup"><span data-stu-id="9cf49-108">Level</span></span>|<span data-ttu-id="9cf49-109">情報</span><span class="sxs-lookup"><span data-stu-id="9cf49-109">Information</span></span>|  
|<span data-ttu-id="9cf49-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9cf49-110">Channel</span></span>|<span data-ttu-id="9cf49-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9cf49-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cf49-112">説明</span><span class="sxs-lookup"><span data-stu-id="9cf49-112">Description</span></span>  
 <span data-ttu-id="9cf49-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="9cf49-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cf49-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="9cf49-114">Message</span></span>  
 <span data-ttu-id="9cf49-115">InvokeMethod '%1' - メソッドは Static です。</span><span class="sxs-lookup"><span data-stu-id="9cf49-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cf49-116">詳細</span><span class="sxs-lookup"><span data-stu-id="9cf49-116">Details</span></span>  
  
|<span data-ttu-id="9cf49-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9cf49-117">Data Item Name</span></span>|<span data-ttu-id="9cf49-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9cf49-118">Data Item Type</span></span>|<span data-ttu-id="9cf49-119">説明</span><span class="sxs-lookup"><span data-stu-id="9cf49-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cf49-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9cf49-120">InvokeMethod</span></span>|<span data-ttu-id="9cf49-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9cf49-121">xs:string</span></span>|<span data-ttu-id="9cf49-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9cf49-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9cf49-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cf49-123">AppDomain</span></span>|<span data-ttu-id="9cf49-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9cf49-124">xs:string</span></span>|<span data-ttu-id="9cf49-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9cf49-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
