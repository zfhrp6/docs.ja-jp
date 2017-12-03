---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68689e1694ac594467e11fabe44773b766af2b25
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="1e592-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="1e592-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="1e592-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1e592-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e592-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e592-104">ID</span></span>|<span data-ttu-id="1e592-105">3507</span><span class="sxs-lookup"><span data-stu-id="1e592-105">3507</span></span>|  
|<span data-ttu-id="1e592-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="1e592-106">Keywords</span></span>|<span data-ttu-id="1e592-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1e592-107">WFServices</span></span>|  
|<span data-ttu-id="1e592-108">レベル</span><span class="sxs-lookup"><span data-stu-id="1e592-108">Level</span></span>|<span data-ttu-id="1e592-109">情報</span><span class="sxs-lookup"><span data-stu-id="1e592-109">Information</span></span>|  
|<span data-ttu-id="1e592-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1e592-110">Channel</span></span>|<span data-ttu-id="1e592-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1e592-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e592-112">説明</span><span class="sxs-lookup"><span data-stu-id="1e592-112">Description</span></span>  
 <span data-ttu-id="1e592-113">サービス エンドポイントが追加されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="1e592-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e592-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="1e592-114">Message</span></span>  
 <span data-ttu-id="1e592-115">アドレス '%1'、バインド '%2'、コントラクト '%3' のサービス エンドポイントが追加されました。</span><span class="sxs-lookup"><span data-stu-id="1e592-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e592-116">詳細</span><span class="sxs-lookup"><span data-stu-id="1e592-116">Details</span></span>  
  
|<span data-ttu-id="1e592-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1e592-117">Data Item Name</span></span>|<span data-ttu-id="1e592-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1e592-118">Data Item Type</span></span>|<span data-ttu-id="1e592-119">説明</span><span class="sxs-lookup"><span data-stu-id="1e592-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e592-120">Address</span><span class="sxs-lookup"><span data-stu-id="1e592-120">Address</span></span>|<span data-ttu-id="1e592-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e592-121">xs:string</span></span>|<span data-ttu-id="1e592-122">エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="1e592-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="1e592-123">バインディング</span><span class="sxs-lookup"><span data-stu-id="1e592-123">Binding</span></span>|<span data-ttu-id="1e592-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e592-124">xs:string</span></span>|<span data-ttu-id="1e592-125">エンドポイントのバインド。</span><span class="sxs-lookup"><span data-stu-id="1e592-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="1e592-126">コントラクト</span><span class="sxs-lookup"><span data-stu-id="1e592-126">Contract</span></span>|<span data-ttu-id="1e592-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e592-127">xs:string</span></span>|<span data-ttu-id="1e592-128">エンドポイントのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="1e592-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="1e592-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e592-129">AppDomain</span></span>|<span data-ttu-id="1e592-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e592-130">xs:string</span></span>|<span data-ttu-id="1e592-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1e592-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
