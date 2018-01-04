---
title: "Windows Communication Foundation サービスのバインディングの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11810e0a39c5b6091a63ef33e5abfccb95b7555
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="f2926-102">Windows Communication Foundation サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="f2926-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="f2926-103">アプリケーションの作成では、アプリケーションの配置後は各種決定事項を管理者に任せる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="f2926-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="f2926-104">たとえば、どのサービス アドレス (URI (Uniform Resource Identifier)) を使用するかなどの情報は、多くの場合、前もって知る方法がありません。</span><span class="sxs-lookup"><span data-stu-id="f2926-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="f2926-105">アドレスをハードコーディングする代わりに、サービスの作成後に管理者が指定する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="f2926-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="f2926-106">構成を活用することで、この柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="f2926-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2926-107">使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)で、`/config`スイッチを構成ファイルをすばやく作成します。</span><span class="sxs-lookup"><span data-stu-id="f2926-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="f2926-108">主要なセクション</span><span class="sxs-lookup"><span data-stu-id="f2926-108">Major Sections</span></span>  
 <span data-ttu-id="f2926-109">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 構成スキームは、3 つの主要なセクション (`serviceModel`、`bindings`、および `services`) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f2926-109">The [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="f2926-110">ServiceModel 要素</span><span class="sxs-lookup"><span data-stu-id="f2926-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="f2926-111">区切られたセクションを使用することができます、`system.ServiceModel`サービスの設定と同様に、1 つまたは複数のエンドポイント サービスの種類を構成する要素。</span><span class="sxs-lookup"><span data-stu-id="f2926-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="f2926-112">各エンドポイントでは、アドレス、コントラクト、およびバインディングをそれぞれ 1 つずつ構成できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f2926-113">エンドポイントを参照してください[エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2926-113"> endpoints, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="f2926-114">エンドポイントを指定しない場合、ランタイムは、既定のエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f2926-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f2926-115"> については、「 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) 」および「 [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f2926-115"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="f2926-116">バインディングはトランスポート (HTTP、TCP、パイプ、およびメッセージ キュー) とプロトコル (セキュリティ、信頼性、およびトランザクション フロー) を指定し、バインド要素で構成されます。各バインド要素は、エンドポイントの通信方法のさまざまな側面を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2926-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="f2926-117">たとえば、指定すると、 [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)要素は、エンドポイントのトランスポートとして HTTP を使用することを示します。</span><span class="sxs-lookup"><span data-stu-id="f2926-117">For example, specifying the [\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="f2926-118">このエンドポイントを使用するサービスが開かれる実行時に、エンドポイントとの接続に HTTP が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2926-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="f2926-119">バインディングには、定義済みバインディングとカスタム バインドの 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="f2926-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="f2926-120">定義済みバインディングには、一般的なシナリオで使用される要素の組み合わせが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f2926-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="f2926-121">定義済みバインディングの一覧を型には、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]提供を参照してください[システム指定のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2926-121">For a list of predefined binding types that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provides, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="f2926-122">定義済みバインディング コレクションに、サービス アプリケーションに必要な正しい機能の組み合わせがないときは、カスタム バインドを作成して、そのアプリケーションの要件を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="f2926-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="f2926-123">カスタム バインディングを参照してください[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2926-123"> custom bindings, see [\<customBinding>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="f2926-124">次の 4 つの例は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの設定に使用される最も一般的なバインディング構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2926-124">The following four examples illustrate the most common binding configurations used for setting up a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="f2926-125">バインディングの種類を使用するエンドポイントの指定</span><span class="sxs-lookup"><span data-stu-id="f2926-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="f2926-126">最初の例は、アドレス、コントラクト、およびバインディングをそれぞれ 1 つずつ使用して構成されたエンドポイントを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f2926-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!—- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="f2926-127">この例では、`name` 属性は、構成がどのサービス型に対するものであるかを示します。</span><span class="sxs-lookup"><span data-stu-id="f2926-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="f2926-128">`HelloWorld` コントラクトを使用してコードでサービスを作成すると、そのサービスは、この例の構成に定義されているすべてのエンドポイントと共に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f2926-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="f2926-129">アセンブリには、1 つのサービス コントラクトが実装されている場合、`name`サービスでのみ使用可能な型が使用するため、属性を省略できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="f2926-130">この属性が受け取る文字列は、`Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null` の形式で指定される必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2926-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="f2926-131">`address` 属性では、他のエンドポイントがこのサービスと通信するために使用する URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2926-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="f2926-132">この URI は、絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f2926-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="f2926-133">相対アドレスを指定すると、ホストは、そのバインディングで使用されるトランスポート スキームに適したベース アドレスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f2926-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="f2926-134">アドレスが構成されていない場合、ベース アドレスはそのエンドポイントのアドレスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="f2926-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="f2926-135">`contract` 属性では、このエンドポイントが公開するコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2926-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="f2926-136">サービス実装の型は、コントラクト型を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2926-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="f2926-137">サービス実装が単一のコントラクトの型を実装する場合は、このプロパティを省略できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="f2926-138">`binding` 属性では、この特定のエンドポイントに使用される定義済みバインディングまたはカスタム バインディングを選択します。</span><span class="sxs-lookup"><span data-stu-id="f2926-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="f2926-139">バインディングが明示的に選択されていないエンドポイントでは、既定のバインディング選択 (`BasicHttpBinding`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f2926-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="f2926-140">定義済みバインディングの変更</span><span class="sxs-lookup"><span data-stu-id="f2926-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="f2926-141">次の例では、定義済みバインディングを変更します。</span><span class="sxs-lookup"><span data-stu-id="f2926-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="f2926-142">これにより、サービスの任意のエンドポイントを構成するために使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f2926-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="f2926-143">バインディングの変更では、<xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> 値を 1 秒に設定します。</span><span class="sxs-lookup"><span data-stu-id="f2926-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="f2926-144">このプロパティは、<xref:System.TimeSpan> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f2926-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="f2926-145">変更されたバインディングは、バインディング セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="f2926-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="f2926-146">この変更したバインディングは、`binding` 要素の `endpoint` 属性を設定することにより、任意のエンドポイントを作成するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2926-147">バインディングに特定の名前を付ける場合、サービス エンドポイントで指定した `bindingConfiguration` と同じ名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2926-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="f2926-148">サービスに適用する動作の構成</span><span class="sxs-lookup"><span data-stu-id="f2926-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="f2926-149">次の例では、サービス型に対して、特定の動作を構成します。</span><span class="sxs-lookup"><span data-stu-id="f2926-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="f2926-150">`ServiceMetadataBehavior`要素を使用して有効にする、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をサービスに照会し、メタデータから Web サービス記述言語 (WSDL) ドキュメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="f2926-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2926-151">動作に特定の名前を付ける場合、サービスまたはエンドポイント セクションで指定した `behaviorConfiguration` と同じ名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2926-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="f2926-152">前の構成では、クライアントが "HelloWorld" の型指定されたサービスを呼び出してメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="f2926-153">異なるバインディング値を使用する 2 つのエンドポイントを持つサービスの指定</span><span class="sxs-lookup"><span data-stu-id="f2926-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="f2926-154">この最後の例では、`HelloWorld` サービス型に 2 つのエンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f2926-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="f2926-155">各エンドポイントを使用して異なるカスタマイズ`bindingConfiguration`同じバインドの種類の属性 (それぞれを変更、 `basicHttpBinding`)。</span><span class="sxs-lookup"><span data-stu-id="f2926-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="f2926-156">次の例に示すように、`protocolMapping` セクションを追加してバインディングを構成することによって、既定の構成を使用する同じ動作を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f2926-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2926-157">参照</span><span class="sxs-lookup"><span data-stu-id="f2926-157">See Also</span></span>  
 [<span data-ttu-id="f2926-158">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="f2926-158">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="f2926-159">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="f2926-159">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="f2926-160">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="f2926-160">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [<span data-ttu-id="f2926-161">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="f2926-161">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
