---
title: '&lt;netNamedPipeBinding&gt; の &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9116532c8b4aae2f7539706b97d564444195c79d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753145"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="a20f4-102">&lt;netNamedPipeBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="a20f4-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="a20f4-103">名前付きパイプのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a20f4-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="a20f4-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a20f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a20f4-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a20f4-105">\<bindings></span></span>  
<span data-ttu-id="a20f4-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a20f4-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="a20f4-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="a20f4-107">\<binding></span></span>  
<span data-ttu-id="a20f4-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="a20f4-108">\<security></span></span>  
<span data-ttu-id="a20f4-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a20f4-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a20f4-110">構文</span><span class="sxs-lookup"><span data-stu-id="a20f4-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a20f4-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a20f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a20f4-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a20f4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a20f4-113">属性</span><span class="sxs-lookup"><span data-stu-id="a20f4-113">Attributes</span></span>  
  
|<span data-ttu-id="a20f4-114">属性</span><span class="sxs-lookup"><span data-stu-id="a20f4-114">Attribute</span></span>|<span data-ttu-id="a20f4-115">説明</span><span class="sxs-lookup"><span data-stu-id="a20f4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a20f4-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a20f4-116">protectionLevel</span></span>|<span data-ttu-id="a20f4-117">名前付きパイプの保護レベルを定義します。</span><span class="sxs-lookup"><span data-stu-id="a20f4-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="a20f4-118">メッセージに署名すると、転送中のメッセージが第三者によって改ざんされるリスクを軽減します。</span><span class="sxs-lookup"><span data-stu-id="a20f4-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a20f4-119">暗号化により、転送中にデータレベルのプライバシーが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a20f4-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a20f4-120">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="a20f4-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a20f4-121">-None: 保護されません。</span><span class="sxs-lookup"><span data-stu-id="a20f4-121">-   None: No protection.</span></span><br /><span data-ttu-id="a20f4-122">-Sign: メッセージは署名されます。</span><span class="sxs-lookup"><span data-stu-id="a20f4-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a20f4-123">-EncryptAndSign: メッセージが暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="a20f4-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a20f4-124">既定値は EncryptAndSign です。</span><span class="sxs-lookup"><span data-stu-id="a20f4-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a20f4-125">子要素</span><span class="sxs-lookup"><span data-stu-id="a20f4-125">Child Elements</span></span>  
 <span data-ttu-id="a20f4-126">なし</span><span class="sxs-lookup"><span data-stu-id="a20f4-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a20f4-127">親要素</span><span class="sxs-lookup"><span data-stu-id="a20f4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a20f4-128">要素</span><span class="sxs-lookup"><span data-stu-id="a20f4-128">Element</span></span>|<span data-ttu-id="a20f4-129">説明</span><span class="sxs-lookup"><span data-stu-id="a20f4-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a20f4-130">\<security></span><span class="sxs-lookup"><span data-stu-id="a20f4-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="a20f4-131">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a20f4-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a20f4-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="a20f4-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="a20f4-133">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a20f4-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a20f4-134">バインディング</span><span class="sxs-lookup"><span data-stu-id="a20f4-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a20f4-135">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="a20f4-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a20f4-136">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="a20f4-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a20f4-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="a20f4-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
