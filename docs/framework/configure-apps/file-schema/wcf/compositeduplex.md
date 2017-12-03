---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 292067daacc9319c144e9d0f2da9f27ca2fcf5b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="c0cd9-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="c0cd9-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="c0cd9-103">サービスがメッセージをクライアントに返送するためのエンドポイントをクライアントが公開する必要がある場合に使用される、バインド要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="c0cd9-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c0cd9-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-105">\<bindings></span></span>  
<span data-ttu-id="c0cd9-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-106">\<customBinding></span></span>  
<span data-ttu-id="c0cd9-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-107">\<binding></span></span>  
<span data-ttu-id="c0cd9-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cd9-109">構文</span><span class="sxs-lookup"><span data-stu-id="c0cd9-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0cd9-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c0cd9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0cd9-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0cd9-112">属性</span><span class="sxs-lookup"><span data-stu-id="c0cd9-112">Attributes</span></span>  
  
|<span data-ttu-id="c0cd9-113">属性</span><span class="sxs-lookup"><span data-stu-id="c0cd9-113">Attribute</span></span>|<span data-ttu-id="c0cd9-114">説明</span><span class="sxs-lookup"><span data-stu-id="c0cd9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0cd9-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="c0cd9-115">clientBaseAddress</span></span>|<span data-ttu-id="c0cd9-116">二重モードのバック チャネルのアドレスを設定する URI。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="c0cd9-117">サービスは、このアドレスを使用して、クライアントへのアクセス、接続の確立を行います。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="c0cd9-118">この属性が設定されていないかどうか、既定のアドレス"`full qualified name+default port\TemporaryIndigoAddress\guid`"が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="c0cd9-119">既定値は、`null` です。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0cd9-120">子要素</span><span class="sxs-lookup"><span data-stu-id="c0cd9-120">Child Elements</span></span>  
 <span data-ttu-id="c0cd9-121">なし</span><span class="sxs-lookup"><span data-stu-id="c0cd9-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0cd9-122">親要素</span><span class="sxs-lookup"><span data-stu-id="c0cd9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c0cd9-123">要素</span><span class="sxs-lookup"><span data-stu-id="c0cd9-123">Element</span></span>|<span data-ttu-id="c0cd9-124">説明</span><span class="sxs-lookup"><span data-stu-id="c0cd9-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0cd9-125">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c0cd9-126">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0cd9-127">コメント</span><span class="sxs-lookup"><span data-stu-id="c0cd9-127">Remarks</span></span>  
 <span data-ttu-id="c0cd9-128">たとえば HTTP のように、この構成要素はネイティブでの二重通信を許可しないトランスポートで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="c0cd9-129">これとは対照的に、TCP では、二重通信がネイティブで許可されているので、クライアントにメッセージを返信するためにこのバインディング要素をサービスで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="c0cd9-130">クライアントは、サービスのアドレスを公開して、アクセスおよび接続の確立ができるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="c0cd9-131">このクライアント アドレスは、`clientBaseAddress` 属性によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="c0cd9-132">ClientBaseAddress がユーザーによって明示的に設定されていない場合は、WCF (Windows Communication Foundation) によって自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="c0cd9-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0cd9-133">例</span><span class="sxs-lookup"><span data-stu-id="c0cd9-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0cd9-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0cd9-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c0cd9-135">バインディング</span><span class="sxs-lookup"><span data-stu-id="c0cd9-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c0cd9-136">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="c0cd9-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c0cd9-137">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="c0cd9-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c0cd9-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c0cd9-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
