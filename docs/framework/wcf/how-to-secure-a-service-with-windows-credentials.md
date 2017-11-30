---
title: "方法 : Windows 資格情報でサービスをセキュリティで保護する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
caps.latest.revision: "26"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 09e15fcb1f18a91961ee77a57dd8eed80f3faf6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="21cb8-102">方法 : Windows 資格情報でサービスをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="21cb8-102">How to: Secure a Service with Windows Credentials</span></span>
<span data-ttu-id="21cb8-103">このトピックでトランスポート セキュリティを有効にする方法について説明、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]サービスを Windows ドメインに存在し、同じドメイン内のクライアントによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-103">This topic shows how to enable transport security on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service that resides in a Windows domain and is called by clients in the same domain.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="21cb8-104">このシナリオを参照してください[トランスポート セキュリティと Windows 認証](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-104"> this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="21cb8-105">サンプル アプリケーションについては、次を参照してください。、 [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="21cb8-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>  
  
 <span data-ttu-id="21cb8-106">このトピックでは、定義済みのコントラクト インターフェイスと実装が既に存在するものとして、それに機能を追加していきます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="21cb8-107">既存のサービスとクライアントを変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-107">You can also modify an existing service and client.</span></span>  
  
 <span data-ttu-id="21cb8-108">Windows 資格情報によるサービスのセキュリティ保護は、完全にコードで実現できます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="21cb8-109">または、構成ファイルを使用して、一部のコードを省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="21cb8-110">このトピックでは両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-110">This topic shows both ways.</span></span> <span data-ttu-id="21cb8-111">ただし、どちらか 1 つの方法だけを使うようにして、両方は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="21cb8-111">Be sure you only use one of the ways, not both.</span></span>  
  
 <span data-ttu-id="21cb8-112">最初の 3 つの手順は、コードを使用してサービスをセキュリティで保護する方法について示しています。</span><span class="sxs-lookup"><span data-stu-id="21cb8-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="21cb8-113">4 番目と 5 番目の手順は、構成ファイルを使用して同様の操作を行う方法について示しています。</span><span class="sxs-lookup"><span data-stu-id="21cb8-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>  
  
## <a name="using-code"></a><span data-ttu-id="21cb8-114">コードの使用</span><span class="sxs-lookup"><span data-stu-id="21cb8-114">Using Code</span></span>  
 <span data-ttu-id="21cb8-115">サービスとクライアントの完全なコードは、このトピックの最後にある「使用例」のセクションに記載されています。</span><span class="sxs-lookup"><span data-stu-id="21cb8-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>  
  
 <span data-ttu-id="21cb8-116">最初の手順では、コードで <xref:System.ServiceModel.WSHttpBinding> クラスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="21cb8-117">バインディングでは HTTP トランスポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="21cb8-118">同じバインディングがクライアント上で使用されます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-118">The same binding is used on the client.</span></span>  
  
#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="21cb8-119">Windows 資格情報とメッセージ セキュリティを使用する WSHttpBinding を作成するには</span><span class="sxs-lookup"><span data-stu-id="21cb8-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>  
  
1.  <span data-ttu-id="21cb8-120">この手順のコードは、「使用例」のセクションに記載されたサービス コードの `Run` クラスの `Test` メソッドの先頭に挿入されています。</span><span class="sxs-lookup"><span data-stu-id="21cb8-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>  
  
2.  <span data-ttu-id="21cb8-121"><xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
3.  <span data-ttu-id="21cb8-122"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A> クラスの <xref:System.ServiceModel.WSHttpSecurity> プロパティを <xref:System.ServiceModel.SecurityMode.Message> に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>  
  
4.  <span data-ttu-id="21cb8-123"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> クラスの <xref:System.ServiceModel.MessageSecurityOverHttp> プロパティを <xref:System.ServiceModel.MessageCredentialType.Windows> に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>  
  
5.  <span data-ttu-id="21cb8-124">この手順で使用するコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="21cb8-124">The code for this procedure is as follows:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
     [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]  
  
### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="21cb8-125">サービスでのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="21cb8-125">Using the Binding in a Service</span></span>  
 <span data-ttu-id="21cb8-126">この 2 番目の手順では、自己ホスト型サービスでバインディングを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="21cb8-127">ホスティング サービスを参照してください[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-127"> hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="21cb8-128">サービスでバインディングを使用するには</span><span class="sxs-lookup"><span data-stu-id="21cb8-128">To use a binding in a service</span></span>  
  
1.  <span data-ttu-id="21cb8-129">前の手順のコードの後に、この手順のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-129">Insert this procedure's code after the code from the preceding procedure.</span></span>  
  
2.  <span data-ttu-id="21cb8-130"><xref:System.Type> という名前の `contractType` 変数を作成し、その変数にインターフェイスの型 (`ICalculator`) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="21cb8-131">[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] を使用している場合は、`GetType` 演算子を使用し、C# を使用している場合は、`typeof` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-131">When using [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>  
  
3.  <span data-ttu-id="21cb8-132">`Type` という名前の 2 つ目の `serviceType` 変数を作成し、その変数に実装されたコントラクトの型 (`Calculator`) を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-132">Create a second `Type` variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>  
  
4.  <span data-ttu-id="21cb8-133"><xref:System.Uri> という名前で、サービスのベース アドレスが指定された `baseAddress` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="21cb8-134">ベース アドレスには、トランスポートに一致するスキームを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21cb8-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="21cb8-135">この場合、トランスポート スキームは HTTP であり、アドレスは、特別な URI (Uniform Resource Identifier) の "localhost"、ポート番号 (8036)、およびベース エンドポイント アドレス ("serviceModelSamples/) で構成されます。つまり、http://localhost:8036/serviceModelSamples/ になります。</span><span class="sxs-lookup"><span data-stu-id="21cb8-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): http://localhost:8036/serviceModelSamples/.</span></span>  
  
5.  <span data-ttu-id="21cb8-136"><xref:System.ServiceModel.ServiceHost> 変数と `serviceType` 変数を指定して、`baseAddress` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>  
  
6.  <span data-ttu-id="21cb8-137">`contractType`、バインディング、およびエンドポイント名 (secureCalculator) を使用して、サービスにエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="21cb8-138">クライアントは、サービスへの呼び出しを開始するときに、ベース アドレスとエンドポイント名を連結する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21cb8-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>  
  
7.  <span data-ttu-id="21cb8-139"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> メソッドを呼び出してサービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="21cb8-140">この手順で使用するコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="21cb8-140">The code for this procedure is shown here:</span></span>  
  
     [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
     [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="21cb8-141">クライアントでのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="21cb8-141">Using the Binding in a Client</span></span>  
 <span data-ttu-id="21cb8-142">この手順では、サービスと通信するプロキシの生成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="21cb8-143">プロキシが生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータを使用してプロキシを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>  
  
 <span data-ttu-id="21cb8-144">この手順では、サービスと通信するための <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスも作成され、サービスが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>  
  
 <span data-ttu-id="21cb8-145">この例では、コードだけを使用してクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-145">This example uses only code to create the client.</span></span> <span data-ttu-id="21cb8-146">この手順の後のセクションに示す構成ファイルを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="21cb8-147">コードによってクライアントでバインディングを使用するには</span><span class="sxs-lookup"><span data-stu-id="21cb8-147">To use a binding in a client with code</span></span>  
  
1.  <span data-ttu-id="21cb8-148">SvcUtil.exe ツールを使用して、サービスのメタデータからプロキシ コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="21cb8-149">[する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-149"> [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="21cb8-150">生成されたプロキシ コードは <xref:System.ServiceModel.ClientBase%601> クラスから継承しているので、各クライアントには、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスとの通信に必要なコンストラクター、メソッド、およびプロパティが確実に定義されます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="21cb8-151">この例では、生成されたコードに、`CalculatorClient` インターフェイスを実装した `ICalculator` クラスが追加されるので、サービス コードとの互換が可能になります。</span><span class="sxs-lookup"><span data-stu-id="21cb8-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>  
  
2.  <span data-ttu-id="21cb8-152">この手順のコードは、クライアント プログラムの `Main` メソッドの先頭に挿入します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
3.  <span data-ttu-id="21cb8-153"><xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードを `Message` に、そのクライアント資格情報の種類を `Windows` に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="21cb8-154">この例では、変数に `clientBinding` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-154">The example names the variable `clientBinding`.</span></span>  
  
4.  <span data-ttu-id="21cb8-155"><xref:System.ServiceModel.EndpointAddress> という名前の `serviceAddress` クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="21cb8-156">エンドポイント名が連結されたベース アドレスでインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>  
  
5.  <span data-ttu-id="21cb8-157">`serviceAddress` 変数と `clientBinding` 変数を指定して、生成されたクライアント クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>  
  
6.  <span data-ttu-id="21cb8-158">次のコードに示すように、<xref:System.ServiceModel.ClientBase%601.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
7.  <span data-ttu-id="21cb8-159">サービスを呼び出し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-159">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
     [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]  
  
## <a name="using-the-configuration-file"></a><span data-ttu-id="21cb8-160">構成ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="21cb8-160">Using the Configuration File</span></span>  
 <span data-ttu-id="21cb8-161">手順コードを使用してバインディングを作成する代わりに、構成ファイルのバインディング セクションに次のコードを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>  
  
 <span data-ttu-id="21cb8-162">定義されたサービスがない場合は、次を参照してください。[を設計および実装するサービス](../../../docs/framework/wcf/designing-and-implementing-services.md)、および[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
 <span data-ttu-id="21cb8-163">**注**この構成コードは、サービスとクライアントの構成ファイルで使用します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-163">**Note** This configuration code is used in both the service and client configuration files.</span></span>  
  
#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="21cb8-164">構成を使用して Windows ドメインのサービスで転送セキュリティを有効にするには</span><span class="sxs-lookup"><span data-stu-id="21cb8-164">To enable transfer security on a service in a Windows domain using configuration</span></span>  
  
1.  <span data-ttu-id="21cb8-165">追加、 [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素を[\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素のセクションです。</span><span class="sxs-lookup"><span data-stu-id="21cb8-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="21cb8-166"><`binding`> 要素に <`WSHttpBinding`> 要素を追加し、`configurationName` 属性をアプリケーションに適した値に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>  
  
3.  <span data-ttu-id="21cb8-167"><`security`> 要素を追加し、`mode` 属性を Message に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>  
  
4.  <span data-ttu-id="21cb8-168"><`message`> 要素を追加し、`clientCredentialType` 属性を Windows に設定します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>  
  
5.  <span data-ttu-id="21cb8-169">サービスの構成ファイルで、`<bindings>` セクションを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="21cb8-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="21cb8-170">サービス構成ファイルがあるまだない場合は、次を参照してください。[を使用してサービスを構成するとクライアントのバインド](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="21cb8-171">クライアントでのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="21cb8-171">Using the Binding in a Client</span></span>  
 <span data-ttu-id="21cb8-172">この手順では、サービスと通信するプロキシと構成ファイルの 2 つのファイルの生成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="21cb8-173">また、クライアント上で使用される 3 つ目のファイルであるクライアント プログラムへの変更点についても説明します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-173">It also describes changes to the client program, which is the third file used on the client.</span></span>  
  
##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="21cb8-174">構成によってクライアントでバインディングを使用するには</span><span class="sxs-lookup"><span data-stu-id="21cb8-174">To use a binding in a client with configuration</span></span>  
  
1.  <span data-ttu-id="21cb8-175">SvcUtil.exe ツールを使用して、サービスのメタデータからプロキシ コードと構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="21cb8-176">[する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="21cb8-176"> [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="21cb8-177">置換、 [\<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)前のセクションの構成コードで生成された構成ファイルのセクションです。</span><span class="sxs-lookup"><span data-stu-id="21cb8-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>  
  
3.  <span data-ttu-id="21cb8-178">手順コードは、クライアント プログラムの `Main` メソッドの先頭に挿入します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>  
  
4.  <span data-ttu-id="21cb8-179">生成されたクライアント クラスのインスタンスを作成します。このとき、構成ファイルのバインディングの名前を入力パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>  
  
5.  <span data-ttu-id="21cb8-180">次のコードに示すように、<xref:System.ServiceModel.ClientBase%601.Open%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>  
  
6.  <span data-ttu-id="21cb8-181">サービスを呼び出し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="21cb8-181">Call the service and display the results.</span></span>  
  
     [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="21cb8-182">例</span><span class="sxs-lookup"><span data-stu-id="21cb8-182">Example</span></span>  
 [!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]  
  
 [!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)] 
 [!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]      
  
## <a name="see-also"></a><span data-ttu-id="21cb8-183">関連項目</span><span class="sxs-lookup"><span data-stu-id="21cb8-183">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpBinding>  
 [<span data-ttu-id="21cb8-184">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="21cb8-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="21cb8-185">方法: クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="21cb8-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="21cb8-186">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="21cb8-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="21cb8-187">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="21cb8-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
