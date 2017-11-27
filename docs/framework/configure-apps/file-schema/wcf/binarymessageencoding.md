---
title: '&lt;binaryMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 11d819d5d6302da309dd3e4ce674110c8419978f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="f6630-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="f6630-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="f6630-103">ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードするバイナリ メッセージ エンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="f6630-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="f6630-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f6630-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f6630-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f6630-105">\<bindings></span></span>  
<span data-ttu-id="f6630-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f6630-106">\<customBinding></span></span>  
<span data-ttu-id="f6630-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f6630-107">\<binding></span></span>  
<span data-ttu-id="f6630-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="f6630-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6630-109">構文</span><span class="sxs-lookup"><span data-stu-id="f6630-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6630-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f6630-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6630-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f6630-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6630-112">属性</span><span class="sxs-lookup"><span data-stu-id="f6630-112">Attributes</span></span>  
  
|<span data-ttu-id="f6630-113">属性</span><span class="sxs-lookup"><span data-stu-id="f6630-113">Attribute</span></span>|<span data-ttu-id="f6630-114">説明</span><span class="sxs-lookup"><span data-stu-id="f6630-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6630-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f6630-115">maxReadPoolSize</span></span>|<span data-ttu-id="f6630-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="f6630-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="f6630-117">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="f6630-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f6630-118">既定値は 64 です。</span><span class="sxs-lookup"><span data-stu-id="f6630-118">The default is 64.</span></span>|  
|<span data-ttu-id="f6630-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="f6630-119">maxSessionSize</span></span>|<span data-ttu-id="f6630-120">エンコーディングに使用されるバッファーのサイズをバイト単位で設定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="f6630-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="f6630-121">バッファーが大きくなると、作業セットのサイズの増加時に、エンコーディングの速度が高まります。</span><span class="sxs-lookup"><span data-stu-id="f6630-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="f6630-122">既定値は 2048 です。</span><span class="sxs-lookup"><span data-stu-id="f6630-122">The default is 2048.</span></span>|  
|<span data-ttu-id="f6630-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f6630-123">maxWritePoolSize</span></span>|<span data-ttu-id="f6630-124">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="f6630-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="f6630-125">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="f6630-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="f6630-126">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="f6630-126">The default is 16.</span></span>|  
|<span data-ttu-id="f6630-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="f6630-127">messageVersion</span></span>|<span data-ttu-id="f6630-128">使用または予想される SOAP メッセージおよび WS-Addressing のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6630-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6630-129">子要素</span><span class="sxs-lookup"><span data-stu-id="f6630-129">Child Elements</span></span>  
  
|<span data-ttu-id="f6630-130">要素</span><span class="sxs-lookup"><span data-stu-id="f6630-130">Element</span></span>|<span data-ttu-id="f6630-131">説明</span><span class="sxs-lookup"><span data-stu-id="f6630-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6630-132">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="f6630-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="f6630-133">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6630-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6630-134">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="f6630-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6630-135">親要素</span><span class="sxs-lookup"><span data-stu-id="f6630-135">Parent Elements</span></span>  
  
|<span data-ttu-id="f6630-136">要素</span><span class="sxs-lookup"><span data-stu-id="f6630-136">Element</span></span>|<span data-ttu-id="f6630-137">説明</span><span class="sxs-lookup"><span data-stu-id="f6630-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6630-138">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="f6630-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f6630-139">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="f6630-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6630-140">コメント</span><span class="sxs-lookup"><span data-stu-id="f6630-140">Remarks</span></span>  
 <span data-ttu-id="f6630-141">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f6630-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="f6630-142">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f6630-142">Decoding is the reverse process.</span></span> <span data-ttu-id="f6630-143">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="f6630-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="f6630-144">`binaryMessageEncoding` 要素は、XML 用の .NET バイナリ形式を指定します。この要素には、使用する文字エンコーディング、SOAP バージョン、および WS-Addressing バージョンを指定するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="f6630-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="f6630-145">バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="f6630-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="f6630-146">このエンコーディングによりメッセージ転送は非常に高速になりますが、WS-* 標準に基づいた相互運用性は失われます。</span><span class="sxs-lookup"><span data-stu-id="f6630-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6630-147">例</span><span class="sxs-lookup"><span data-stu-id="f6630-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6630-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6630-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="f6630-149">メッセージのエンコード</span><span class="sxs-lookup"><span data-stu-id="f6630-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="f6630-150">メッセージ エンコーダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="f6630-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="f6630-151">バインディング</span><span class="sxs-lookup"><span data-stu-id="f6630-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f6630-152">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="f6630-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f6630-153">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="f6630-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f6630-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f6630-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
