---
title: "メッセージ エンコーディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3040a16b6d167c4f066b2ddbd0a542741f88d62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="message-encoding"></a><span data-ttu-id="f0f5d-102">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="f0f5d-102">Message Encoding</span></span>
<span data-ttu-id="f0f5d-103">エンコーディングは、Unicode 文字のセットをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="f0f5d-104">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-104">Decoding is the reverse process.</span></span> <span data-ttu-id="f0f5d-105">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f0f5d-106">`binaryMessageEncoding` 構成セクションでは、バイナリ ベースの XML メッセージに使用される文字エンコーディングおよびメッセージ バージョン管理が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="f0f5d-107">バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="f0f5d-108">このエンコーディングによりメッセージ転送は非常に高速になりますが、WS-* 標準に基づいた相互運用性は失われます。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
 <span data-ttu-id="f0f5d-109">`mtomMessageEncoding` 構成セクションでは、Message Transmission Optimization Mechanism (MTOM) エンコーディングを使用したメッセージの文字エンコーディングおよびメッセージ バージョン管理が指定されます。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="f0f5d-110">(MTOM) は、Windows Communication Foundation (WCF) メッセージでバイナリ データを送信する効率的な技術です。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="f0f5d-111">MTOM エンコーダーは、効率と相互運用性のバランスをとろうとします。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="f0f5d-112">MTOM エンコーディングは、ほとんどの XML をテキスト形式で転送しますが、大きいサイズのバイナリ データ ブロックはテキストに変換せずにそのまま転送することによって最適化します。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="f0f5d-113">`textMessageEncoding` 構成セクションは、ネットワーク上でテキストベースのメッセージの作成に使用されるテキスト エンコーダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="f0f5d-114">このエンコーダーにより生成されるメッセージは、WS-* ベースの相互運用に適しています。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-114">Messages produced by this encoder are suitable for WS-* based interop.</span></span> <span data-ttu-id="f0f5d-115">Web サービスまたは Web サービス クライアントは、一般に、テキスト形式の XML を認識できます。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="f0f5d-116">ただし、バイナリ データの大きいブロックをテキストとして送信することは、XML メッセージをエンコードする最も効率の悪い方法です。</span><span class="sxs-lookup"><span data-stu-id="f0f5d-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f5d-117">参照</span><span class="sxs-lookup"><span data-stu-id="f0f5d-117">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 [<span data-ttu-id="f0f5d-118">バインディング</span><span class="sxs-lookup"><span data-stu-id="f0f5d-118">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f0f5d-119">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="f0f5d-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f0f5d-120">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="f0f5d-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f0f5d-121">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f0f5d-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="f0f5d-122">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="f0f5d-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
