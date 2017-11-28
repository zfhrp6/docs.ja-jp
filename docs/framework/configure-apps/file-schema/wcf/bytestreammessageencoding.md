---
title: '&lt;byteStreamMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1788300407ad84a5ff7e3929eaa728f5399961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbytestreammessageencodinggt"></a><span data-ttu-id="9c5ee-102">&lt;byteStreamMessageEncoding&gt;</span><span class="sxs-lookup"><span data-stu-id="9c5ee-102">&lt;byteStreamMessageEncoding&gt;</span></span>
<span data-ttu-id="9c5ee-103">文字エンコーディングを指定するオプションを使用し、メッセージ エンコーディングをバイト ストリームとして指定します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-103">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
 <span data-ttu-id="9c5ee-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9c5ee-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-105">\<bindings></span></span>  
<span data-ttu-id="9c5ee-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-106">\<customBinding></span></span>  
<span data-ttu-id="9c5ee-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-107">\<binding></span></span>  
<span data-ttu-id="9c5ee-108">\<binaryMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-108">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c5ee-109">構文</span><span class="sxs-lookup"><span data-stu-id="9c5ee-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c5ee-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9c5ee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9c5ee-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c5ee-112">属性</span><span class="sxs-lookup"><span data-stu-id="9c5ee-112">Attributes</span></span>  
  
|<span data-ttu-id="9c5ee-113">属性</span><span class="sxs-lookup"><span data-stu-id="9c5ee-113">Attribute</span></span>|<span data-ttu-id="9c5ee-114">説明</span><span class="sxs-lookup"><span data-stu-id="9c5ee-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c5ee-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="9c5ee-115">messageVersion</span></span>|<span data-ttu-id="9c5ee-116">バインディングを使用して送信されたメッセージの SOAP バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="9c5ee-117">このプロパティは、<xref:System.ServiceModel.Channels.MessageVersion.None%2A> のメッセージ バージョン値にのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="9c5ee-118">バイト ストリーム メッセージ エンコーダーは、他のメッセージ バージョンをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="9c5ee-119">この属性は <xref:System.ServiceModel.Channels.MessageVersion> 型です。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c5ee-120">子要素</span><span class="sxs-lookup"><span data-stu-id="9c5ee-120">Child Elements</span></span>  
  
|<span data-ttu-id="9c5ee-121">要素</span><span class="sxs-lookup"><span data-stu-id="9c5ee-121">Element</span></span>|<span data-ttu-id="9c5ee-122">説明</span><span class="sxs-lookup"><span data-stu-id="9c5ee-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c5ee-123">\<ある readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-123">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="9c5ee-124">このバインドを使用して設定されるエンドポイントにより処理可能な、SOAP メッセージの複雑さに対する制約を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="9c5ee-125">この要素は <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c5ee-126">親要素</span><span class="sxs-lookup"><span data-stu-id="9c5ee-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9c5ee-127">要素</span><span class="sxs-lookup"><span data-stu-id="9c5ee-127">Element</span></span>|<span data-ttu-id="9c5ee-128">説明</span><span class="sxs-lookup"><span data-stu-id="9c5ee-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c5ee-129">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-129">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9c5ee-130">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c5ee-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c5ee-131">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>  
 [<span data-ttu-id="9c5ee-132">メッセージのエンコード</span><span class="sxs-lookup"><span data-stu-id="9c5ee-132">Message Encoding</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [<span data-ttu-id="9c5ee-133">メッセージ エンコーダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="9c5ee-133">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [<span data-ttu-id="9c5ee-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="9c5ee-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9c5ee-135">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="9c5ee-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9c5ee-136">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="9c5ee-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9c5ee-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9c5ee-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
