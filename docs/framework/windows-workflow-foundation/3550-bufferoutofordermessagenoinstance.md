---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511599"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="c4162-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="c4162-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="c4162-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c4162-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4162-104">ID</span><span class="sxs-lookup"><span data-stu-id="c4162-104">ID</span></span>|<span data-ttu-id="c4162-105">3550</span><span class="sxs-lookup"><span data-stu-id="c4162-105">3550</span></span>|  
|<span data-ttu-id="c4162-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="c4162-106">Keywords</span></span>|<span data-ttu-id="c4162-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c4162-107">WFServices</span></span>|  
|<span data-ttu-id="c4162-108">レベル</span><span class="sxs-lookup"><span data-stu-id="c4162-108">Level</span></span>|<span data-ttu-id="c4162-109">情報</span><span class="sxs-lookup"><span data-stu-id="c4162-109">Information</span></span>|  
|<span data-ttu-id="c4162-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c4162-110">Channel</span></span>|<span data-ttu-id="c4162-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c4162-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c4162-112">説明</span><span class="sxs-lookup"><span data-stu-id="c4162-112">Description</span></span>  
 <span data-ttu-id="c4162-113">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c4162-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="c4162-114">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="c4162-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c4162-115">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c4162-115">Message</span></span>  
 <span data-ttu-id="c4162-116">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="c4162-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="c4162-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="c4162-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c4162-118">詳細</span><span class="sxs-lookup"><span data-stu-id="c4162-118">Details</span></span>  
  
|<span data-ttu-id="c4162-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c4162-119">Data Item Name</span></span>|<span data-ttu-id="c4162-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c4162-120">Data Item Type</span></span>|<span data-ttu-id="c4162-121">説明</span><span class="sxs-lookup"><span data-stu-id="c4162-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c4162-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="c4162-122">OperationName</span></span>|<span data-ttu-id="c4162-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4162-123">xs:string</span></span>|<span data-ttu-id="c4162-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="c4162-124">The name of the operation.</span></span>|  
|<span data-ttu-id="c4162-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c4162-125">AppDomain</span></span>|<span data-ttu-id="c4162-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4162-126">xs:string</span></span>|<span data-ttu-id="c4162-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c4162-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
