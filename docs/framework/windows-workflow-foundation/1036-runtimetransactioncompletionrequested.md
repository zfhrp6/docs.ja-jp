---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="a26d0-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="a26d0-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="a26d0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a26d0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a26d0-104">ID</span><span class="sxs-lookup"><span data-stu-id="a26d0-104">ID</span></span>|<span data-ttu-id="a26d0-105">1036</span><span class="sxs-lookup"><span data-stu-id="a26d0-105">1036</span></span>|  
|<span data-ttu-id="a26d0-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="a26d0-106">Keywords</span></span>|<span data-ttu-id="a26d0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a26d0-107">WFRuntime</span></span>|  
|<span data-ttu-id="a26d0-108">レベル</span><span class="sxs-lookup"><span data-stu-id="a26d0-108">Level</span></span>|<span data-ttu-id="a26d0-109">詳細</span><span class="sxs-lookup"><span data-stu-id="a26d0-109">Verbose</span></span>|  
|<span data-ttu-id="a26d0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a26d0-110">Channel</span></span>|<span data-ttu-id="a26d0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a26d0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a26d0-112">説明</span><span class="sxs-lookup"><span data-stu-id="a26d0-112">Description</span></span>  
 <span data-ttu-id="a26d0-113">アクティビティがランタイムのトランザクションの完了をスケジュールしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="a26d0-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a26d0-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="a26d0-114">Message</span></span>  
 <span data-ttu-id="a26d0-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。</span><span class="sxs-lookup"><span data-stu-id="a26d0-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a26d0-116">詳細</span><span class="sxs-lookup"><span data-stu-id="a26d0-116">Details</span></span>  
  
|<span data-ttu-id="a26d0-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a26d0-117">Data Item Name</span></span>|<span data-ttu-id="a26d0-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a26d0-118">Data Item Type</span></span>|<span data-ttu-id="a26d0-119">説明</span><span class="sxs-lookup"><span data-stu-id="a26d0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a26d0-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a26d0-120">Activity</span></span>|<span data-ttu-id="a26d0-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a26d0-121">xs:string</span></span>|<span data-ttu-id="a26d0-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a26d0-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a26d0-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a26d0-123">DisplayName</span></span>|<span data-ttu-id="a26d0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a26d0-124">xs:string</span></span>|<span data-ttu-id="a26d0-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a26d0-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a26d0-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a26d0-126">InstanceId</span></span>|<span data-ttu-id="a26d0-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a26d0-127">xs:string</span></span>|<span data-ttu-id="a26d0-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a26d0-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a26d0-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a26d0-129">AppDomain</span></span>|<span data-ttu-id="a26d0-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a26d0-130">xs:string</span></span>|<span data-ttu-id="a26d0-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a26d0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
