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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e1314347dfb83fb0631ebaa98b4d35bb0ac402f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltbinarymessageencodinggt"></a><span data-ttu-id="813b2-102">&lt;binaryMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="813b2-102">&lt;binaryMessageEncoding&gt;</span></span>
<span data-ttu-id="813b2-103">ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードするバイナリ メッセージ エンコーダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="813b2-103">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="813b2-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="813b2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="813b2-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="813b2-105">\<bindings></span></span>  
<span data-ttu-id="813b2-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="813b2-106">\<customBinding></span></span>  
<span data-ttu-id="813b2-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="813b2-107">\<binding></span></span>  
<span data-ttu-id="813b2-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="813b2-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813b2-109">構文</span><span class="sxs-lookup"><span data-stu-id="813b2-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding   
      maxReadPoolSize="Integer"  
   maxSessionSize="Integer"   
   maxWritePoolSize="Integer"   messageVersion="Soap11Addressing10/Soap12Addressing10" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="813b2-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="813b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="813b2-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="813b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="813b2-112">属性</span><span class="sxs-lookup"><span data-stu-id="813b2-112">Attributes</span></span>  
  
|<span data-ttu-id="813b2-113">属性</span><span class="sxs-lookup"><span data-stu-id="813b2-113">Attribute</span></span>|<span data-ttu-id="813b2-114">説明</span><span class="sxs-lookup"><span data-stu-id="813b2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="813b2-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="813b2-115">maxReadPoolSize</span></span>|<span data-ttu-id="813b2-116">新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="813b2-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="813b2-117">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="813b2-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="813b2-118">既定値は 64 です。</span><span class="sxs-lookup"><span data-stu-id="813b2-118">The default is 64.</span></span>|  
|<span data-ttu-id="813b2-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="813b2-119">maxSessionSize</span></span>|<span data-ttu-id="813b2-120">エンコーディングに使用されるバッファーのサイズをバイト単位で設定する正の整数。</span><span class="sxs-lookup"><span data-stu-id="813b2-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="813b2-121">バッファーが大きくなると、作業セットのサイズの増加時に、エンコーディングの速度が高まります。</span><span class="sxs-lookup"><span data-stu-id="813b2-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="813b2-122">既定値は 2048 です。</span><span class="sxs-lookup"><span data-stu-id="813b2-122">The default is 2048.</span></span>|  
|<span data-ttu-id="813b2-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="813b2-123">maxWritePoolSize</span></span>|<span data-ttu-id="813b2-124">新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。</span><span class="sxs-lookup"><span data-stu-id="813b2-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="813b2-125">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="813b2-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="813b2-126">既定値は 16 です。</span><span class="sxs-lookup"><span data-stu-id="813b2-126">The default is 16.</span></span>|  
|<span data-ttu-id="813b2-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="813b2-127">messageVersion</span></span>|<span data-ttu-id="813b2-128">使用または予想される SOAP メッセージおよび WS-Addressing のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="813b2-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="813b2-129">子要素</span><span class="sxs-lookup"><span data-stu-id="813b2-129">Child Elements</span></span>  
  
|<span data-ttu-id="813b2-130">要素</span><span class="sxs-lookup"><span data-stu-id="813b2-130">Element</span></span>|<span data-ttu-id="813b2-131">説明</span><span class="sxs-lookup"><span data-stu-id="813b2-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="813b2-132">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="813b2-132">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="813b2-133">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="813b2-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="813b2-134">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="813b2-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="813b2-135">親要素</span><span class="sxs-lookup"><span data-stu-id="813b2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="813b2-136">要素</span><span class="sxs-lookup"><span data-stu-id="813b2-136">Element</span></span>|<span data-ttu-id="813b2-137">説明</span><span class="sxs-lookup"><span data-stu-id="813b2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="813b2-138">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="813b2-138">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="813b2-139">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="813b2-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="813b2-140">コメント</span><span class="sxs-lookup"><span data-stu-id="813b2-140">Remarks</span></span>  
 <span data-ttu-id="813b2-141">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="813b2-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="813b2-142">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="813b2-142">Decoding is the reverse process.</span></span> <span data-ttu-id="813b2-143">WCF (Windows Communication Foundation) には、SOAP メッセージのエンコードとして、テキスト、バイナリ、および MTOM (Message Transmission Optimization Mechanism) の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="813b2-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="813b2-144">`binaryMessageEncoding` 要素は、XML 用の .NET バイナリ形式を指定します。この要素には、使用する文字エンコーディング、SOAP バージョン、および WS-Addressing バージョンを指定するオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="813b2-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="813b2-145">バイナリ メッセージ エンコーダーは、ネットワーク上で Windows Communication Foundation (WCF) メッセージをバイナリにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="813b2-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="813b2-146">このエンコーディングによりメッセージ転送は非常に高速になりますが、WS-* 標準に基づいた相互運用性は失われます。</span><span class="sxs-lookup"><span data-stu-id="813b2-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="813b2-147">例</span><span class="sxs-lookup"><span data-stu-id="813b2-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"  
   maxWritePoolSize="2132"  
   maxSessionSize="3141" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="813b2-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="813b2-148">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
 [<span data-ttu-id="813b2-149">メッセージのエンコード</span><span class="sxs-lookup"><span data-stu-id="813b2-149">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="813b2-150">メッセージ エンコーダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="813b2-150">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="813b2-151">バインディング</span><span class="sxs-lookup"><span data-stu-id="813b2-151">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="813b2-152">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="813b2-152">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="813b2-153">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="813b2-153">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="813b2-154">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="813b2-154">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
