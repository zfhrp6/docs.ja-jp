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
ms.openlocfilehash: 112063d5cd550f438541b2d775eaa49124d9cc02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="83fbf-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="83fbf-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="83fbf-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="83fbf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83fbf-104">ID</span><span class="sxs-lookup"><span data-stu-id="83fbf-104">ID</span></span>|<span data-ttu-id="83fbf-105">1036</span><span class="sxs-lookup"><span data-stu-id="83fbf-105">1036</span></span>|  
|<span data-ttu-id="83fbf-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="83fbf-106">Keywords</span></span>|<span data-ttu-id="83fbf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="83fbf-107">WFRuntime</span></span>|  
|<span data-ttu-id="83fbf-108">レベル</span><span class="sxs-lookup"><span data-stu-id="83fbf-108">Level</span></span>|<span data-ttu-id="83fbf-109">詳細</span><span class="sxs-lookup"><span data-stu-id="83fbf-109">Verbose</span></span>|  
|<span data-ttu-id="83fbf-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="83fbf-110">Channel</span></span>|<span data-ttu-id="83fbf-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="83fbf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83fbf-112">説明</span><span class="sxs-lookup"><span data-stu-id="83fbf-112">Description</span></span>  
 <span data-ttu-id="83fbf-113">アクティビティがランタイムのトランザクションの完了をスケジュールしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="83fbf-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83fbf-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="83fbf-114">Message</span></span>  
 <span data-ttu-id="83fbf-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。</span><span class="sxs-lookup"><span data-stu-id="83fbf-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83fbf-116">詳細</span><span class="sxs-lookup"><span data-stu-id="83fbf-116">Details</span></span>  
  
|<span data-ttu-id="83fbf-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="83fbf-117">Data Item Name</span></span>|<span data-ttu-id="83fbf-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="83fbf-118">Data Item Type</span></span>|<span data-ttu-id="83fbf-119">説明</span><span class="sxs-lookup"><span data-stu-id="83fbf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83fbf-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="83fbf-120">Activity</span></span>|<span data-ttu-id="83fbf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="83fbf-121">xs:string</span></span>|<span data-ttu-id="83fbf-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="83fbf-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="83fbf-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="83fbf-123">DisplayName</span></span>|<span data-ttu-id="83fbf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="83fbf-124">xs:string</span></span>|<span data-ttu-id="83fbf-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="83fbf-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="83fbf-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="83fbf-126">InstanceId</span></span>|<span data-ttu-id="83fbf-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="83fbf-127">xs:string</span></span>|<span data-ttu-id="83fbf-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="83fbf-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="83fbf-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83fbf-129">AppDomain</span></span>|<span data-ttu-id="83fbf-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="83fbf-130">xs:string</span></span>|<span data-ttu-id="83fbf-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="83fbf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
