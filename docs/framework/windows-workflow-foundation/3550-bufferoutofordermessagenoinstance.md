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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce8b2cd52523d8a2efc94214479ca3c41d2dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="bc202-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="bc202-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="bc202-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc202-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc202-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc202-104">ID</span></span>|<span data-ttu-id="bc202-105">3550</span><span class="sxs-lookup"><span data-stu-id="bc202-105">3550</span></span>|  
|<span data-ttu-id="bc202-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bc202-106">Keywords</span></span>|<span data-ttu-id="bc202-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="bc202-107">WFServices</span></span>|  
|<span data-ttu-id="bc202-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bc202-108">Level</span></span>|<span data-ttu-id="bc202-109">情報</span><span class="sxs-lookup"><span data-stu-id="bc202-109">Information</span></span>|  
|<span data-ttu-id="bc202-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bc202-110">Channel</span></span>|<span data-ttu-id="bc202-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bc202-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc202-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc202-112">Description</span></span>  
 <span data-ttu-id="bc202-113">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc202-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="bc202-114">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="bc202-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc202-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bc202-115">Message</span></span>  
 <span data-ttu-id="bc202-116">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="bc202-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="bc202-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="bc202-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc202-118">詳細</span><span class="sxs-lookup"><span data-stu-id="bc202-118">Details</span></span>  
  
|<span data-ttu-id="bc202-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bc202-119">Data Item Name</span></span>|<span data-ttu-id="bc202-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bc202-120">Data Item Type</span></span>|<span data-ttu-id="bc202-121">説明</span><span class="sxs-lookup"><span data-stu-id="bc202-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc202-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="bc202-122">OperationName</span></span>|<span data-ttu-id="bc202-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc202-123">xs:string</span></span>|<span data-ttu-id="bc202-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="bc202-124">The name of the operation.</span></span>|  
|<span data-ttu-id="bc202-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc202-125">AppDomain</span></span>|<span data-ttu-id="bc202-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc202-126">xs:string</span></span>|<span data-ttu-id="bc202-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bc202-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
