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
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="521da-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="521da-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="521da-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="521da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="521da-104">ID</span><span class="sxs-lookup"><span data-stu-id="521da-104">ID</span></span>|<span data-ttu-id="521da-105">3508</span><span class="sxs-lookup"><span data-stu-id="521da-105">3508</span></span>|  
|<span data-ttu-id="521da-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="521da-106">Keywords</span></span>|<span data-ttu-id="521da-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="521da-107">WFServices</span></span>|  
|<span data-ttu-id="521da-108">レベル</span><span class="sxs-lookup"><span data-stu-id="521da-108">Level</span></span>|<span data-ttu-id="521da-109">詳細</span><span class="sxs-lookup"><span data-stu-id="521da-109">Verbose</span></span>|  
|<span data-ttu-id="521da-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="521da-110">Channel</span></span>|<span data-ttu-id="521da-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="521da-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="521da-112">説明</span><span class="sxs-lookup"><span data-stu-id="521da-112">Description</span></span>  
 <span data-ttu-id="521da-113">構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="521da-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="521da-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="521da-114">Message</span></span>  
 <span data-ttu-id="521da-115">ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="521da-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="521da-116">config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。</span><span class="sxs-lookup"><span data-stu-id="521da-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="521da-117">詳細</span><span class="sxs-lookup"><span data-stu-id="521da-117">Details</span></span>  
  
|<span data-ttu-id="521da-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="521da-118">Data Item Name</span></span>|<span data-ttu-id="521da-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="521da-119">Data Item Type</span></span>|<span data-ttu-id="521da-120">説明</span><span class="sxs-lookup"><span data-stu-id="521da-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="521da-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="521da-121">TrackingProfile</span></span>|<span data-ttu-id="521da-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="521da-122">xs:string</span></span>|<span data-ttu-id="521da-123">追跡プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="521da-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="521da-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="521da-124">ActivityDefinitionId</span></span>|<span data-ttu-id="521da-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="521da-125">xs:string</span></span>|<span data-ttu-id="521da-126">アクティビティ定義 ID。</span><span class="sxs-lookup"><span data-stu-id="521da-126">The activity definition id.</span></span>|  
|<span data-ttu-id="521da-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="521da-127">AppDomain</span></span>|<span data-ttu-id="521da-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="521da-128">xs:string</span></span>|<span data-ttu-id="521da-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="521da-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
