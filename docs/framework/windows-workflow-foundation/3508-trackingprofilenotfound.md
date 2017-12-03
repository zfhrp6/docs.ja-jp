---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="b59eb-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="b59eb-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="b59eb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b59eb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b59eb-104">ID</span><span class="sxs-lookup"><span data-stu-id="b59eb-104">ID</span></span>|<span data-ttu-id="b59eb-105">3508</span><span class="sxs-lookup"><span data-stu-id="b59eb-105">3508</span></span>|  
|<span data-ttu-id="b59eb-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="b59eb-106">Keywords</span></span>|<span data-ttu-id="b59eb-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b59eb-107">WFServices</span></span>|  
|<span data-ttu-id="b59eb-108">レベル</span><span class="sxs-lookup"><span data-stu-id="b59eb-108">Level</span></span>|<span data-ttu-id="b59eb-109">詳細</span><span class="sxs-lookup"><span data-stu-id="b59eb-109">Verbose</span></span>|  
|<span data-ttu-id="b59eb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b59eb-110">Channel</span></span>|<span data-ttu-id="b59eb-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b59eb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b59eb-112">説明</span><span class="sxs-lookup"><span data-stu-id="b59eb-112">Description</span></span>  
 <span data-ttu-id="b59eb-113">構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b59eb-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b59eb-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b59eb-114">Message</span></span>  
 <span data-ttu-id="b59eb-115">ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="b59eb-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="b59eb-116">config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。</span><span class="sxs-lookup"><span data-stu-id="b59eb-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b59eb-117">詳細</span><span class="sxs-lookup"><span data-stu-id="b59eb-117">Details</span></span>  
  
|<span data-ttu-id="b59eb-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b59eb-118">Data Item Name</span></span>|<span data-ttu-id="b59eb-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b59eb-119">Data Item Type</span></span>|<span data-ttu-id="b59eb-120">説明</span><span class="sxs-lookup"><span data-stu-id="b59eb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b59eb-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="b59eb-121">TrackingProfile</span></span>|<span data-ttu-id="b59eb-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b59eb-122">xs:string</span></span>|<span data-ttu-id="b59eb-123">追跡プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="b59eb-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="b59eb-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b59eb-124">ActivityDefinitionId</span></span>|<span data-ttu-id="b59eb-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b59eb-125">xs:string</span></span>|<span data-ttu-id="b59eb-126">アクティビティ定義 ID。</span><span class="sxs-lookup"><span data-stu-id="b59eb-126">The activity definition id.</span></span>|  
|<span data-ttu-id="b59eb-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b59eb-127">AppDomain</span></span>|<span data-ttu-id="b59eb-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b59eb-128">xs:string</span></span>|<span data-ttu-id="b59eb-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b59eb-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
