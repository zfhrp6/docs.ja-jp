---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="8a476-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="8a476-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="8a476-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8a476-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a476-104">ID</span><span class="sxs-lookup"><span data-stu-id="8a476-104">ID</span></span>|<span data-ttu-id="8a476-105">3550</span><span class="sxs-lookup"><span data-stu-id="8a476-105">3550</span></span>|  
|<span data-ttu-id="8a476-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="8a476-106">Keywords</span></span>|<span data-ttu-id="8a476-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8a476-107">WFServices</span></span>|  
|<span data-ttu-id="8a476-108">レベル</span><span class="sxs-lookup"><span data-stu-id="8a476-108">Level</span></span>|<span data-ttu-id="8a476-109">情報</span><span class="sxs-lookup"><span data-stu-id="8a476-109">Information</span></span>|  
|<span data-ttu-id="8a476-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8a476-110">Channel</span></span>|<span data-ttu-id="8a476-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8a476-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8a476-112">説明</span><span class="sxs-lookup"><span data-stu-id="8a476-112">Description</span></span>  
 <span data-ttu-id="8a476-113">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8a476-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="8a476-114">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="8a476-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8a476-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="8a476-115">Message</span></span>  
 <span data-ttu-id="8a476-116">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="8a476-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="8a476-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="8a476-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8a476-118">詳細</span><span class="sxs-lookup"><span data-stu-id="8a476-118">Details</span></span>  
  
|<span data-ttu-id="8a476-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8a476-119">Data Item Name</span></span>|<span data-ttu-id="8a476-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8a476-120">Data Item Type</span></span>|<span data-ttu-id="8a476-121">説明</span><span class="sxs-lookup"><span data-stu-id="8a476-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8a476-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="8a476-122">OperationName</span></span>|<span data-ttu-id="8a476-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="8a476-123">xs:string</span></span>|<span data-ttu-id="8a476-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="8a476-124">The name of the operation.</span></span>|  
|<span data-ttu-id="8a476-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8a476-125">AppDomain</span></span>|<span data-ttu-id="8a476-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="8a476-126">xs:string</span></span>|<span data-ttu-id="8a476-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8a476-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
