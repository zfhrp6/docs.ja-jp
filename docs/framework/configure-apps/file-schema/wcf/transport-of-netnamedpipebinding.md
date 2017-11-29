---
title: "&lt;netNamedPipeBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 00f4ddfd218e8797aa2089a21081ee711be316d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="92666-102">&lt;netNamedPipeBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="92666-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="92666-103">名前付きパイプのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="92666-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="92666-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="92666-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92666-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92666-105">\<bindings></span></span>  
<span data-ttu-id="92666-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="92666-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="92666-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92666-107">\<binding></span></span>  
<span data-ttu-id="92666-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="92666-108">\<security></span></span>  
<span data-ttu-id="92666-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="92666-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92666-110">構文</span><span class="sxs-lookup"><span data-stu-id="92666-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92666-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="92666-111">Attributes and Elements</span></span>  
 <span data-ttu-id="92666-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="92666-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92666-113">属性</span><span class="sxs-lookup"><span data-stu-id="92666-113">Attributes</span></span>  
  
|<span data-ttu-id="92666-114">属性</span><span class="sxs-lookup"><span data-stu-id="92666-114">Attribute</span></span>|<span data-ttu-id="92666-115">説明</span><span class="sxs-lookup"><span data-stu-id="92666-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92666-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="92666-116">protectionLevel</span></span>|<span data-ttu-id="92666-117">名前付きパイプの保護レベルを定義します。</span><span class="sxs-lookup"><span data-stu-id="92666-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="92666-118">メッセージに署名すると、転送中のメッセージが第三者によって改ざんされるリスクを軽減します。</span><span class="sxs-lookup"><span data-stu-id="92666-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="92666-119">暗号化により、転送中にデータレベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="92666-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="92666-120">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="92666-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92666-121">-None: 保護されません。</span><span class="sxs-lookup"><span data-stu-id="92666-121">-   None: No protection.</span></span><br /><span data-ttu-id="92666-122">-Sign: メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="92666-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="92666-123">-EncryptAndSign: メッセージが暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="92666-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="92666-124">既定値は EncryptAndSign です。</span><span class="sxs-lookup"><span data-stu-id="92666-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92666-125">子要素</span><span class="sxs-lookup"><span data-stu-id="92666-125">Child Elements</span></span>  
 <span data-ttu-id="92666-126">なし</span><span class="sxs-lookup"><span data-stu-id="92666-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92666-127">親要素</span><span class="sxs-lookup"><span data-stu-id="92666-127">Parent Elements</span></span>  
  
|<span data-ttu-id="92666-128">要素</span><span class="sxs-lookup"><span data-stu-id="92666-128">Element</span></span>|<span data-ttu-id="92666-129">説明</span><span class="sxs-lookup"><span data-stu-id="92666-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92666-130">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="92666-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="92666-131">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="92666-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92666-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="92666-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="92666-133">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="92666-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="92666-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="92666-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="92666-135">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="92666-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="92666-136">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="92666-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="92666-137">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="92666-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
