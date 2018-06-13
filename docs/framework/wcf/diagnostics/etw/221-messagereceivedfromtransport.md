---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458778"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="bc32f-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="bc32f-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="bc32f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc32f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc32f-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc32f-104">ID</span></span>|<span data-ttu-id="bc32f-105">221</span><span class="sxs-lookup"><span data-stu-id="bc32f-105">221</span></span>|  
|<span data-ttu-id="bc32f-106">キーワード</span><span class="sxs-lookup"><span data-stu-id="bc32f-106">Keywords</span></span>|<span data-ttu-id="bc32f-107">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bc32f-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="bc32f-108">レベル</span><span class="sxs-lookup"><span data-stu-id="bc32f-108">Level</span></span>|<span data-ttu-id="bc32f-109">情報</span><span class="sxs-lookup"><span data-stu-id="bc32f-109">Information</span></span>|  
|<span data-ttu-id="bc32f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bc32f-110">Channel</span></span>|<span data-ttu-id="bc32f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bc32f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc32f-112">説明</span><span class="sxs-lookup"><span data-stu-id="bc32f-112">Description</span></span>  
 <span data-ttu-id="bc32f-113">このイベントは、サービス モデルがトランスポートからメッセージを受信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="bc32f-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc32f-114">メッセージ</span><span class="sxs-lookup"><span data-stu-id="bc32f-114">Message</span></span>  
 <span data-ttu-id="bc32f-115">ディスパッチャーがトランスポートからメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="bc32f-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="bc32f-116">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="bc32f-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc32f-117">説明</span><span class="sxs-lookup"><span data-stu-id="bc32f-117">Details</span></span>  
  
|<span data-ttu-id="bc32f-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bc32f-118">Data Item Name</span></span>|<span data-ttu-id="bc32f-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bc32f-119">Data Item Type</span></span>|<span data-ttu-id="bc32f-120">説明</span><span class="sxs-lookup"><span data-stu-id="bc32f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc32f-121">Correlation ID</span><span class="sxs-lookup"><span data-stu-id="bc32f-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="bc32f-122">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="bc32f-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="bc32f-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="bc32f-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="bc32f-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="bc32f-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bc32f-125">その形式とは見なさ ' Web サイト名アプリケーション仮想パス&#124;サービス仮想パス&#124;ServiceName' です。</span><span class="sxs-lookup"><span data-stu-id="bc32f-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bc32f-126">例: ' 既定の Web サイト/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'。</span><span class="sxs-lookup"><span data-stu-id="bc32f-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bc32f-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc32f-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bc32f-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bc32f-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
