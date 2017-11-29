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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22a798dabd2253d340d7fb3dffb9f95fc66d0a9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a><span data-ttu-id="f2cd5-102">2578 - TryCatchExceptionFromCatchOrFinally</span><span class="sxs-lookup"><span data-stu-id="f2cd5-102">2578 - TryCatchExceptionFromCatchOrFinally</span></span>
## <a name="properties"></a><span data-ttu-id="f2cd5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2cd5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2cd5-104">ID</span><span class="sxs-lookup"><span data-stu-id="f2cd5-104">ID</span></span>|<span data-ttu-id="f2cd5-105">2578</span><span class="sxs-lookup"><span data-stu-id="f2cd5-105">2578</span></span>|  
|<span data-ttu-id="f2cd5-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="f2cd5-106">Keywords</span></span>|<span data-ttu-id="f2cd5-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="f2cd5-107">WFActivities</span></span>|  
|<span data-ttu-id="f2cd5-108">レベル</span><span class="sxs-lookup"><span data-stu-id="f2cd5-108">Level</span></span>|<span data-ttu-id="f2cd5-109">警告</span><span class="sxs-lookup"><span data-stu-id="f2cd5-109">Warning</span></span>|  
|<span data-ttu-id="f2cd5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f2cd5-110">Channel</span></span>|<span data-ttu-id="f2cd5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f2cd5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2cd5-112">説明</span><span class="sxs-lookup"><span data-stu-id="f2cd5-112">Description</span></span>  
 <span data-ttu-id="f2cd5-113">Catch または Finally アクティビティから例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f2cd5-113">Indicates a Catch or Finally activity has thrown an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2cd5-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="f2cd5-114">Message</span></span>  
 <span data-ttu-id="f2cd5-115">TryCatch アクティビティ '%1' に関連付けられている Catch または Finally アクティビティは例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="f2cd5-115">A Catch or Finally activity that is associated with the TryCatch activity '%1' has thrown an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2cd5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f2cd5-116">Details</span></span>  
  
|<span data-ttu-id="f2cd5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f2cd5-117">Data Item Name</span></span>|<span data-ttu-id="f2cd5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f2cd5-118">Data Item Type</span></span>|<span data-ttu-id="f2cd5-119">説明</span><span class="sxs-lookup"><span data-stu-id="f2cd5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2cd5-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f2cd5-120">DisplayName</span></span>|<span data-ttu-id="f2cd5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f2cd5-121">xs:string</span></span>|<span data-ttu-id="f2cd5-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="f2cd5-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="f2cd5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f2cd5-123">AppDomain</span></span>|<span data-ttu-id="f2cd5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f2cd5-124">xs:string</span></span>|<span data-ttu-id="f2cd5-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f2cd5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
