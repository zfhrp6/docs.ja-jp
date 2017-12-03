---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42974d0f1de639370d6fac2346572758e1d19d46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="019db-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="019db-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="019db-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="019db-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019db-104">構文</span><span class="sxs-lookup"><span data-stu-id="019db-104">Syntax</span></span>  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="019db-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="019db-105">Methods</span></span>  
 <span data-ttu-id="019db-106">ConnectionOrientedTransportBindingElement クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="019db-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="019db-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="019db-107">Properties</span></span>  
 <span data-ttu-id="019db-108">ConnectionOrientedTransportBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="019db-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="019db-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="019db-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="019db-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="019db-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="019db-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-112">チャネルの初期化が開始されてからタイムアウトになるまでの時間の長さを示す期間。</span><span class="sxs-lookup"><span data-stu-id="019db-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="019db-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="019db-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="019db-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="019db-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="019db-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-116">クライアントまたサービスからネットワークでシリアル化されたメッセージのチャンクを転送するために使用されるバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="019db-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="019db-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="019db-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="019db-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="019db-118">Data type: string</span></span>  
  
 <span data-ttu-id="019db-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-120">URI の照合時にサービスに到達するため、ホスト名が使用されたかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="019db-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="019db-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="019db-121">MaxBufferSize</span></span>  
 <span data-ttu-id="019db-122">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="019db-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="019db-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-124">使用するバッファーの最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="019db-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="019db-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="019db-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="019db-126">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="019db-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="019db-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-128">メッセージのチャンクまたは完全なメッセージを、送信前にメモリ内のバッファーに残したままにできる最長期間。</span><span class="sxs-lookup"><span data-stu-id="019db-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="019db-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="019db-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="019db-130">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="019db-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="019db-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-132">サービスでの着信接続処理に使用できる保留中の非同期受け入れスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="019db-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="019db-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="019db-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="019db-134">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="019db-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="019db-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-136">保留状態の接続の最大数。</span><span class="sxs-lookup"><span data-stu-id="019db-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="019db-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="019db-137">TransferMode</span></span>  
 <span data-ttu-id="019db-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="019db-138">Data type: string</span></span>  
  
 <span data-ttu-id="019db-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="019db-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019db-140">接続指向トランスポートを使用して、メッセージをバッファーするかまたはストリームするかを指定する値。</span><span class="sxs-lookup"><span data-stu-id="019db-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="019db-141">要件</span><span class="sxs-lookup"><span data-stu-id="019db-141">Requirements</span></span>  
  
|<span data-ttu-id="019db-142">MOF</span><span class="sxs-lookup"><span data-stu-id="019db-142">MOF</span></span>|<span data-ttu-id="019db-143">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="019db-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="019db-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="019db-144">Namespace</span></span>|<span data-ttu-id="019db-145">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="019db-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="019db-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="019db-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
