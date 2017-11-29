---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e53225399e3acba275d2d95533c4baad20386a4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="e6612-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="e6612-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="e6612-103">異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="e6612-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="e6612-104">**\<システムです。ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="e6612-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="e6612-105">&nbsp;&nbsp;**\<ビヘイビアー >** </span><span class="sxs-lookup"><span data-stu-id="e6612-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="e6612-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="e6612-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="e6612-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<動作 >** </span><span class="sxs-lookup"><span data-stu-id="e6612-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="e6612-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="e6612-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e6612-109">構文</span><span class="sxs-lookup"><span data-stu-id="e6612-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6612-110">属性と要素</span><span class="sxs-lookup"><span data-stu-id="e6612-110">Attributes and elements</span></span>

<span data-ttu-id="e6612-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6612-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6612-112">属性</span><span class="sxs-lookup"><span data-stu-id="e6612-112">Attributes</span></span>

|                   | <span data-ttu-id="e6612-113">説明</span><span class="sxs-lookup"><span data-stu-id="e6612-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="e6612-114">SOAP メッセージ バージョン間のメッセージをマーシャリングするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="e6612-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="e6612-115">子要素</span><span class="sxs-lookup"><span data-stu-id="e6612-115">Child elements</span></span>

<span data-ttu-id="e6612-116">なし</span><span class="sxs-lookup"><span data-stu-id="e6612-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e6612-117">親要素</span><span class="sxs-lookup"><span data-stu-id="e6612-117">Parent elements</span></span>

|     | <span data-ttu-id="e6612-118">説明</span><span class="sxs-lookup"><span data-stu-id="e6612-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e6612-119">**\<動作 >**</span><span class="sxs-lookup"><span data-stu-id="e6612-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="e6612-120">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6612-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e6612-121">コメント</span><span class="sxs-lookup"><span data-stu-id="e6612-121">Remarks</span></span>

<span data-ttu-id="e6612-122">SOAP 処理は、メッセージ バージョン間でメッセージが変換されるプロセスです。</span><span class="sxs-lookup"><span data-stu-id="e6612-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="e6612-123">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ルーティング サービスは、あるプロトコルから別のプロトコルにメッセージを変換できます。</span><span class="sxs-lookup"><span data-stu-id="e6612-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="e6612-124">受信メッセージのバージョンと送信メッセージのバージョンが異なる場合、新しいメッセージが正しいバージョンで作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6612-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="e6612-125">いずれかからメッセージを処理する<!--zz <xref:System.ServiceModel.Channel.MessageVersion> -->`MessageVersion`間は新しい構築することによって実現[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]本文および関連する受信ヘッダーを含むメッセージ[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]メッセージ。</span><span class="sxs-lookup"><span data-stu-id="e6612-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="e6612-126">アドレス指定に固有のヘッダーまたはルーター レベルで認識されるヘッダーは、新しい WCF メッセージの作成に使用されません。これらのヘッダーは、異なるバージョンであるか (アドレス指定ヘッダーの場合)、クライアントとルーターの間の通信の一部として処理されているためです。</span><span class="sxs-lookup"><span data-stu-id="e6612-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="e6612-127">発信メッセージにヘッダーが配置されるかどうかは、受信チャネル層を介して渡されたと認識されるようにマークされているかどうかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="e6612-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="e6612-128">認識されないヘッダー (カスタム ヘッダーなど) は削除されずに送信メッセージにコピーされ、ルーティング サービスを介して渡されます。</span><span class="sxs-lookup"><span data-stu-id="e6612-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="e6612-129">メッセージの本文は、送信メッセージにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="e6612-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="e6612-130">そして、メッセージは送信チャネルに送信されます。この時点で、すべてのヘッダー、および使用されている通信プロトコル/トランスポートに固有のエンベロープ データが作成され、追加されます。</span><span class="sxs-lookup"><span data-stu-id="e6612-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="e6612-131">このような処理手順は、SOAP 処理動作が指定されているときに行われます。</span><span class="sxs-lookup"><span data-stu-id="e6612-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="e6612-132">これは、 [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)動作は、ルーティング サービスの起動時に、すべてのクライアント (送信) エンドポイントに適用されるエンドポイントの動作です。</span><span class="sxs-lookup"><span data-stu-id="e6612-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="e6612-133">既定で、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作を作成し、新しい[ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)での動作`processMessages`'éý'`true`ごとクライアントのエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="e6612-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="e6612-134">ルーティング サービスが認識しないプロトコルを使用している場合や既定の処理動作をオーバーライドする場合は、ルーティング サービス全体または特定のエンドポイントにおいて SOAP 処理を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="e6612-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="e6612-135">SOAP のすべてのエンドポイントにルーティング サービス全体の処理を無効にする設定、`soapProcessing`の属性、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作を`false`です。</span><span class="sxs-lookup"><span data-stu-id="e6612-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="e6612-136">特定のエンドポイントで SOAP 処理を無効にするには、この動作を使用して `processMessages` 属性を `false` に設定してから、既定の処理コードを実行しないエンドポイントにこの動作をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="e6612-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="e6612-137">ときに、 [\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)動作は、ルーティング サービスを設定、1 つが既に存在するために、エンドポイントの動作を再適用はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="e6612-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
