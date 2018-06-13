---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511876"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="9ef24-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="9ef24-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="9ef24-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9ef24-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ef24-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ef24-104">ID</span></span>|<span data-ttu-id="9ef24-105">1132</span><span class="sxs-lookup"><span data-stu-id="9ef24-105">1132</span></span>|  
|<span data-ttu-id="9ef24-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="9ef24-106">Keywords</span></span>|<span data-ttu-id="9ef24-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ef24-107">WFRuntime</span></span>|  
|<span data-ttu-id="9ef24-108">レベル</span><span class="sxs-lookup"><span data-stu-id="9ef24-108">Level</span></span>|<span data-ttu-id="9ef24-109">情報</span><span class="sxs-lookup"><span data-stu-id="9ef24-109">Information</span></span>|  
|<span data-ttu-id="9ef24-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9ef24-110">Channel</span></span>|<span data-ttu-id="9ef24-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9ef24-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ef24-112">説明</span><span class="sxs-lookup"><span data-stu-id="9ef24-112">Description</span></span>  
 <span data-ttu-id="9ef24-113">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="9ef24-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ef24-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="9ef24-114">Message</span></span>  
 <span data-ttu-id="9ef24-115">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="9ef24-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ef24-116">詳細</span><span class="sxs-lookup"><span data-stu-id="9ef24-116">Details</span></span>  
  
|<span data-ttu-id="9ef24-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9ef24-117">Data Item Name</span></span>|<span data-ttu-id="9ef24-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9ef24-118">Data Item Type</span></span>|<span data-ttu-id="9ef24-119">説明</span><span class="sxs-lookup"><span data-stu-id="9ef24-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ef24-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9ef24-120">InvokeMethod</span></span>|<span data-ttu-id="9ef24-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef24-121">xs:string</span></span>|<span data-ttu-id="9ef24-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9ef24-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9ef24-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ef24-123">AppDomain</span></span>|<span data-ttu-id="9ef24-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ef24-124">xs:string</span></span>|<span data-ttu-id="9ef24-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9ef24-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
