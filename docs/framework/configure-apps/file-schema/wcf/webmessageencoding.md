---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3b5a8ff5fdf9e3da8824e7eb9443f71613899dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebmessageencodinggt"></a><span data-ttu-id="dae5a-102">&lt;webMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="dae5a-102">&lt;webMessageEncoding&gt;</span></span>
<span data-ttu-id="dae5a-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] バインディングで使用されるときに、プレーンテキストの XML、JSON (JavaScript Object Notation) メッセージ エンコーディング、および "生の" バイナリ コンテンツの読み取りと書き込みができるようにします。</span><span class="sxs-lookup"><span data-stu-id="dae5a-103">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] binding.</span></span>  
  
 <span data-ttu-id="dae5a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="dae5a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="dae5a-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="dae5a-105">\<bindings></span></span>  
<span data-ttu-id="dae5a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dae5a-106">\<customBinding></span></span>  
<span data-ttu-id="dae5a-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="dae5a-107">\<binding></span></span>  
<span data-ttu-id="dae5a-108">\<webMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="dae5a-108">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae5a-109">構文</span><span class="sxs-lookup"><span data-stu-id="dae5a-109">Syntax</span></span>  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dae5a-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dae5a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dae5a-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dae5a-112">属性</span><span class="sxs-lookup"><span data-stu-id="dae5a-112">Attributes</span></span>  
  
|<span data-ttu-id="dae5a-113">属性</span><span class="sxs-lookup"><span data-stu-id="dae5a-113">Attribute</span></span>|<span data-ttu-id="dae5a-114">説明</span><span class="sxs-lookup"><span data-stu-id="dae5a-114">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="dae5a-115">新しいリーダーを割り当てずに同時に読み取ることができるメッセージの数。</span><span class="sxs-lookup"><span data-stu-id="dae5a-115">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="dae5a-116">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="dae5a-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dae5a-117">既定値は、内部エンコーダー (Text、JSON、および raw (生)) ごとに 64 リーダーです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-117">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="dae5a-118">この数を増やすとメモリの消費量が増えますが、受信メッセージ数の急激な増加にエンコーダーが対処できるようになります。これは、作成済みのリーダーをプールから使用でき、新しいリーダーを作成する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-118">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="dae5a-119">新しいライターを割り当てずに同時に送信できるメッセージの数。</span><span class="sxs-lookup"><span data-stu-id="dae5a-119">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="dae5a-120">プール サイズを大きくすると、システムでは、比較的大きい作業セットで、アクティビティの急増に対する許容度が高まります。</span><span class="sxs-lookup"><span data-stu-id="dae5a-120">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="dae5a-121">既定値は、内部エンコーダー (Text、JSON、および raw (生)) ごとに 64 リーダーです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-121">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="dae5a-122">この数を増やすとメモリの消費が増えますが、送信メッセージ数の急激な増加にエンコーダーが対処できるようになります。これは、作成済みのライターをプールから使用でき、新しいライターを作成する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-122">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="dae5a-123">バインドでメッセージの発行に使用される文字セット エンコーディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-123">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="dae5a-124">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="dae5a-125">-UnicodeFffeTextEncoding: Unicode ビッグ エンディアン エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="dae5a-125">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="dae5a-126">-Utf16TextEncoding: Unicode エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="dae5a-126">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="dae5a-127">-Utf8TextEncoding: 8 ビット エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="dae5a-127">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="dae5a-128">既定値は Utf8TextEncoding です。</span><span class="sxs-lookup"><span data-stu-id="dae5a-128">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="dae5a-129">この属性は <xref:System.Text.Encoding> 型です。</span><span class="sxs-lookup"><span data-stu-id="dae5a-129">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dae5a-130">子要素</span><span class="sxs-lookup"><span data-stu-id="dae5a-130">Child Elements</span></span>  
  
|<span data-ttu-id="dae5a-131">要素</span><span class="sxs-lookup"><span data-stu-id="dae5a-131">Element</span></span>|<span data-ttu-id="dae5a-132">説明</span><span class="sxs-lookup"><span data-stu-id="dae5a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dae5a-133">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="dae5a-133">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="dae5a-134">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-134">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dae5a-135">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="dae5a-135">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dae5a-136">親要素</span><span class="sxs-lookup"><span data-stu-id="dae5a-136">Parent Elements</span></span>  
  
|<span data-ttu-id="dae5a-137">要素</span><span class="sxs-lookup"><span data-stu-id="dae5a-137">Element</span></span>|<span data-ttu-id="dae5a-138">説明</span><span class="sxs-lookup"><span data-stu-id="dae5a-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dae5a-139">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="dae5a-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="dae5a-140">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-140">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dae5a-141">コメント</span><span class="sxs-lookup"><span data-stu-id="dae5a-141">Remarks</span></span>  
 <span data-ttu-id="dae5a-142">エンコーディングは、メッセージをバイト シーケンスに変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-142">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="dae5a-143">デコードは、その逆のプロセスです。</span><span class="sxs-lookup"><span data-stu-id="dae5a-143">Decoding is the reverse process.</span></span> <span data-ttu-id="dae5a-144">これらのプロセスでは、文字エンコーディングの指定が必要です。</span><span class="sxs-lookup"><span data-stu-id="dae5a-144">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="dae5a-145">`webMessageEncoding` 要素は、プレーンテキストの XML と JSON エンコーディング、および "生" のバイナリ データの処理を、一連の内部エンコーダーに代行させることで機能します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-145">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="dae5a-146">この委任は、複合メッセージ エンコーダーによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-146">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="dae5a-147">このバインディング要素と複合エンコーダーは、`webHttpBinding` 要素によって使用される SOAP メッセージを使用しないシナリオでのエンコーディングを制御するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-147">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="dae5a-148">これらのシナリオには、POX ("Plain Old XML")、REST (Representational State Transfer)、RSS (Really Simple Syndication) と Atom 配信、および AJAX (Asynchronous JavaScript and XML) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-148">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="dae5a-149">複合メッセージ エンコーダーは SOAP または WS-Addressing をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="dae5a-149">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="dae5a-150">`writeEncoding` 属性を使用すると、バインディング要素に書き込みの文字エンコーディングを構成できます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-150">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="dae5a-151">指定された <xref:System.Text.Encoding> 値は、JSON およびテキスト形式の XML の場合の書き込みの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="dae5a-151">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="dae5a-152">読み取りについては、任意の有効なメッセージ エンコーディングとテキスト エンコーディングが認識されます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-152">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="dae5a-153">`maxReadPoolSize` と `maxWritePoolSize` を使用して、割り当てられるリーダーとライターの最大数をそれぞれ設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="dae5a-153">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="dae5a-154">既定では、64 のリーダーと 16 のライターが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="dae5a-154">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="dae5a-155">複雑さの制約は既定値を使用しても設定されて、 [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)サービス拒否 (DOS) のクラスを防ぐために要素がメッセージの複雑さを利用してエンドポイント処理を妨害するを試みるを攻撃リソース。</span><span class="sxs-lookup"><span data-stu-id="dae5a-155">Default complexity constraints are also set using the [\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dae5a-156">例</span><span class="sxs-lookup"><span data-stu-id="dae5a-156">Example</span></span>  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dae5a-157">参照</span><span class="sxs-lookup"><span data-stu-id="dae5a-157">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [<span data-ttu-id="dae5a-158">メッセージ エンコーディング</span><span class="sxs-lookup"><span data-stu-id="dae5a-158">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="dae5a-159">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="dae5a-159">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="dae5a-160">バインディング</span><span class="sxs-lookup"><span data-stu-id="dae5a-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dae5a-161">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="dae5a-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="dae5a-162">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="dae5a-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="dae5a-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="dae5a-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
