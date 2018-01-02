---
title: "&lt;サービス&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 689dfae90baffa3e9895258d1635c7840d8df6b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicegt"></a><span data-ttu-id="77ca7-102">&lt;サービス&gt;</span><span class="sxs-lookup"><span data-stu-id="77ca7-102">&lt;service&gt;</span></span>
<span data-ttu-id="77ca7-103">`service` 要素には Windows Communication Foundation (WCF) サービスの設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="77ca7-104">また、サービスを公開するエンドポイントも含まれます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="77ca7-105">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="77ca7-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="77ca7-106">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="77ca7-106">\<services></span></span>  
<span data-ttu-id="77ca7-107">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="77ca7-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ca7-108">構文</span><span class="sxs-lookup"><span data-stu-id="77ca7-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77ca7-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="77ca7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="77ca7-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77ca7-111">属性</span><span class="sxs-lookup"><span data-stu-id="77ca7-111">Attributes</span></span>  
  
|<span data-ttu-id="77ca7-112">属性</span><span class="sxs-lookup"><span data-stu-id="77ca7-112">Attribute</span></span>|<span data-ttu-id="77ca7-113">説明</span><span class="sxs-lookup"><span data-stu-id="77ca7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77ca7-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="77ca7-114">behaviorConfiguration</span></span>|<span data-ttu-id="77ca7-115">サービスのインスタンス化に使用される動作の動作名を含む文字列。</span><span class="sxs-lookup"><span data-stu-id="77ca7-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="77ca7-116">動作名は、サービスが定義される時点でスコープ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="77ca7-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="77ca7-117">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="77ca7-118">name</span><span class="sxs-lookup"><span data-stu-id="77ca7-118">name</span></span>|<span data-ttu-id="77ca7-119">インスタンス化するサービスの型を指定する必須の文字列属性。</span><span class="sxs-lookup"><span data-stu-id="77ca7-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="77ca7-120">この設定は有効な型と同じでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="77ca7-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="77ca7-121">形式は、`Namespace.Class.` です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77ca7-122">子要素</span><span class="sxs-lookup"><span data-stu-id="77ca7-122">Child Elements</span></span>  
  
|<span data-ttu-id="77ca7-123">要素</span><span class="sxs-lookup"><span data-stu-id="77ca7-123">Element</span></span>|<span data-ttu-id="77ca7-124">説明</span><span class="sxs-lookup"><span data-stu-id="77ca7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77ca7-125">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="77ca7-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="77ca7-126">このサービスを公開する `endpoint` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="77ca7-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="77ca7-127">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="77ca7-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="77ca7-128">このサービス インスタンスのホストを指定します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="77ca7-129">この要素は <xref:System.ServiceModel.Configuration.HostElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77ca7-130">親要素</span><span class="sxs-lookup"><span data-stu-id="77ca7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="77ca7-131">要素</span><span class="sxs-lookup"><span data-stu-id="77ca7-131">Element</span></span>|<span data-ttu-id="77ca7-132">説明</span><span class="sxs-lookup"><span data-stu-id="77ca7-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77ca7-133">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="77ca7-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="77ca7-134">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77ca7-135">コメント</span><span class="sxs-lookup"><span data-stu-id="77ca7-135">Remarks</span></span>  
 <span data-ttu-id="77ca7-136">サービスは、設定ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="77ca7-137">アセンブリには、任意の数のサービスを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="77ca7-138">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="77ca7-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="77ca7-139">このセクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="77ca7-140">`behaviorConfiguration` 要素も省略可能です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="77ca7-141">サービスが使用する動作を識別します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="77ca7-142">この属性で指定された動作は、同じ設定ファイルの範囲にある動作にリンクしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="77ca7-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="77ca7-143">各サービスでは、固有のアドレスとバインディングを持つ 1 つまたは複数のエンドポイントが公開されます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="77ca7-144">構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。</span><span class="sxs-lookup"><span data-stu-id="77ca7-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="77ca7-145">バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="77ca7-146">`name` 属性は、バインディングが定義されているセクションを示します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="77ca7-147">`bindingConfiguration` 属性は、バインディング セクション内の使用される構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="77ca7-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="77ca7-148">バインディング セクションでは、複数の設定を定義できます。</span><span class="sxs-lookup"><span data-stu-id="77ca7-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77ca7-149">例</span><span class="sxs-lookup"><span data-stu-id="77ca7-149">Example</span></span>  
 <span data-ttu-id="77ca7-150">これはサービスの構成の例です。</span><span class="sxs-lookup"><span data-stu-id="77ca7-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77ca7-151">参照</span><span class="sxs-lookup"><span data-stu-id="77ca7-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="77ca7-152">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="77ca7-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
