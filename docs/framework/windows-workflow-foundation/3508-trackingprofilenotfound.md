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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="2ef5d-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="2ef5d-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="2ef5d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2ef5d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ef5d-104">ID</span><span class="sxs-lookup"><span data-stu-id="2ef5d-104">ID</span></span>|<span data-ttu-id="2ef5d-105">3508</span><span class="sxs-lookup"><span data-stu-id="2ef5d-105">3508</span></span>|  
|<span data-ttu-id="2ef5d-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="2ef5d-106">Keywords</span></span>|<span data-ttu-id="2ef5d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2ef5d-107">WFServices</span></span>|  
|<span data-ttu-id="2ef5d-108">レベル</span><span class="sxs-lookup"><span data-stu-id="2ef5d-108">Level</span></span>|<span data-ttu-id="2ef5d-109">詳細</span><span class="sxs-lookup"><span data-stu-id="2ef5d-109">Verbose</span></span>|  
|<span data-ttu-id="2ef5d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="2ef5d-110">Channel</span></span>|<span data-ttu-id="2ef5d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2ef5d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2ef5d-112">説明</span><span class="sxs-lookup"><span data-stu-id="2ef5d-112">Description</span></span>  
 <span data-ttu-id="2ef5d-113">構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2ef5d-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="2ef5d-114">Message</span></span>  
 <span data-ttu-id="2ef5d-115">ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="2ef5d-116">config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2ef5d-117">詳細</span><span class="sxs-lookup"><span data-stu-id="2ef5d-117">Details</span></span>  
  
|<span data-ttu-id="2ef5d-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="2ef5d-118">Data Item Name</span></span>|<span data-ttu-id="2ef5d-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="2ef5d-119">Data Item Type</span></span>|<span data-ttu-id="2ef5d-120">説明</span><span class="sxs-lookup"><span data-stu-id="2ef5d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2ef5d-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="2ef5d-121">TrackingProfile</span></span>|<span data-ttu-id="2ef5d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ef5d-122">xs:string</span></span>|<span data-ttu-id="2ef5d-123">追跡プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="2ef5d-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="2ef5d-124">ActivityDefinitionId</span></span>|<span data-ttu-id="2ef5d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ef5d-125">xs:string</span></span>|<span data-ttu-id="2ef5d-126">アクティビティ定義 ID。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-126">The activity definition id.</span></span>|  
|<span data-ttu-id="2ef5d-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2ef5d-127">AppDomain</span></span>|<span data-ttu-id="2ef5d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="2ef5d-128">xs:string</span></span>|<span data-ttu-id="2ef5d-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="2ef5d-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
