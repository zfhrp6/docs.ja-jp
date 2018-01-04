---
title: 2578 - TryCatchExceptionFromCatchOrFinally
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 340f8fa140f44e4a85f9b19259dc0a9f49b9b08e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a><span data-ttu-id="eff62-102">2578 - TryCatchExceptionFromCatchOrFinally</span><span class="sxs-lookup"><span data-stu-id="eff62-102">2578 - TryCatchExceptionFromCatchOrFinally</span></span>
## <a name="properties"></a><span data-ttu-id="eff62-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="eff62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eff62-104">ID</span><span class="sxs-lookup"><span data-stu-id="eff62-104">ID</span></span>|<span data-ttu-id="eff62-105">2578</span><span class="sxs-lookup"><span data-stu-id="eff62-105">2578</span></span>|  
|<span data-ttu-id="eff62-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="eff62-106">Keywords</span></span>|<span data-ttu-id="eff62-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="eff62-107">WFActivities</span></span>|  
|<span data-ttu-id="eff62-108">レベル</span><span class="sxs-lookup"><span data-stu-id="eff62-108">Level</span></span>|<span data-ttu-id="eff62-109">警告</span><span class="sxs-lookup"><span data-stu-id="eff62-109">Warning</span></span>|  
|<span data-ttu-id="eff62-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="eff62-110">Channel</span></span>|<span data-ttu-id="eff62-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="eff62-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eff62-112">説明</span><span class="sxs-lookup"><span data-stu-id="eff62-112">Description</span></span>  
 <span data-ttu-id="eff62-113">Catch または Finally アクティビティから例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="eff62-113">Indicates a Catch or Finally activity has thrown an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eff62-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="eff62-114">Message</span></span>  
 <span data-ttu-id="eff62-115">TryCatch アクティビティ '%1' に関連付けられている Catch または Finally アクティビティは例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="eff62-115">A Catch or Finally activity that is associated with the TryCatch activity '%1' has thrown an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eff62-116">詳細</span><span class="sxs-lookup"><span data-stu-id="eff62-116">Details</span></span>  
  
|<span data-ttu-id="eff62-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="eff62-117">Data Item Name</span></span>|<span data-ttu-id="eff62-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="eff62-118">Data Item Type</span></span>|<span data-ttu-id="eff62-119">説明</span><span class="sxs-lookup"><span data-stu-id="eff62-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eff62-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="eff62-120">DisplayName</span></span>|<span data-ttu-id="eff62-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="eff62-121">xs:string</span></span>|<span data-ttu-id="eff62-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="eff62-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="eff62-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eff62-123">AppDomain</span></span>|<span data-ttu-id="eff62-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eff62-124">xs:string</span></span>|<span data-ttu-id="eff62-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="eff62-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
