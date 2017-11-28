---
title: 39457 - TrackingRecordRaised
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d2e142db5834a6c867970a28ec74e9fceebee16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39457---trackingrecordraised"></a><span data-ttu-id="35173-102">39457 - TrackingRecordRaised</span><span class="sxs-lookup"><span data-stu-id="35173-102">39457 - TrackingRecordRaised</span></span>
## <a name="properties"></a><span data-ttu-id="35173-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="35173-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="35173-104">ID</span><span class="sxs-lookup"><span data-stu-id="35173-104">ID</span></span>|<span data-ttu-id="35173-105">39457</span><span class="sxs-lookup"><span data-stu-id="35173-105">39457</span></span>|  
|<span data-ttu-id="35173-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="35173-106">Keywords</span></span>|<span data-ttu-id="35173-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="35173-107">WFRuntime</span></span>|  
|<span data-ttu-id="35173-108">レベル</span><span class="sxs-lookup"><span data-stu-id="35173-108">Level</span></span>|<span data-ttu-id="35173-109">情報</span><span class="sxs-lookup"><span data-stu-id="35173-109">Information</span></span>|  
|<span data-ttu-id="35173-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="35173-110">Channel</span></span>|<span data-ttu-id="35173-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="35173-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="35173-112">説明</span><span class="sxs-lookup"><span data-stu-id="35173-112">Description</span></span>  
 <span data-ttu-id="35173-113">TrackingRecord が TrackingParticipant に発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="35173-113">Indicates a TrackingRecord has been raised to a TrackingParticipant.</span></span>  
  
## <a name="message"></a><span data-ttu-id="35173-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="35173-114">Message</span></span>  
 <span data-ttu-id="35173-115">追跡レコード %1 が %2 になりました。</span><span class="sxs-lookup"><span data-stu-id="35173-115">Tracking Record %1 raised to %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="35173-116">詳細</span><span class="sxs-lookup"><span data-stu-id="35173-116">Details</span></span>  
  
|<span data-ttu-id="35173-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="35173-117">Data Item Name</span></span>|<span data-ttu-id="35173-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="35173-118">Data Item Type</span></span>|<span data-ttu-id="35173-119">説明</span><span class="sxs-lookup"><span data-stu-id="35173-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="35173-120">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="35173-120">RecordNumber</span></span>|<span data-ttu-id="35173-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="35173-121">xs:string</span></span>|<span data-ttu-id="35173-122">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="35173-122">The tracking record number.</span></span>|  
|<span data-ttu-id="35173-123">ParticipantId</span><span class="sxs-lookup"><span data-stu-id="35173-123">ParticipantId</span></span>|<span data-ttu-id="35173-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="35173-124">xs:string</span></span>|<span data-ttu-id="35173-125">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="35173-125">The tracking participant.</span></span>|  
|<span data-ttu-id="35173-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="35173-126">AppDomain</span></span>|<span data-ttu-id="35173-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="35173-127">xs:string</span></span>|<span data-ttu-id="35173-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="35173-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
