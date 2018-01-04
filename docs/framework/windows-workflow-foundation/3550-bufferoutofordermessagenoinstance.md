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
ms.workload: dotnet
ms.openlocfilehash: 435a6a4390d52555d353a25ac119934087cf9c87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="f3f0d-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="f3f0d-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="f3f0d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3f0d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3f0d-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3f0d-104">ID</span></span>|<span data-ttu-id="f3f0d-105">3550</span><span class="sxs-lookup"><span data-stu-id="f3f0d-105">3550</span></span>|  
|<span data-ttu-id="f3f0d-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="f3f0d-106">Keywords</span></span>|<span data-ttu-id="f3f0d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f3f0d-107">WFServices</span></span>|  
|<span data-ttu-id="f3f0d-108">レベル</span><span class="sxs-lookup"><span data-stu-id="f3f0d-108">Level</span></span>|<span data-ttu-id="f3f0d-109">情報</span><span class="sxs-lookup"><span data-stu-id="f3f0d-109">Information</span></span>|  
|<span data-ttu-id="f3f0d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f3f0d-110">Channel</span></span>|<span data-ttu-id="f3f0d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f3f0d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3f0d-112">説明</span><span class="sxs-lookup"><span data-stu-id="f3f0d-112">Description</span></span>  
 <span data-ttu-id="f3f0d-113">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="f3f0d-114">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3f0d-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="f3f0d-115">Message</span></span>  
 <span data-ttu-id="f3f0d-116">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="f3f0d-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3f0d-118">詳細</span><span class="sxs-lookup"><span data-stu-id="f3f0d-118">Details</span></span>  
  
|<span data-ttu-id="f3f0d-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f3f0d-119">Data Item Name</span></span>|<span data-ttu-id="f3f0d-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f3f0d-120">Data Item Type</span></span>|<span data-ttu-id="f3f0d-121">説明</span><span class="sxs-lookup"><span data-stu-id="f3f0d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3f0d-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="f3f0d-122">OperationName</span></span>|<span data-ttu-id="f3f0d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="f3f0d-123">xs:string</span></span>|<span data-ttu-id="f3f0d-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-124">The name of the operation.</span></span>|  
|<span data-ttu-id="f3f0d-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3f0d-125">AppDomain</span></span>|<span data-ttu-id="f3f0d-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="f3f0d-126">xs:string</span></span>|<span data-ttu-id="f3f0d-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f3f0d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
