---
title: "動作を使用したランタイムの構成と拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aab2d1d8c676a70b0fb4cfa80a16d52cd6f8b800
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a><span data-ttu-id="372b0-102">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="372b0-102">Configuring and Extending the Runtime with Behaviors</span></span>
<span data-ttu-id="372b0-103">動作を使用すると、既定の動作を変更したり、カスタム拡張機能を追加したりできます。カスタム拡張機能では、サービス構成の検査および検証や、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント アプリケーションとサービス アプリケーションのランタイム動作の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="372b0-103">Behaviors enable you to modify default behavior and add custom extensions that inspect and validate service configuration or modify runtime behavior in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service applications.</span></span> <span data-ttu-id="372b0-104">ここでは、動作インターフェイスとその実装方法について説明します。また、動作インターフェイスをサービスの説明 (サービス アプリケーションの場合) またはエンドポイント (クライアント アプリケーションの場合) にプログラムによって追加する方法と、構成ファイル内で追加する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="372b0-104">This topic describes the behavior interfaces, how to implement them, and how to add them to the service description (in a service application) or endpoint (in a client application) programmatically or in a configuration file.</span></span> <span data-ttu-id="372b0-105">詳細については、システム指定の動作を使用して、次を参照してください。[サービスの実行時の動作を指定する](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)と[クライアントの実行時の動作を指定する](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="372b0-105">For more information about using system-provided behaviors, see [Specifying Service Run-Time Behavior](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) and [Specifying Client Run-Time Behavior](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).</span></span>  
  
## <a name="behaviors"></a><span data-ttu-id="372b0-106">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="372b0-106">Behaviors</span></span>  
 <span data-ttu-id="372b0-107">動作の型は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] がサービス説明オブジェクト (サービスの場合) またはサービス エンド ポイント説明オブジェクト (クライアントの場合) を使用してランタイムを作成する前に、これらのオブジェクトに追加されます。このランタイムは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスまたは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="372b0-107">Behavior types are added to the service or service endpoint description objects (on the service or client, respectively) before those objects are used by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a runtime that executes a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="372b0-108">ランタイムの構築プロセスでこれらの動作を呼び出すと、コントラクト、バインディング、およびアドレスによって構築されたランタイムを変更するランタイム プロパティやランタイム メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-108">When these behaviors are called during the runtime construction process they are then able to access runtime properties and methods that modify the runtime constructed by the contract, bindings, and addresses.</span></span>  
  
### <a name="behavior-methods"></a><span data-ttu-id="372b0-109">動作メソッド</span><span class="sxs-lookup"><span data-stu-id="372b0-109">Behavior Methods</span></span>  
 <span data-ttu-id="372b0-110">すべての動作で、`AddBindingParameters` メソッド、`ApplyDispatchBehavior` メソッド、`Validate` メソッド、および `ApplyClientBehavior` メソッドを使用できます。ただし、<xref:System.ServiceModel.Description.IServiceBehavior> には、例外が 1 つあります。`ApplyClientBehavior` はクライアントで実行できないため、このメソッドを実装していません。</span><span class="sxs-lookup"><span data-stu-id="372b0-110">All behaviors have an `AddBindingParameters` method, an `ApplyDispatchBehavior` method, a `Validate` method, and an `ApplyClientBehavior` method with one exception: Because <xref:System.ServiceModel.Description.IServiceBehavior> cannot execute in a client, it does not implement `ApplyClientBehavior`.</span></span>  
  
-   <span data-ttu-id="372b0-111">カスタム オブジェクトを変更したり、ランタイム構築時に使用するためにカスタム バインディングがアクセスできるコレクションにカスタム オブジェクトを追加したりするには、`AddBindingParameters` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-111">Use the `AddBindingParameters` method to modify or add custom objects to a collection that custom bindings can access for their use when the runtime is constructed.</span></span> <span data-ttu-id="372b0-112">たとえば、これによって、チャネルを構築する方法に影響するが、チャネル開発者には知られていない保護要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="372b0-112">For example, this how protection requirements are specified that affect the way the channel is built, but are not known by the channel developer.</span></span>  
  
-   <span data-ttu-id="372b0-113">説明ツリーと対応するランタイム オブジェクトを検査し、特定の基準セットに従っていることを確認するには、`Validate` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-113">Use the `Validate` method to examine the description tree and corresponding runtime object to ensure it conforms to some set of criteria.</span></span>  
  
-   <span data-ttu-id="372b0-114">説明ツリーを検査し、サービスまたはクライアントの特定のスコープのランタイムを変更するには、`ApplyDispatchBehavior` メソッドと `ApplyClientBehavior` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-114">Use the `ApplyDispatchBehavior` and `ApplyClientBehavior` methods to examine the description tree and modify the runtime for a particular scope on either the service or the client.</span></span> <span data-ttu-id="372b0-115">また、拡張オブジェクトを挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-115">You can also insert extension objects as well.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="372b0-116">これらのメソッドでは説明ツリーが提供されますが、説明ツリーは検査にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-116">Although a description tree is provided in these methods, it is for examination only.</span></span> <span data-ttu-id="372b0-117">説明ツリーを変更すると、動作は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="372b0-117">If a description tree is modified, the behavior is undefined.</span></span>  
  
 <span data-ttu-id="372b0-118">変更できるプロパティと実装できるカスタマイズ インターフェイスには、サービスおよびクライアントのランタイム クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-118">The properties you can modify and the customization interfaces you can implement are accessed through the service and client runtime classes.</span></span> <span data-ttu-id="372b0-119">サービス型は、<xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスと <xref:System.ServiceModel.Dispatcher.DispatchOperation> クラスです。</span><span class="sxs-lookup"><span data-stu-id="372b0-119">The service types are the <xref:System.ServiceModel.Dispatcher.DispatchRuntime> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes.</span></span> <span data-ttu-id="372b0-120">クライアント型は、<xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスと <xref:System.ServiceModel.Dispatcher.ClientOperation> クラスです。</span><span class="sxs-lookup"><span data-stu-id="372b0-120">The client types are the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.ClientOperation> classes.</span></span> <span data-ttu-id="372b0-121"><xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスと <xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスは、それぞれクライアント全体またはサービス全体のランタイム プロパティと拡張コレクションにアクセスするための拡張エントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="372b0-121">The <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes are the extensibility entry points to access client-wide and service-wide runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="372b0-122">同様に、<xref:System.ServiceModel.Dispatcher.ClientOperation> クラスと <xref:System.ServiceModel.Dispatcher.DispatchOperation> クラスは、それぞれクライアント操作またはサービス操作のランタイム プロパティと拡張コレクションを公開します。</span><span class="sxs-lookup"><span data-stu-id="372b0-122">Similarly, the <xref:System.ServiceModel.Dispatcher.ClientOperation> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes expose client operation and service operation runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="372b0-123">ただし、必要に応じて、操作ランタイム オブジェクトからより広いスコープのランタイム オブジェクトにアクセスできます。また、逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="372b0-123">You can, however, access the wider scoped runtime object from the operation runtime object and vice versa if need be.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="372b0-124">ランタイム プロパティと、クライアントの実行動作を変更に使用できる拡張機能の種類の詳細については、次を参照してください。[を拡張するクライアント](../../../../docs/framework/wcf/extending/extending-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="372b0-124">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a client, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="372b0-125">ランタイム プロパティと、サービス ディスパッチャの実行動作を変更に使用できる拡張機能の種類の詳細については、次を参照してください。[ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)です。</span><span class="sxs-lookup"><span data-stu-id="372b0-125">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a service dispatcher, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
 <span data-ttu-id="372b0-126">ほとんどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ユーザーは、ランタイムと直接やり取りすることはありません。代わりに、構成ファイル内のクラスや動作で、コア プログラミング モデルの構成要素 (エンドポイント、コントラクト、バインディング、アドレス、動作属性など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-126">Most [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] users do not interact with the runtime directly; instead they use core programming model constructs like endpoints, contracts, bindings, addresses, and behavior attributes on classes or behaviors in configuration files.</span></span> <span data-ttu-id="372b0-127">これらの構成要素の構成、*説明ツリー*サービスをサポートするためにランタイムを構築するための完全な仕様はまたはクライアントが、説明ツリーによって記述します。</span><span class="sxs-lookup"><span data-stu-id="372b0-127">These constructs make up the *description tree*, which is the complete specification for constructing a runtime to support a service or client described by the description tree.</span></span>  
  
 <span data-ttu-id="372b0-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、次の 4 種類の動作があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-128">There are four kinds of behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="372b0-129">サービスの動作 (<xref:System.ServiceModel.Description.IServiceBehavior> 型) : <xref:System.ServiceModel.ServiceHostBase> を含むサービス ランタイム全体のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="372b0-129">Service behaviors (<xref:System.ServiceModel.Description.IServiceBehavior> types) enable the customization of the entire service runtime including <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
-   <span data-ttu-id="372b0-130">エンドポイントの動作 (<xref:System.ServiceModel.Description.IEndpointBehavior> 型) : サービス エンドポイントと、関連する <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> オブジェクトのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="372b0-130">Endpoint behaviors (<xref:System.ServiceModel.Description.IEndpointBehavior> types) enable the customization of service endpoints and their associated <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objects.</span></span>  
  
-   <span data-ttu-id="372b0-131">コントラクトの動作 (<xref:System.ServiceModel.Description.IContractBehavior> 型) : <xref:System.ServiceModel.Dispatcher.ClientRuntime> クラス (クライアント アプリケーションの場合) と、<xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラス (サービス アプリケーションの場合) のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="372b0-131">Contract behaviors (<xref:System.ServiceModel.Description.IContractBehavior> types) enable the customization of both the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes in client and service applications, respectively.</span></span>  
  
-   <span data-ttu-id="372b0-132">操作の動作 (<xref:System.ServiceModel.Description.IOperationBehavior> 型) : <xref:System.ServiceModel.Dispatcher.ClientOperation> クラス (クライアントの場合) と、<xref:System.ServiceModel.Dispatcher.DispatchOperation> クラス (サービスの場合) のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="372b0-132">Operation behaviors (<xref:System.ServiceModel.Description.IOperationBehavior> types) enable the customization of the <xref:System.ServiceModel.Dispatcher.ClientOperation> and <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes, again, on the client and service.</span></span>  
  
 <span data-ttu-id="372b0-133">カスタム属性を実装するか、アプリケーション構成ファイルを使用することにより、これらの動作をさまざまな説明オブジェクトに追加できます。また、適切な説明オブジェクトの動作コレクションに直接追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-133">You can add these behaviors to the various description objects by implementing custom attributes, using application configuration files, or directly by adding them to the behaviors collection on the appropriate description object.</span></span> <span data-ttu-id="372b0-134">ただし、<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.ChannelFactory%601> を呼び出す前に、サービス説明オブジェクトまたはサービス エンドポイント説明オブジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-134">The must, however, be added to a service description or service endpoint description object prior to calling <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>.</span></span>  
  
### <a name="behavior-scopes"></a><span data-ttu-id="372b0-135">動作のスコープ</span><span class="sxs-lookup"><span data-stu-id="372b0-135">Behavior Scopes</span></span>  
 <span data-ttu-id="372b0-136">4 種類の動作があり、それぞれランタイム アクセスの特定のスコープに対応しています。</span><span class="sxs-lookup"><span data-stu-id="372b0-136">There are four behavior types, each of which corresponds to a particular scope of runtime access.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="372b0-137">サービスの動作</span><span class="sxs-lookup"><span data-stu-id="372b0-137">Service Behaviors</span></span>  
 <span data-ttu-id="372b0-138"><xref:System.ServiceModel.Description.IServiceBehavior> を実装するサービスの動作は、サービス ランタイム全体を変更する主要機構です。</span><span class="sxs-lookup"><span data-stu-id="372b0-138">Service behaviors, which implement <xref:System.ServiceModel.Description.IServiceBehavior>, are the primary mechanism by which you modify the entire service runtime.</span></span> <span data-ttu-id="372b0-139">サービスの動作をサービスに追加する場合、3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-139">There are three mechanisms for adding service behaviors to a service.</span></span>  
  
1.  <span data-ttu-id="372b0-140">サービス クラスの属性を使用する方法。</span><span class="sxs-lookup"><span data-stu-id="372b0-140">Using an attribute on the service class.</span></span>  <span data-ttu-id="372b0-141"><xref:System.ServiceModel.ServiceHost> を構築すると、<xref:System.ServiceModel.ServiceHost> 実装は、リフレクションを使用してそのサービス型の属性セットを検出します。</span><span class="sxs-lookup"><span data-stu-id="372b0-141">When a <xref:System.ServiceModel.ServiceHost> is constructed, the <xref:System.ServiceModel.ServiceHost> implementation uses reflection to discover the set of attributes on the type of the service.</span></span> <span data-ttu-id="372b0-142">これらの属性のいずれかが <xref:System.ServiceModel.Description.IServiceBehavior> の実装である場合、<xref:System.ServiceModel.Description.ServiceDescription> の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-142">If any of those attributes are implementations of <xref:System.ServiceModel.Description.IServiceBehavior>, they are added to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="372b0-143">これにより、これらの動作はサービス ランタイムの構築に参加できます。</span><span class="sxs-lookup"><span data-stu-id="372b0-143">This allows those behaviors to participate in the construction of the service run time.</span></span>  
  
2.  <span data-ttu-id="372b0-144">プログラムによって、<xref:System.ServiceModel.Description.ServiceDescription> の動作コレクションに動作を追加する方法。</span><span class="sxs-lookup"><span data-stu-id="372b0-144">Programmatically adding the behavior to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="372b0-145">これを行うには、次のコード行を使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-145">This can be accomplished with the following lines of code:</span></span>  
  
    ```  
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3.  <span data-ttu-id="372b0-146">構成を拡張するカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法。</span><span class="sxs-lookup"><span data-stu-id="372b0-146">Implementing a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span> <span data-ttu-id="372b0-147">これにより、アプリケーション構成ファイルからサービスの動作を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="372b0-147">This enables the use of the service behavior from application configuration files.</span></span>  
  
 <span data-ttu-id="372b0-148">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサービスの動作の例として、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作などがあります。</span><span class="sxs-lookup"><span data-stu-id="372b0-148">Examples of service behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] include the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute, the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>, and the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="372b0-149">コントラクトの動作</span><span class="sxs-lookup"><span data-stu-id="372b0-149">Contract Behaviors</span></span>  
 <span data-ttu-id="372b0-150"><xref:System.ServiceModel.Description.IContractBehavior> インターフェイスを実装するコントラクトの動作は、コントラクト全体にわたり、クライアント ランタイムとサービス ランタイムを拡張する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-150">Contract behaviors, which implement the <xref:System.ServiceModel.Description.IContractBehavior> interface, are used to extend both the client and service runtime across a contract.</span></span>  
  
 <span data-ttu-id="372b0-151">コントラクトの動作をコントラクトに追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-151">There are two mechanisms for adding contract behaviors to a contract.</span></span>  <span data-ttu-id="372b0-152">1 つは、コントラクト インターフェイスで使用するカスタム属性を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="372b0-152">The first mechanism is to create a custom attribute to be used on the contract interface.</span></span> <span data-ttu-id="372b0-153">コントラクト インターフェイスを <xref:System.ServiceModel.ServiceHost> または <xref:System.ServiceModel.ChannelFactory%601> に渡すと、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はインターフェイスの属性を検査します。</span><span class="sxs-lookup"><span data-stu-id="372b0-153">When a contract interface is passed to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] examines the attributes on the interface.</span></span> <span data-ttu-id="372b0-154">属性のいずれかが <xref:System.ServiceModel.Description.IContractBehavior> の実装である場合、そのインターフェイス用に作成された <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-154">If any attributes are implementations of <xref:System.ServiceModel.Description.IContractBehavior>, those are added to the behaviors collection on the <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> created for that interface.</span></span>  
  
 <span data-ttu-id="372b0-155">カスタム コントラクトの動作属性に <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-155">You can also implement the <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> on the custom contract behavior attribute.</span></span> <span data-ttu-id="372b0-156">この場合、適用先に応じて動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="372b0-156">In this case, the behavior is as follows when applied to:</span></span>  
  
 <span data-ttu-id="372b0-157">•コントラクト インターフェイスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="372b0-157">•A contract interface.</span></span> <span data-ttu-id="372b0-158">この場合、動作は任意のエンドポイント内の該当の型のすべてのコントラクトに適用されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> プロパティの値を無視します。</span><span class="sxs-lookup"><span data-stu-id="372b0-158">In this case, the behavior is applied to all contracts of that type in any endpoint and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="372b0-159">•サービス クラスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="372b0-159">•A service class.</span></span> <span data-ttu-id="372b0-160">この場合、動作はコントラクトが <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> プロパティの値であるエンドポイントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-160">In this case, the behavior is applied only to endpoints the contract of which is the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="372b0-161">•コールバック クラスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="372b0-161">•A callback class.</span></span> <span data-ttu-id="372b0-162">この場合、動作は双方向クライアントのエンドポイントに適用されます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> プロパティの値を無視します。</span><span class="sxs-lookup"><span data-stu-id="372b0-162">In this case, the behavior is applied to the duplex client's endpoint and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="372b0-163">2 番目の方法として、<xref:System.ServiceModel.Description.ContractDescription> の動作コレクションに動作を追加する方法があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-163">The second mechanism is to add the behavior to the behaviors collection on a <xref:System.ServiceModel.Description.ContractDescription>.</span></span>  
  
 <span data-ttu-id="372b0-164">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のコントラクトの動作の例として、<xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> 属性などがあります。</span><span class="sxs-lookup"><span data-stu-id="372b0-164">Examples of contract behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] include the <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="372b0-165">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="372b0-165">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="endpoint-behaviors"></a><span data-ttu-id="372b0-166">エンドポイントの動作</span><span class="sxs-lookup"><span data-stu-id="372b0-166">Endpoint Behaviors</span></span>  
 <span data-ttu-id="372b0-167"><xref:System.ServiceModel.Description.IEndpointBehavior> を実装するエンドポイントの動作は、特定のエンドポイントのサービス ランタイムまたはクライアント ランタイム全体を変更する主要機構です。</span><span class="sxs-lookup"><span data-stu-id="372b0-167">Endpoint behaviors, which implement <xref:System.ServiceModel.Description.IEndpointBehavior>, are the primary mechanism by which you modify the entire service or client run time for a specific endpoint.</span></span>  
  
 <span data-ttu-id="372b0-168">エンドポイントの動作をサービスに追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-168">There are two mechanisms for adding endpoint behaviors to a service.</span></span>  
  
1.  <span data-ttu-id="372b0-169"><xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティに動作を追加する方法。</span><span class="sxs-lookup"><span data-stu-id="372b0-169">Add the behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property.</span></span>  
  
2.  <span data-ttu-id="372b0-170">構成を拡張するカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法。</span><span class="sxs-lookup"><span data-stu-id="372b0-170">Implement a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span>  
  
 <span data-ttu-id="372b0-171">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="372b0-171">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="372b0-172">操作の動作</span><span class="sxs-lookup"><span data-stu-id="372b0-172">Operation Behaviors</span></span>  
 <span data-ttu-id="372b0-173"><xref:System.ServiceModel.Description.IOperationBehavior> インターフェイスを実装する操作の動作は、各操作のクライアント ランタイムとサービス ランタイムを拡張する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-173">Operation behaviors, which implement the <xref:System.ServiceModel.Description.IOperationBehavior> interface, are used to extend both the client and service runtime for each operation.</span></span>  
  
 <span data-ttu-id="372b0-174">操作の動作を操作に追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-174">There are two mechanisms for adding operation behaviors to an operation.</span></span> <span data-ttu-id="372b0-175">1 つは、操作をモデル化するメソッドで使用するカスタム属性を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="372b0-175">The first mechanism is to create a custom attribute to be used on the method that models the operation.</span></span> <span data-ttu-id="372b0-176"><xref:System.ServiceModel.ServiceHost> または <xref:System.ServiceModel.ChannelFactory> に操作を追加すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、その操作用に作成された <xref:System.ServiceModel.Description.IOperationBehavior> の動作コレクションに任意の <xref:System.ServiceModel.Description.OperationDescription> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="372b0-176">When an operation is added to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adds any  <xref:System.ServiceModel.Description.IOperationBehavior> attributes to the behaviors collection on the <xref:System.ServiceModel.Description.OperationDescription> created for that operation.</span></span>  
  
 <span data-ttu-id="372b0-177">2 番目の機構は、構成された <xref:System.ServiceModel.Description.OperationDescription> の動作コレクションに動作を直接追加します。</span><span class="sxs-lookup"><span data-stu-id="372b0-177">The second mechanism is by directly adding the behavior to the behaviors collection on a constructed <xref:System.ServiceModel.Description.OperationDescription>.</span></span>  
  
 <span data-ttu-id="372b0-178">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の操作の動作の例として、<xref:System.ServiceModel.OperationBehaviorAttribute> や <xref:System.ServiceModel.TransactionFlowAttribute> などがあります。</span><span class="sxs-lookup"><span data-stu-id="372b0-178">Examples of operation behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] include the <xref:System.ServiceModel.OperationBehaviorAttribute> and the <xref:System.ServiceModel.TransactionFlowAttribute>.</span></span>  
  
 <span data-ttu-id="372b0-179">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="372b0-179">For more information and an example, see the reference topic.</span></span>  
  
### <a name="using-configuration-to-create-behaviors"></a><span data-ttu-id="372b0-180">構成を使用した動作の作成</span><span class="sxs-lookup"><span data-stu-id="372b0-180">Using Configuration to Create Behaviors</span></span>  
 <span data-ttu-id="372b0-181">サービス、エンドポイント、およびコントラクトの動作は、コードまたは属性を使用して指定するように設計できます。アプリケーション構成ファイルまたは Web 構成ファイルを使用して構成できるのは、サービスの動作とエンドポイントの動作だけです。</span><span class="sxs-lookup"><span data-stu-id="372b0-181">Service and endpoint, and contract behaviors can by designed to be specified in code or using attributes; only service and endpoint behaviors can be configured using application or Web configuration files.</span></span> <span data-ttu-id="372b0-182">属性を使用して動作を公開した場合、開発者は、実行時に追加、削除、または変更できない動作をコンパイル時に指定できます。</span><span class="sxs-lookup"><span data-stu-id="372b0-182">Exposing behaviors using attributes allows developers to specify a behavior at compilation-time that cannot be added, removed, or modified at runtime.</span></span> <span data-ttu-id="372b0-183">多くの場合、これはサービスの適切な操作のために常に必要となる動作に適しています (<xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> 属性に対するトランザクション関連のパラメーターなど)。</span><span class="sxs-lookup"><span data-stu-id="372b0-183">This is often suitable for behaviors that are always required for the correct operation of a service (for example, the transaction-related parameters to the <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> attribute).</span></span> <span data-ttu-id="372b0-184">構成を使用して動作を公開すると、開発者はサービス展開者に動作の仕様と構成を委ねることができます。</span><span class="sxs-lookup"><span data-stu-id="372b0-184">Exposing behaviors using configuration allows developers to leave the specification and configuration of those behaviors to those who deploy the service.</span></span> <span data-ttu-id="372b0-185">これは、動作がオプション コンポーネント、または他の展開固有の構成 (サービスまたはサービスの特定の承認構成についてメタデータを公開するかどうかなど) である場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="372b0-185">This is suitable for behaviors that are optional components or other deployment-specific configuration, such as whether metadata is exposed for the service or the particular authorization configuration for a service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="372b0-186">企業のアプリケーション ポリシーを machine.config 構成ファイルに挿入し、これらの項目をロックダウンすることで、ポリシーを適用する構成をサポートする動作を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="372b0-186">You can also use behaviors that support configuration to enforce company application policies by inserting them into the machine.config configuration file and locking those items down.</span></span> <span data-ttu-id="372b0-187">説明および例に、次を参照してください。[する方法: 企業内のロックのダウン エンドポイント](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)です。</span><span class="sxs-lookup"><span data-stu-id="372b0-187">For a description and an example, see [How to: Lock Down Endpoints in the Enterprise](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
 <span data-ttu-id="372b0-188">構成を使用して動作を公開するには、開発者は <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> の派生クラスを作成し、その拡張を構成に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-188">To expose a behavior using configuration, a developer must create a derived class of <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> and then register that extension with configuration.</span></span>  
  
 <span data-ttu-id="372b0-189"><xref:System.ServiceModel.Description.IEndpointBehavior> で <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="372b0-189">The following code example shows how an  <xref:System.ServiceModel.Description.IEndpointBehavior> implements <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:</span></span>  
  
```  
// BehaviorExtensionElement members  
    public override Type BehaviorType  
    {  
      get { return typeof(EndpointBehaviorMessageInspector); }  
    }  
  
    protected override object CreateBehavior()  
    {  
      return new EndpointBehaviorMessageInspector();  
    }  
```  
  
 <span data-ttu-id="372b0-190">構成システムでカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を読み込むには、拡張として登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-190">In order for the configuration system to load a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, it must be registered as an extension.</span></span> <span data-ttu-id="372b0-191">上記のエンドポイントの動作の構成ファイルを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="372b0-191">The following code example shows the configuration file for the preceding endpoint behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"   
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add   
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="372b0-192">ここで`Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector`動作拡張型と`HostApplication`そのクラスがコンパイルされているアセンブリの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="372b0-192">Where `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` is the behavior extension type and `HostApplication` is the name of the assembly into which that class has been compiled.</span></span>  
  
### <a name="evaluation-order"></a><span data-ttu-id="372b0-193">評価順序</span><span class="sxs-lookup"><span data-stu-id="372b0-193">Evaluation Order</span></span>  
 <span data-ttu-id="372b0-194"><xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> と <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> は、プログラミング モデルと記述からランタイムを構築します。</span><span class="sxs-lookup"><span data-stu-id="372b0-194">The <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> and the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> are responsible for building the runtime from the programming model and description.</span></span> <span data-ttu-id="372b0-195">前述のように、動作は、サービス、エンドポイント、コントラクト、および操作でランタイムの構築プロセスを支援します。</span><span class="sxs-lookup"><span data-stu-id="372b0-195">Behaviors, as previously described, contribute to that build process at the service, endpoint, contract, and operation.</span></span>  
  
 <span data-ttu-id="372b0-196"><xref:System.ServiceModel.ServiceHost> は次の順序で動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-196">The <xref:System.ServiceModel.ServiceHost> applies behaviors in the following order:</span></span>  
  
1.  <span data-ttu-id="372b0-197">サービス</span><span class="sxs-lookup"><span data-stu-id="372b0-197">Service</span></span>  
  
2.  <span data-ttu-id="372b0-198">コントラクト</span><span class="sxs-lookup"><span data-stu-id="372b0-198">Contract</span></span>  
  
3.  <span data-ttu-id="372b0-199">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="372b0-199">Endpoint</span></span>  
  
4.  <span data-ttu-id="372b0-200">操作</span><span class="sxs-lookup"><span data-stu-id="372b0-200">Operation</span></span>  
  
 <span data-ttu-id="372b0-201">動作のどのコレクション内でも、順序が保証されるというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="372b0-201">Within any collection of behaviors, no order is guaranteed.</span></span>  
  
 <span data-ttu-id="372b0-202"><xref:System.ServiceModel.ChannelFactory%601> は次の順序で動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="372b0-202">The <xref:System.ServiceModel.ChannelFactory%601> applies behaviors in the following order:</span></span>  
  
1.  <span data-ttu-id="372b0-203">コントラクト</span><span class="sxs-lookup"><span data-stu-id="372b0-203">Contract</span></span>  
  
2.  <span data-ttu-id="372b0-204">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="372b0-204">Endpoint</span></span>  
  
3.  <span data-ttu-id="372b0-205">操作</span><span class="sxs-lookup"><span data-stu-id="372b0-205">Operation</span></span>  
  
 <span data-ttu-id="372b0-206">この場合も、動作のどのコレクション内でも、順序が保証されるというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="372b0-206">Within any collection of behaviors, again, no order is guaranteed.</span></span>  
  
### <a name="adding-behaviors-programmatically"></a><span data-ttu-id="372b0-207">プログラムによる動作の追加</span><span class="sxs-lookup"><span data-stu-id="372b0-207">Adding Behaviors Programmatically</span></span>  
 <span data-ttu-id="372b0-208"><xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> メソッドの後で、サービス アプリケーションの <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> の各プロパティを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="372b0-208">Properties of the <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> method on <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="372b0-209">このメソッドの後で変更すると、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> および `AddServiceEndpoint` の <xref:System.ServiceModel.ServiceHostBase> プロパティや <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドなどの一部のメンバーは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="372b0-209">Some members, like the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, throw an exception if modified past that point.</span></span> <span data-ttu-id="372b0-210">変更を許可するメンバーもありますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="372b0-210">Others permit you to modify them, but the result is undefined.</span></span>  
  
 <span data-ttu-id="372b0-211">同様に、クライアントで、<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 呼び出しの後で、<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="372b0-211">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>.</span></span> <span data-ttu-id="372b0-212">この呼び出しの後で変更すると、<xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> プロパティは例外をスローします。その他のクライアント記述値は、エラーを発生させずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="372b0-212">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> property throws an exception if modified past that point, but the other client description values can be modified without error.</span></span> <span data-ttu-id="372b0-213">ただし、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="372b0-213">The result, however, is undefined.</span></span>  
  
 <span data-ttu-id="372b0-214">サービスとクライアントのどちらの場合も、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> の呼び出しの前に記述を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="372b0-214">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="inheritance-rules-for-behavior-attributes"></a><span data-ttu-id="372b0-215">動作属性の継承ルール</span><span class="sxs-lookup"><span data-stu-id="372b0-215">Inheritance Rules for Behavior Attributes</span></span>  
 <span data-ttu-id="372b0-216">4 種類の動作はすべて、属性 (サービスの動作とコントラクトの動作) を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="372b0-216">All four types of behaviors can be populated using attributes – service behaviors and contract behaviors.</span></span> <span data-ttu-id="372b0-217">属性はマネージ オブジェクトとメンバーで定義され、マネージ オブジェクトとメンバーは継承をサポートしているため、継承のコンテキストでの動作属性の機能を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="372b0-217">Because attributes are defined on managed objects and members, and managed objects and members support inheritance, it is necessary to define how behavior attributes work in the context of inheritance.</span></span>  
  
 <span data-ttu-id="372b0-218">大まかに言えば、特定のスコープ (サービス、コントラクト、操作など) については、そのスコープの継承階層内のすべての動作属性が適用されるという継承ルールになります。</span><span class="sxs-lookup"><span data-stu-id="372b0-218">At a high level, the rule is that for a particular scope (for example, service, contract, or operation), all behavior attributes in the inheritance hierarchy for that scope are applied.</span></span> <span data-ttu-id="372b0-219">同じ種類の 2 つの動作属性がある場合、最も多く派生された種類だけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-219">If there are two behavior attributes of the same type, only the most-derived type is used.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="372b0-220">サービスの動作</span><span class="sxs-lookup"><span data-stu-id="372b0-220">Service Behaviors</span></span>  
 <span data-ttu-id="372b0-221">サービス クラスの場合、指定のクラスとその親のすべてのサービス動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-221">For a given service class, all service behavior attributes on that class, and on parents of that class, are applied.</span></span> <span data-ttu-id="372b0-222">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-222">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 <span data-ttu-id="372b0-223">たとえば、上記の例では、最終的にサービス B は、<xref:System.ServiceModel.InstanceContextMode> が <xref:System.ServiceModel.InstanceContextMode.Single>、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> が <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>、<xref:System.ServiceModel.ConcurrencyMode> が <xref:System.ServiceModel.ConcurrencyMode.Single> になります。</span><span class="sxs-lookup"><span data-stu-id="372b0-223">For example, in the preceding case, the service B ends up with an <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.Single>, an <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> mode of <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, and a <xref:System.ServiceModel.ConcurrencyMode> of <xref:System.ServiceModel.ConcurrencyMode.Single>.</span></span> <span data-ttu-id="372b0-224"><xref:System.ServiceModel.ConcurrencyMode> が <xref:System.ServiceModel.ConcurrencyMode.Single> になるのは、サービス B の <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性の方がサービス A よりも多く派生されているためです。</span><span class="sxs-lookup"><span data-stu-id="372b0-224">The <xref:System.ServiceModel.ConcurrencyMode> is <xref:System.ServiceModel.ConcurrencyMode.Single>, because <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute on service B is on "more derived" than that on service A.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="372b0-225">コントラクトの動作</span><span class="sxs-lookup"><span data-stu-id="372b0-225">Contract Behaviors</span></span>  
 <span data-ttu-id="372b0-226">コントラクトの場合、指定のインターフェイスとその親のすべてのコントラクト動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-226">For a given contract, all contract behavior attributes on that interface and on parents of that interface, are applied.</span></span> <span data-ttu-id="372b0-227">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-227">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="372b0-228">操作の動作</span><span class="sxs-lookup"><span data-stu-id="372b0-228">Operation Behaviors</span></span>  
 <span data-ttu-id="372b0-229">指定の操作が既存の抽象操作または仮想操作をオーバーライドしない場合、継承ルールは適用されません。</span><span class="sxs-lookup"><span data-stu-id="372b0-229">If a given operation does not override an existing abstract or virtual operation, no inheritance rules apply.</span></span>  
  
 <span data-ttu-id="372b0-230">操作が既存の操作をオーバーライドする場合は、その操作とその親のすべての操作動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-230">If an operation does override an existing operation, then all operation behavior attributes on that operation and on parents of that operation, are applied.</span></span>  <span data-ttu-id="372b0-231">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="372b0-231">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>
