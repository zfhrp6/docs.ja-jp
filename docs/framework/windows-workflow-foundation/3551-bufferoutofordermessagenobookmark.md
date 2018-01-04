---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e785e40afcb91620940f952022eda4c4b799f4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="7d930-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="7d930-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="7d930-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d930-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d930-104">ID</span><span class="sxs-lookup"><span data-stu-id="7d930-104">ID</span></span>|<span data-ttu-id="7d930-105">3551</span><span class="sxs-lookup"><span data-stu-id="7d930-105">3551</span></span>|  
|<span data-ttu-id="7d930-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="7d930-106">Keywords</span></span>|<span data-ttu-id="7d930-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7d930-107">WFServices</span></span>|  
|<span data-ttu-id="7d930-108">レベル</span><span class="sxs-lookup"><span data-stu-id="7d930-108">Level</span></span>|<span data-ttu-id="7d930-109">情報</span><span class="sxs-lookup"><span data-stu-id="7d930-109">Information</span></span>|  
|<span data-ttu-id="7d930-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7d930-110">Channel</span></span>|<span data-ttu-id="7d930-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7d930-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d930-112">説明</span><span class="sxs-lookup"><span data-stu-id="7d930-112">Description</span></span>  
 <span data-ttu-id="7d930-113">ブックマークの再開が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="7d930-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="7d930-114">サービス インスタンスがこの特定の操作を処理する準備が整ったら、バッファーされた受信操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="7d930-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d930-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="7d930-115">Message</span></span>  
 <span data-ttu-id="7d930-116">サービス インスタンス '%1' での操作 '%2' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="7d930-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="7d930-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="7d930-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d930-118">詳細</span><span class="sxs-lookup"><span data-stu-id="7d930-118">Details</span></span>  
  
|<span data-ttu-id="7d930-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7d930-119">Data Item Name</span></span>|<span data-ttu-id="7d930-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7d930-120">Data Item Type</span></span>|<span data-ttu-id="7d930-121">説明</span><span class="sxs-lookup"><span data-stu-id="7d930-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d930-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="7d930-122">OperationName</span></span>|<span data-ttu-id="7d930-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d930-123">xs:string</span></span>|<span data-ttu-id="7d930-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="7d930-124">The name of the operation.</span></span>|  
|<span data-ttu-id="7d930-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="7d930-125">ServiceInstanceId</span></span>|<span data-ttu-id="7d930-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d930-126">xs:string</span></span>|<span data-ttu-id="7d930-127">サービス インスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="7d930-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="7d930-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7d930-128">AppDomain</span></span>|<span data-ttu-id="7d930-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d930-129">xs:string</span></span>|<span data-ttu-id="7d930-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7d930-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
