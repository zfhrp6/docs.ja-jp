---
title: "エンドポイント : アドレス、バインディング、およびコントラクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ee80307e0db82f4744970844754a910e81ca3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a><span data-ttu-id="b8ef7-102">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="b8ef7-102">Endpoints: Addresses, Bindings, and Contracts</span></span>
<span data-ttu-id="b8ef7-103">すべての通信、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]サービスが使用して行われる、*エンドポイント*サービス。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-103">All communication with a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="b8ef7-104">エンドポイントは、クライアントが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-104">Endpoints provide clients access to the functionality offered by a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="b8ef7-105">各エンドポイントは、次の 4 つのプロパティで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-105">Each endpoint consists of four properties:</span></span>  
  
-   <span data-ttu-id="b8ef7-106">そのエンドポイントの場所を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-106">An address that indicates where the endpoint can be found.</span></span>  
  
-   <span data-ttu-id="b8ef7-107">クライアントがエンドポイントと通信する方法を指定するバインディング。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-107">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="b8ef7-108">利用可能な操作を識別するためのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-108">A contract that identifies the operations available.</span></span>  
  
-   <span data-ttu-id="b8ef7-109">エンドポイントのローカル実装の詳細を指定する一連の動作。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-109">A set of behaviors that specify local implementation details of the endpoint.</span></span>  
  
 <span data-ttu-id="b8ef7-110">ここでは、エンドポイントの構造と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでの表現方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-110">This topic discusses this endpoint structure and explains how it is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model.</span></span>  
  
## <a name="the-structure-of-an-endpoint"></a><span data-ttu-id="b8ef7-111">エンドポイントの構造</span><span class="sxs-lookup"><span data-stu-id="b8ef7-111">The Structure of an Endpoint</span></span>  
 <span data-ttu-id="b8ef7-112">各エンドポイントの構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-112">Each endpoint consists of the following:</span></span>  
  
-   <span data-ttu-id="b8ef7-113">アドレス : アドレスは、エンドポイントを一意に識別し、サービスの潜在的ユーザーにそのエンドポイントの場所を示します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-113">Address: The address uniquely identifies the endpoint and tells potential consumers of the service where it is located.</span></span> <span data-ttu-id="b8ef7-114">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでは、<xref:System.ServiceModel.EndpointAddress> クラスで表されます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-114">It is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="b8ef7-115"><xref:System.ServiceModel.EndpointAddress> クラスには次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-115">An <xref:System.ServiceModel.EndpointAddress> class contains:</span></span>  
  
    -   <span data-ttu-id="b8ef7-116"><xref:System.ServiceModel.EndpointAddress.Uri%2A> プロパティは、サービスのアドレスを表します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-116">A <xref:System.ServiceModel.EndpointAddress.Uri%2A> property, which represents the address of the service.</span></span>  
  
    -   <span data-ttu-id="b8ef7-117"><xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティは、サービスのセキュリティ ID とオプションのメッセージ ヘッダーのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-117">An <xref:System.ServiceModel.EndpointAddress.Identity%2A> property, which represents the security identity of the service and a collection of optional message headers.</span></span> <span data-ttu-id="b8ef7-118">オプションのメッセージ ヘッダーは、エンドポイントの識別またはエンドポイントとの対話のための、より詳細なアドレス指定情報を追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-118">The optional message headers are used to provide additional and more detailed addressing information to identify or interact with the endpoint.</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8ef7-119">[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-119"> [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
-   <span data-ttu-id="b8ef7-120">バインディング : バインディングは、エンドポイントとの通信方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-120">Binding: The binding specifies how to communicate with the endpoint.</span></span> <span data-ttu-id="b8ef7-121">バインディングには、以下の項目が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-121">This includes:</span></span>  
  
    -   <span data-ttu-id="b8ef7-122">使用するトランスポート プロトコル (例 : TCP や HTTP)。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-122">The transport protocol to use (for example, TCP or HTTP).</span></span>  
  
    -   <span data-ttu-id="b8ef7-123">メッセージに使用するエンコーディング (例 : テキストやバイナリ)。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-123">The encoding to use for the messages (for example, text or binary).</span></span>  
  
    -   <span data-ttu-id="b8ef7-124">必要なセキュリティ要件 (例 : SSL メッセージ セキュリティや SOAP メッセージ セキュリティ)。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-124">The necessary security requirements (for example, SSL or SOAP message security).</span></span>  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8ef7-125">[WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-125"> [WCF Bindings Overview](../../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="b8ef7-126">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでは、バインディングは抽象基本クラス <xref:System.ServiceModel.Channels.Binding> で表されます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-126">A binding is represented in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] object model by the abstract base class <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b8ef7-127">ほとんどのシナリオでは、システム指定のバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-127">For most scenarios, users can use one of the system-provided bindings.</span></span> <span data-ttu-id="b8ef7-128">詳細については、次を参照してください。[システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-128">For more information, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
-   <span data-ttu-id="b8ef7-129">コントラクト : コントラクトは、エンドポイントがクライアントに公開する機能を示します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-129">Contracts: The contract outlines what functionality the endpoint exposes to the client.</span></span> <span data-ttu-id="b8ef7-130">コントラクトは、以下の項目を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-130">A contract specifies:</span></span>  
  
    -   <span data-ttu-id="b8ef7-131">クライアントから呼び出すことができる操作。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-131">What operations can be called by a client.</span></span>  
  
    -   <span data-ttu-id="b8ef7-132">メッセージの形式。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-132">The form of the message.</span></span>  
  
    -   <span data-ttu-id="b8ef7-133">操作を呼び出すために必要な入力パラメーターまたはデータの型。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-133">The type of input parameters or data required to call the operation.</span></span>  
  
    -   <span data-ttu-id="b8ef7-134">クライアントが予期できる処理メッセージまたは応答メッセージの種類。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-134">What type of processing or response message the client can expect.</span></span>  
  
     <span data-ttu-id="b8ef7-135">詳細については、コントラクトを定義する、次を参照してください。[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-135">For more information about defining a contract, see [Designing Service Contracts](../../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
-   <span data-ttu-id="b8ef7-136">動作 : エンドポイントの動作を使用すると、サービス エンドポイントのローカル動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-136">Behaviors: You can use endpoint behaviors to customize the local behavior of the service endpoint.</span></span> <span data-ttu-id="b8ef7-137">エンドポイントの動作では、これを実現ビルド プロセスに参加を[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ランタイム。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-137">Endpoint behaviors achieve this by participating in the process of building a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]runtime.</span></span> <span data-ttu-id="b8ef7-138">エンドポイントの動作の一例は、<xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> プロパティです。このプロパティにより、SOAP アドレスまたは Web サービス記述言語 (WSDL) アドレスとは異なるリッスン アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-138">An example of an endpoint behavior is the <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> property, which allows you to specify a different listening address than the SOAP or Web Services Description Language (WSDL) address.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8ef7-139">[ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-139"> [ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).</span></span>  
  
## <a name="defining-endpoints"></a><span data-ttu-id="b8ef7-140">エンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="b8ef7-140">Defining Endpoints</span></span>  
 <span data-ttu-id="b8ef7-141">サービスのエンドポイントは、コードを使用して強制的に指定するか、構成を介して宣言として指定することができます。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-141">You can specify the endpoint for a service either imperatively using code or declaratively through configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b8ef7-142">[する方法: 構成でサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)と[する方法: コードでサービス エンドポイントの作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-142"> [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) and [How to: Create a Service Endpoint in Code](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8ef7-143">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b8ef7-143">In This Section</span></span>  
 <span data-ttu-id="b8ef7-144">このセクションでは、バインディング、エンドポイント、およびアドレスの目的を説明し、バインディングとエンドポイントの構成方法および `ClientVia` 動作と `ListenUri` プロパティの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-144">This section explains the purpose of bindings, endpoints, and addresses; shows how to configure a binding and an endpoint; and demonstrates how to use the `ClientVia` behavior and `ListenUri` property.</span></span>  
  
 [<span data-ttu-id="b8ef7-145">アドレス</span><span class="sxs-lookup"><span data-stu-id="b8ef7-145">Addresses</span></span>](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 <span data-ttu-id="b8ef7-146">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でのエンドポイントのアドレス指定の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-146">Describes how endpoints are addressed in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="b8ef7-147">バインディング</span><span class="sxs-lookup"><span data-stu-id="b8ef7-147">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 <span data-ttu-id="b8ef7-148">バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-148">Describes how bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span>  
  
 [<span data-ttu-id="b8ef7-149">コントラクト</span><span class="sxs-lookup"><span data-stu-id="b8ef7-149">Contracts</span></span>](../../../../docs/framework/wcf/feature-details/contracts.md)  
 <span data-ttu-id="b8ef7-150">コントラクトでサービスのメソッドが定義されるしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-150">Describes how contracts define the methods of a service.</span></span>  
  
 [<span data-ttu-id="b8ef7-151">方法: 構成でサービス エンドポイントの作成</span><span class="sxs-lookup"><span data-stu-id="b8ef7-151">How to: Create a Service Endpoint in Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="b8ef7-152">構成にサービス エンドポイントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-152">Describes how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="b8ef7-153">方法: コードでサービス エンドポイントの作成</span><span class="sxs-lookup"><span data-stu-id="b8ef7-153">How to: Create a Service Endpoint in Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="b8ef7-154">コード内にサービス エンドポイントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-154">Describes how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="b8ef7-155">方法: Svcutil.exe を使用してコンパイル済みサービス コードを検証するには</span><span class="sxs-lookup"><span data-stu-id="b8ef7-155">How to: Use Svcutil.exe to Validate Compiled Service Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 <span data-ttu-id="b8ef7-156">使用してサービスをホストせず、サービスの実装と構成のエラーを検出する方法について説明、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8ef7-156">Describes how to detect errors in service implementations and configurations without hosting the service using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ef7-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8ef7-157">See Also</span></span>  
 [<span data-ttu-id="b8ef7-158">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="b8ef7-158">Configuring Services</span></span>](../../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="b8ef7-159">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="b8ef7-159">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
