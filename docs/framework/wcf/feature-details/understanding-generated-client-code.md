---
title: "生成されたクライアント コードの理解"
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
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 935f3fe168ebafd7a62c54d2aec1c8336a31a54a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="understanding-generated-client-code"></a><span data-ttu-id="8af31-102">生成されたクライアント コードの理解</span><span class="sxs-lookup"><span data-stu-id="8af31-102">Understanding Generated Client Code</span></span>
<span data-ttu-id="8af31-103">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) は、クライアント アプリケーションの構築時に使用するクライアント コードとクライアント アプリケーション構成ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="8af31-103">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generates client code and a client application configuration file for use in building client applications.</span></span> <span data-ttu-id="8af31-104">このトピックでは、標準サービス コントラクトのシナリオ向けに生成されたコード例について説明します。</span><span class="sxs-lookup"><span data-stu-id="8af31-104">This topic provides a tour of generated code examples for standard service contract scenarios.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8af31-105"> については、「 [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af31-105"> building a client application using the generated code, see [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8af31-106">概要</span><span class="sxs-lookup"><span data-stu-id="8af31-106">Overview</span></span>  
 <span data-ttu-id="8af31-107">プロジェクトで [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント型を生成する場合、通常、生成されたクライアント コードを調べる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8af31-107">If you use [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] to generate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client types for your project, you typically do not need to examine the generated client code.</span></span> <span data-ttu-id="8af31-108">同じサービスを実行する開発環境を使用していない場合は、Svcutil.exe のようなツールを使用してクライアント コードを生成し、そのコードでクライアント アプリケーションを開発します。</span><span class="sxs-lookup"><span data-stu-id="8af31-108">If you are not using a development environment that performs the same services for you, you can use a tool such as Svcutil.exe to generate client code and then use that code to develop your client application.</span></span>  
  
 <span data-ttu-id="8af31-109">Svcutil.exe には、生成された型情報を変更する多くのオプションがあるため、ここですべてのシナリオを説明することはできません。</span><span class="sxs-lookup"><span data-stu-id="8af31-109">Because Svcutil.exe has a number of options that modify the generated type information, this topic does not discuss all scenarios.</span></span> <span data-ttu-id="8af31-110">ここでは、生成されたコードの検索に関する標準的な作業の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="8af31-110">However, the following standard tasks involve locating generated code:</span></span>  
  
-   <span data-ttu-id="8af31-111">サービス コントラクト インターフェイスの識別</span><span class="sxs-lookup"><span data-stu-id="8af31-111">Identifying service contract interfaces.</span></span>  
  
-   <span data-ttu-id="8af31-112">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスの識別</span><span class="sxs-lookup"><span data-stu-id="8af31-112">Identifying the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span>  
  
-   <span data-ttu-id="8af31-113">データ型の識別</span><span class="sxs-lookup"><span data-stu-id="8af31-113">Identifying data types.</span></span>  
  
-   <span data-ttu-id="8af31-114">双方向サービスのコールバック コントラクトの識別</span><span class="sxs-lookup"><span data-stu-id="8af31-114">Identifying callback contracts for duplex services.</span></span>  
  
-   <span data-ttu-id="8af31-115">ヘルパーのサービス コントラクトのチャネル インターフェイスの識別</span><span class="sxs-lookup"><span data-stu-id="8af31-115">Identifying the helper service contract channel interface.</span></span>  
  
### <a name="finding-service-contract-interfaces"></a><span data-ttu-id="8af31-116">サービス コントラクト インターフェイスの検索</span><span class="sxs-lookup"><span data-stu-id="8af31-116">Finding Service Contract Interfaces</span></span>  
 <span data-ttu-id="8af31-117">サービス コントラクトをモデル化するインターフェイスを検索するには、<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 属性でマークされたインターフェイスを検索します。</span><span class="sxs-lookup"><span data-stu-id="8af31-117">To locate the interfaces that model service contracts, search for interfaces that are marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="8af31-118">多くの場合、属性自体に設定された他の属性や明示的なプロパティが存在するため、この属性をすばやく読み取って見つけることは簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="8af31-118">Often this attribute can be difficult to locate with a quick read due to the presence of other attributes and the explicit properties set on the attribute itself.</span></span> <span data-ttu-id="8af31-119">サービス コントラクト インターフェイスとクライアント コントラクト インターフェイスは 2 つの別の種類だという点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8af31-119">Remember that the service contract interface and the client contract interface are two different types.</span></span> <span data-ttu-id="8af31-120">次のコード例は、元のサービス コントラクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="8af31-120">The following code example shows the original service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 <span data-ttu-id="8af31-121">次のコード例は、Svcutil.exe で生成された同じサービス コントラクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="8af31-121">The following code example shows the same service contract as generated by Svcutil.exe.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="8af31-122">生成されたサービス コントラクト インターフェイスと <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> クラスを使用して、サービス操作の呼び出しに使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8af31-122">You can use the generated service contract interface along with the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> class to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel object with which to invoke service operations.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="8af31-123">[する方法: ChannelFactory を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)です。</span><span class="sxs-lookup"><span data-stu-id="8af31-123"> [How to: Use the ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).</span></span>  
  
### <a name="finding-wcf-client-classes"></a><span data-ttu-id="8af31-124">WCF クライアント クラスの検索</span><span class="sxs-lookup"><span data-stu-id="8af31-124">Finding WCF Client Classes</span></span>  
 <span data-ttu-id="8af31-125">使用するサービス コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスを検索するには、<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> の拡張を検索します。ここで、型パラメーターは、以前に検索され、自身を拡張するサービス コントラクト インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8af31-125">To locate the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class that implements the service contract you want to use, search for an extension of <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>, where the type parameter is the service contract interface that you previously located and that extends that interface.</span></span> <span data-ttu-id="8af31-126">次のコード例は、 <xref:System.ServiceModel.ClientBase%601> 型の `ISampleService`クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="8af31-126">The following code example shows the <xref:System.ServiceModel.ClientBase%601> class of type `ISampleService`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="8af31-127">この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント クラスを使用するには、新しいインスタンスを作成し、このクラスに実装されているメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8af31-127">You can use this [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class by creating a new instance of it and calling the methods it implements.</span></span> <span data-ttu-id="8af31-128">これらのメソッドは、対応しているサービス操作を呼び出し、やり取りを行うように構成されています。</span><span class="sxs-lookup"><span data-stu-id="8af31-128">Those methods invoke the service operation with which it is designed and configured to interact.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="8af31-129">[WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="8af31-129"> [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8af31-130">SvcUtil.exe で WCF クライアント クラスが生成されるとき、 <xref:System.Diagnostics.DebuggerStepThroughAttribute> がクライアント クラスに追加されるため、デバッガーで WCF クライアント クラスをステップ実行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8af31-130">When SvcUtil.exe generates a WCF client class, it adds a <xref:System.Diagnostics.DebuggerStepThroughAttribute> to the client class that prevents debuggers from stepping through the WCF client class.</span></span>  
  
### <a name="finding-data-types"></a><span data-ttu-id="8af31-131">データ型の検索</span><span class="sxs-lookup"><span data-stu-id="8af31-131">Finding Data Types</span></span>  
 <span data-ttu-id="8af31-132">生成されたコード内でデータ型を検索する最も基本的な方法は、コントラクトに指定された型名を識別し、その型宣言のコードを検索することです。</span><span class="sxs-lookup"><span data-stu-id="8af31-132">To locate data types in the generated code, the most basic mechanism is to identify the type name specified in a contract and search the code for that type declaration.</span></span> <span data-ttu-id="8af31-133">たとえば、次のコントラクトには、 `SampleMethod` が型 `microsoft.wcf.documentation.SampleFault`の SOAP エラーを返せることが指定されています。</span><span class="sxs-lookup"><span data-stu-id="8af31-133">For example, the following contract specifies that the `SampleMethod` can return a SOAP fault of type `microsoft.wcf.documentation.SampleFault`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 <span data-ttu-id="8af31-134">`SampleFault` を検索すると、次の型宣言が見つかります。</span><span class="sxs-lookup"><span data-stu-id="8af31-134">Searching for `SampleFault` locates the following type declaration.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 <span data-ttu-id="8af31-135">この場合、このデータ型は、クライアントの特定の例外 ( <xref:System.ServiceModel.FaultException%601> ) によりスローされる詳細な型です。詳細な型のパラメーターは、 `microsoft.wcf.documentation.SampleFault`です。</span><span class="sxs-lookup"><span data-stu-id="8af31-135">In this case the data type is the detail type thrown by a specific exception on the client, a <xref:System.ServiceModel.FaultException%601> where the detail type parameter is `microsoft.wcf.documentation.SampleFault`.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8af31-136"> については、「 [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af31-136"> data types, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8af31-137"> については、「 [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8af31-137"> handling exceptions in clients, see [Sending and Receiving Faults](../../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span>  
  
### <a name="finding-callback-contracts-for-duplex-services"></a><span data-ttu-id="8af31-138">双方向サービスのコールバック コントラクトの検索</span><span class="sxs-lookup"><span data-stu-id="8af31-138">Finding Callback Contracts for Duplex Services</span></span>  
 <span data-ttu-id="8af31-139">コントラクト インターフェイスにより <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> プロパティの値が指定されているサービス コントラクトを検索すると、そのコントラクトには双方向コントラクトが指定されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8af31-139">If you locate a service contract for which the contract interface specifies a value for the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property, then that contract specifies a duplex contract.</span></span> <span data-ttu-id="8af31-140">二重のコントラクトを使用した場合、クライアント アプリケーションは、コールバック コントラクトを実装するコールバック クラスを作成し、そのクラスのインスタンスを、サービスとの通信に使用する <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> または <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8af31-140">Duplex contracts require the client application to create a callback class that implements the callback contract and pass an instance of that class to the <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> or <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> used to communicate with the service.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8af31-141">双方向クライアントを参照してください[する方法: 双方向コントラクトでサービスをアクセス](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="8af31-141"> duplex clients, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="8af31-142">次のコントラクトは、型 `SampleDuplexHelloCallback`のコールバック コントラクトを指定しています。</span><span class="sxs-lookup"><span data-stu-id="8af31-142">The following contract specifies a callback contract of type `SampleDuplexHelloCallback`.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 <span data-ttu-id="8af31-143">このコールバック コントラクトを検索すると、クライアント アプリケーションが実装する必要のある次のインターフェイスが見つかります。</span><span class="sxs-lookup"><span data-stu-id="8af31-143">Searching for that callback contract locates the following interface that the client application must implement.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a><span data-ttu-id="8af31-144">サービス コントラクト チャネル インターフェイスの検索</span><span class="sxs-lookup"><span data-stu-id="8af31-144">Finding Service Contract Channel Interfaces</span></span>  
 <span data-ttu-id="8af31-145">サービス コントラクト インターフェイスで <xref:System.ServiceModel.ChannelFactory> クラスを使用する場合、明示的にチャネルを開いたり、閉じたり、中止したりするには、<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> インターフェイスにキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8af31-145">When using the <xref:System.ServiceModel.ChannelFactory> class with a service contract interface, you must cast to the <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to explicitly open, close, or abort the channel.</span></span> <span data-ttu-id="8af31-146">処理を容易にするために、Svcutil.exe ツールでは、サービス コントラクト インターフェイスと <xref:System.ServiceModel.IClientChannel> の両方を実装するヘルパー インターフェイスも生成されます。これにより、キャストを行わずにクライアント チャネル インフラストラクチャとのやりとりを実現できます。</span><span class="sxs-lookup"><span data-stu-id="8af31-146">To make it easier to work with, the Svcutil.exe tool also generates a helper interface that implements both the service contract interface and <xref:System.ServiceModel.IClientChannel> to enable you to interact with the client channel infrastructure without having to cast.</span></span> <span data-ttu-id="8af31-147">上記のサービス コントラクトを実装するヘルパー クライアント チャネルの定義を、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="8af31-147">The following code shows the definition of a helper client channel that implements the preceding service contract.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="8af31-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="8af31-148">See Also</span></span>  
 [<span data-ttu-id="8af31-149">WCF クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="8af31-149">WCF Client Overview</span></span>](../../../../docs/framework/wcf/wcf-client-overview.md)
