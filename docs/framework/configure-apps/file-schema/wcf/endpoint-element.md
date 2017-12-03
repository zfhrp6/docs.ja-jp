---
title: "&lt;endpoint&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c466d7f7f00d7fd2358f0d5d71c0b705f316f66f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointgt-element"></a><span data-ttu-id="4a31e-102">&lt;endpoint&gt; 要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-102">&lt;endpoint&gt; element</span></span>
<span data-ttu-id="4a31e-103">サービスの公開に使用されるサービス エンドポイントのバインディング、コントラクト、およびアドレスのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="4a31e-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="4a31e-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4a31e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a31e-105">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="4a31e-105">\<service></span></span>  
<span data-ttu-id="4a31e-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="4a31e-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a31e-107">構文</span><span class="sxs-lookup"><span data-stu-id="4a31e-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a31e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4a31e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a31e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a31e-110">属性</span><span class="sxs-lookup"><span data-stu-id="4a31e-110">Attributes</span></span>  
  
|<span data-ttu-id="4a31e-111">属性</span><span class="sxs-lookup"><span data-stu-id="4a31e-111">Attribute</span></span>|<span data-ttu-id="4a31e-112">説明</span><span class="sxs-lookup"><span data-stu-id="4a31e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a31e-113">address</span><span class="sxs-lookup"><span data-stu-id="4a31e-113">address</span></span>|<span data-ttu-id="4a31e-114">エンドポイントのアドレスを含む文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="4a31e-115">アドレスは、絶対または相対アドレスとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="4a31e-116">相対アドレスが提供されている場合、ホストは、そのバインディングで使用されるトランスポート スキームに適したベース アドレスが提供されることを想定します。</span><span class="sxs-lookup"><span data-stu-id="4a31e-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="4a31e-117">アドレスが構成されていない場合、ベース アドレスはそのエンドポイントのアドレスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="4a31e-118">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a31e-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a31e-119">behaviorConfiguration</span></span>|<span data-ttu-id="4a31e-120">エンドポイントで使用される動作の名前を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="4a31e-121">バインド</span><span class="sxs-lookup"><span data-stu-id="4a31e-121">binding</span></span>|<span data-ttu-id="4a31e-122">使用するバインディングの種類を指定する必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="4a31e-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="4a31e-123">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="4a31e-124">種類は、バインディングの種類の名前ではなくセクション名で登録されます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="4a31e-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a31e-125">bindingConfiguration</span></span>|<span data-ttu-id="4a31e-126">エンドポイントがインスタンス化されるときに使用するバインディングのバインディング名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="4a31e-127">バインディング名は、エンドポイントが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="4a31e-128">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4a31e-129">この属性は、構成ファイル内の特定のバインディング構成を参照するために、`binding` と組み合わせて使用されます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="4a31e-130">カスタム バインディングを使用しようとする場合にこの属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="4a31e-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="4a31e-131">そうでない場合は、例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="4a31e-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="4a31e-132">bindingName</span></span>|<span data-ttu-id="4a31e-133">WSDL を介した定義エクスポートに使用するバインディングの一意の修飾名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="4a31e-134">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a31e-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="4a31e-135">bindingNamespace</span></span>|<span data-ttu-id="4a31e-136">WSDL を介した定義エクスポートに使用するバインディングの名前空間の修飾名を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="4a31e-137">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a31e-138">コントラクト</span><span class="sxs-lookup"><span data-stu-id="4a31e-138">contract</span></span>|<span data-ttu-id="4a31e-139">このエンドポイントが公開するコントラクトを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="4a31e-140">アセンブリは、コントラクト型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="4a31e-141">サービス実装が単一のコントラクトの型を実装する場合は、このプロパティを省略できます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="4a31e-142">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a31e-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a31e-143">endpointConfiguration</span></span>|<span data-ttu-id="4a31e-144">この標準エンドポイントの追加の構成情報を参照する `kind` 属性によって設定される標準エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="4a31e-145">同じ名前を `<standardEndpoints>` セクションに定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="4a31e-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="4a31e-146">isSystemEndpoint</span></span>|<span data-ttu-id="4a31e-147">インフラストラクチャ エンドポイントであるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="4a31e-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="4a31e-148">kind</span><span class="sxs-lookup"><span data-stu-id="4a31e-148">kind</span></span>|<span data-ttu-id="4a31e-149">適用する標準エンドポイントの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="4a31e-150">種類は `<extensions>` セクションまたは machine.config に登録する必要があります。何も指定されていない場合は、共通のサービス エンドポイントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="4a31e-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="4a31e-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="4a31e-151">listenUriMode</span></span>|<span data-ttu-id="4a31e-152">リッスンするサービスに提供される `ListenUri` をトランスポートが処理する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a31e-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="4a31e-153">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4a31e-153">Valid values are</span></span><br /><br /> <span data-ttu-id="4a31e-154">明示的</span><span class="sxs-lookup"><span data-stu-id="4a31e-154">-   Explicit</span></span><br /><span data-ttu-id="4a31e-155">一意</span><span class="sxs-lookup"><span data-stu-id="4a31e-155">-   Unique</span></span><br /><br /> <span data-ttu-id="4a31e-156">既定値は Explicit です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="4a31e-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="4a31e-157">listenUri</span></span>|<span data-ttu-id="4a31e-158">サービス エンドポイントがリッスンする URI を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="4a31e-159">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a31e-160">name</span><span class="sxs-lookup"><span data-stu-id="4a31e-160">name</span></span>|<span data-ttu-id="4a31e-161">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-161">Optional attribute.</span></span> <span data-ttu-id="4a31e-162">サービス エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4a31e-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="4a31e-163">既定値は、バインディング名とコントラクトの説明の名前を連結した値です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="4a31e-164">サービスには複数のエンドポイントが存在する場合があるため、エンドポイントの `name` 属性はサービスの名前とは異なります。</span><span class="sxs-lookup"><span data-stu-id="4a31e-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a31e-165">子要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-165">Child Elements</span></span>  
  
|<span data-ttu-id="4a31e-166">要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-166">Element</span></span>|<span data-ttu-id="4a31e-167">説明</span><span class="sxs-lookup"><span data-stu-id="4a31e-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a31e-168">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="4a31e-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="4a31e-169">アドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="4a31e-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="4a31e-170">\<id ></span><span class="sxs-lookup"><span data-stu-id="4a31e-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4a31e-171">メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a31e-172">親要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-172">Parent Elements</span></span>  
  
|<span data-ttu-id="4a31e-173">要素</span><span class="sxs-lookup"><span data-stu-id="4a31e-173">Element</span></span>|<span data-ttu-id="4a31e-174">説明</span><span class="sxs-lookup"><span data-stu-id="4a31e-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a31e-175">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="4a31e-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="4a31e-176">クライアントが接続可能なエンドポイントの一覧を定義する設定セクションです。</span><span class="sxs-lookup"><span data-stu-id="4a31e-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4a31e-177">例</span><span class="sxs-lookup"><span data-stu-id="4a31e-177">Example</span></span>  
 <span data-ttu-id="4a31e-178">これはサービス エンドポイントの構成の例です。</span><span class="sxs-lookup"><span data-stu-id="4a31e-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a31e-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a31e-179">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [<span data-ttu-id="4a31e-180">エンドポイント: アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="4a31e-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="4a31e-181">方法: 構成でサービス エンドポイントの作成</span><span class="sxs-lookup"><span data-stu-id="4a31e-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
