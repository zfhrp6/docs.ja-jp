---
title: WCF クライアントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], architecture
ms.assetid: f60d9bc5-8ade-4471-8ecf-5a07a936c82d
ms.openlocfilehash: 03a9580bee6308ef53c7d2bc6e9dbe619c2048f7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-client-overview"></a><span data-ttu-id="2f14e-102">WCF クライアントの概要</span><span class="sxs-lookup"><span data-stu-id="2f14e-102">WCF Client Overview</span></span>
<span data-ttu-id="2f14e-103">このセクションでは、クライアント アプリケーションの処理、構成、作成、および Windows Communication Foundation (WCF) クライアントを使用する方法、およびクライアント アプリケーションをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-103">This section describes what client applications do, how to configure, create, and use a Windows Communication Foundation (WCF) client, and how to secure client applications.</span></span>  
  
## <a name="using-wcf-client-objects"></a><span data-ttu-id="2f14e-104">WCF クライアント オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="2f14e-104">Using WCF Client Objects</span></span>  
 <span data-ttu-id="2f14e-105">クライアント アプリケーションは、別のアプリケーションと通信する WCF クライアントを使用するマネージ アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-105">A client application is a managed application that uses a WCF client to communicate with another application.</span></span> <span data-ttu-id="2f14e-106">クライアントを作成するのには、WCF サービスのアプリケーションには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-106">To create a client application for a WCF service requires the following steps:</span></span>  
  
1.  <span data-ttu-id="2f14e-107">サービス エンドポイントのサービス コントラクト、バインディング、およびアドレス情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-107">Obtain the service contract, bindings, and address information for a service endpoint.</span></span>  
  
2.  <span data-ttu-id="2f14e-108">情報を使用する WCF クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-108">Create a WCF client using that information.</span></span>  
  
3.  <span data-ttu-id="2f14e-109">操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-109">Call operations.</span></span>  
  
4.  <span data-ttu-id="2f14e-110">WCF クライアント オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-110">Close the WCF client object.</span></span>  
  
 <span data-ttu-id="2f14e-111">この後の各セクションでは、これらの手順について詳しく説明します。また、次の内容についても簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-111">The following sections discuss these steps and provide brief introductions to the following issues:</span></span>  
  
-   <span data-ttu-id="2f14e-112">エラー処理</span><span class="sxs-lookup"><span data-stu-id="2f14e-112">Handling errors.</span></span>  
  
-   <span data-ttu-id="2f14e-113">クライアントの構成とセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2f14e-113">Configuring and securing clients.</span></span>  
  
-   <span data-ttu-id="2f14e-114">双方向サービスのコールバック オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2f14e-114">Creating callback objects for duplex services.</span></span>  
  
-   <span data-ttu-id="2f14e-115">サービスの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f14e-115">Calling services asynchronously.</span></span>  
  
-   <span data-ttu-id="2f14e-116">クライアント チャネルを使用したサービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f14e-116">Calling services using client channels.</span></span>  
  
## <a name="obtain-the-service-contract-bindings-and-addresses"></a><span data-ttu-id="2f14e-117">サービス コントラクト、バインディング、およびアドレスを取得する</span><span class="sxs-lookup"><span data-stu-id="2f14e-117">Obtain the Service Contract, Bindings, and Addresses</span></span>  
 <span data-ttu-id="2f14e-118">WCF では、サービスとクライアントは、マネージ属性、インターフェイス、およびメソッドを使用してコントラクトをモデルします。</span><span class="sxs-lookup"><span data-stu-id="2f14e-118">In WCF, services and clients model contracts using managed attributes, interfaces, and methods.</span></span> <span data-ttu-id="2f14e-119">クライアント アプリケーションからサービスに接続するには、そのサービス コントラクトの型情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-119">To connect to a service in a client application, you need to obtain the type information for the service contract.</span></span> <span data-ttu-id="2f14e-120">通常、これを行うを使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)、サービスからメタデータをダウンロード、任意の言語でのマネージ ソース コード ファイルに変換され、クライアントを作成アプリケーション構成ファイル、WCF クライアント オブジェクトを構成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-120">Typically, you do this by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), which downloads metadata from the service, converts it to a managed source code file in the language of your choice, and creates a client application configuration file that you can use to configure your WCF client object.</span></span> <span data-ttu-id="2f14e-121">呼び出すための WCF クライアント オブジェクトを作成しようとする場合など、`MyCalculatorService`でそのサービスのメタデータが公開されていることがわかって`http://computerName/MyCalculatorService/Service.svc?wsdl`、次のコード例は、Svcutil.exe を使用して取得する方法を示します、`ClientCode.vb`ファイルマネージ コードにサービス コントラクトを含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f14e-121">For example, if you are going to create an WCF client object to invoke a `MyCalculatorService`, and you know that the metadata for that service is published at `http://computerName/MyCalculatorService/Service.svc?wsdl`, then the following code example shows how to use Svcutil.exe to obtain a `ClientCode.vb` file that contains the service contract in managed code.</span></span>  
  
```  
svcutil /language:vb /out:ClientCode.vb /config:app.config http://computerName/MyCalculatorService/Service.svc?wsdl  
```  
  
 <span data-ttu-id="2f14e-122">クライアント アプリケーションまたはクライアント アプリケーションは WCF クライアント オブジェクトを作成し、使用できる別のアセンブリには、このコントラクト コードをコンパイルすることができますか。</span><span class="sxs-lookup"><span data-stu-id="2f14e-122">You can either compile this contract code into the client application or into another assembly that the client application can then use to create an WCF client object.</span></span> <span data-ttu-id="2f14e-123">構成ファイルを使用してサービスに正しく接続するクライアント オブジェクトを構成できます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-123">You can use the configuration file to configure the client object to properly connect to the service .</span></span>  
  
 <span data-ttu-id="2f14e-124">このプロセスの例は、次を参照してください。[する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-124">For an example of this process, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="2f14e-125">コントラクトの詳細については、次を参照してください。[コントラクト](../../../docs/framework/wcf/feature-details/contracts.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-125">For more complete information about contracts, see [Contracts](../../../docs/framework/wcf/feature-details/contracts.md).</span></span>  
  
## <a name="create-a-wcf-client-object"></a><span data-ttu-id="2f14e-126">WCF クライアント オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2f14e-126">Create a WCF Client Object</span></span>  
 <span data-ttu-id="2f14e-127">WCF クライアントは、クライアントは、リモート サービスと通信するために使用できる形式で WCF サービスを表すローカル オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-127">A WCF client is a local object that represents a WCF service in a form that the client can use to communicate with the remote service.</span></span> <span data-ttu-id="2f14e-128">WCF クライアントの種類が対象となるサービスを実装するコントラクトを作成し、構成したときに使用できるようにし、クライアント オブジェクト直接サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-128">WCF client types implement the target service contract, so when you create one and configure it, you can then use the client object directly to invoke service operations.</span></span> <span data-ttu-id="2f14e-129">WCF ランタイム メソッドの呼び出しをメッセージに変換、サービスに送信、応答、リッスンおよび戻り値として、WCF クライアント オブジェクトにこれらの値を返しますまたは`out`または`ref`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="2f14e-129">The WCF run time converts the method calls into messages, sends them to the service, listens for the reply, and returns those values to the WCF client object as return values or `out` or `ref` parameters.</span></span>  
  
 <span data-ttu-id="2f14e-130">接続してサービスを使用して WCF クライアント チャネル オブジェクトを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-130">You can also use WCF client channel objects to connect with and use services.</span></span> <span data-ttu-id="2f14e-131">詳細については、「 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-131">For details, see [WCF Client Architecture](../../../docs/framework/wcf/feature-details/client-architecture.md).</span></span>  
  
#### <a name="creating-a-new-wcf-object"></a><span data-ttu-id="2f14e-132">新しい WCF オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2f14e-132">Creating a New WCF Object</span></span>  
 <span data-ttu-id="2f14e-133">サービスアプリケーションから次の簡単なサービス コントラクトが生成されていることを前提に、<xref:System.ServiceModel.ClientBase%601> クラスの使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-133">To illustrate the use of a <xref:System.ServiceModel.ClientBase%601> class, assume the following simple service contract has been generated from a service application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f14e-134">WCF クライアントを作成するのには、Visual Studio を使用する、オブジェクトはサービス参照をプロジェクトに追加するときにオブジェクト ブラウザーに自動的に読み込まれです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-134">If you are using Visual Studio to create your WCF client, objects are loaded automatically into the object browser when you add a service reference to your project.</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 <span data-ttu-id="2f14e-135">Visual Studio を使用していない場合、生成されるコントラクト コードを調べを拡張する型を見つける<xref:System.ServiceModel.ClientBase%601>とサービス コントラクト インターフェイス`ISampleService`です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-135">If you are not using Visual Studio, examine the generated contract code to find the type that extends <xref:System.ServiceModel.ClientBase%601> and the service contract interface `ISampleService`.</span></span> <span data-ttu-id="2f14e-136">この場合、この型は次のようなコードになります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-136">In this case, that type looks like the following code:</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 <span data-ttu-id="2f14e-137">このクラスを、コンストラクターの 1 つを使用してローカル オブジェクトとして作成し、構成して、型 `ISampleService` のサービスへの接続に使用できます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-137">This class can be created as a local object using one of the constructors, configured, and then used to connect to a service of the type `ISampleService`.</span></span>  
  
 <span data-ttu-id="2f14e-138">最初に、WCF クライアント オブジェクトを作成し、それを使用して閉じて 1 つの try/catch ブロック内をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2f14e-138">It is recommended that you create your WCF client object first, and then use it and close it inside a single try/catch block.</span></span> <span data-ttu-id="2f14e-139">使用しないで、`using`ステートメント (`Using` Visual Basic で) ため、特定のエラー モードで例外をマスクすることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-139">You should not use the `using` statement (`Using` in Visual Basic) because it may mask exceptions in certain failure modes.</span></span> <span data-ttu-id="2f14e-140">詳細については、次のセクションを参照してください。 だけでなく[Using ステートメントに関する問題を回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-140">For more information, see the following sections as well as [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).</span></span>  
  
### <a name="contracts-bindings-and-addresses"></a><span data-ttu-id="2f14e-141">コントラクト、バインディング、およびアドレス</span><span class="sxs-lookup"><span data-stu-id="2f14e-141">Contracts, Bindings, and Addresses</span></span>  
 <span data-ttu-id="2f14e-142">WCF クライアント オブジェクトを作成することができます、前に、クライアント オブジェクトを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-142">Before you can create a WCF client object, you must configure the client object.</span></span> <span data-ttu-id="2f14e-143">具体的には、サービスがあります*エンドポイント*を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-143">Specifically, it must have a service *endpoint* to use.</span></span> <span data-ttu-id="2f14e-144">エンドポイントは、サービス コントラクト、バインディング、およびアドレスの組み合わせです </span><span class="sxs-lookup"><span data-stu-id="2f14e-144">An endpoint is the combination of a service contract, a binding, and an address.</span></span> <span data-ttu-id="2f14e-145">(エンドポイントの詳細については、次を参照してください[エンドポイント: アドレス、バインディング、およびコントラクト](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)。)。通常、この情報にある、 [\<エンドポイント >](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)もの、Svcutil.exe ツールを生成して、クライアントを作成するときに自動的に読み込まれますなど、クライアント アプリケーション構成ファイル内の要素オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2f14e-145">(For more information about endpoints, see [Endpoints: Addresses, Bindings, and Contracts](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md).) Typically, this information is located in the [\<endpoint>](../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md) element in a client application configuration file, such as the one the Svcutil.exe tool generates, and is loaded automatically when you create your client object.</span></span> <span data-ttu-id="2f14e-146">WCF クライアントのどちらも使用すると、プログラムでこの情報を指定するオーバー ロードがあります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-146">Both WCF client types also have overloads that enable you to programmatically specify this information.</span></span>  
  
 <span data-ttu-id="2f14e-147">たとえば、上記の例で使用した `ISampleService` 用に生成された構成ファイルには、次のエンドポイント情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-147">For example, a generated configuration file for an `ISampleService` used in the preceding examples contains the following endpoint information.</span></span>  
  
 [!code-xml[C_GeneratedCodeFiles#19](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/common/client.exe.config#19)]  
  
 <span data-ttu-id="2f14e-148">この構成ファイルの `<client>` 要素には、ターゲット エンドポイントが指定されます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-148">This configuration file specifies a target endpoint in the `<client>` element.</span></span> <span data-ttu-id="2f14e-149">詳細については、複数のターゲット エンドポイントを使用して、次を参照してください。、<xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType>または<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-149">For more information about using multiple target endpoints, see the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A?displayProperty=nameWithType> constructors.</span></span>  
  
## <a name="calling-operations"></a><span data-ttu-id="2f14e-150">操作の呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f14e-150">Calling Operations</span></span>  
 <span data-ttu-id="2f14e-151">1 回するクライアント オブジェクトを作成し、構成して、try ブロックと catch ブロックを作成する、オブジェクトは、ローカルの場合と同じ方法で操作を呼び出す、WCF クライアント オブジェクトを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-151">Once you have a client object created and configured, create a try/catch block, call operations in the same way that you would if the object were local, and close the WCF client object.</span></span> <span data-ttu-id="2f14e-152">クライアント アプリケーションが最初の操作を呼び出すし、WCF は、基になるチャネルを自動的に開きますオブジェクトがリサイクルされるときに、基になるチャネルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-152">When the client application calls the first operation, WCF automatically opens the underlying channel, and the underlying channel is closed when the object is recycled.</span></span> <span data-ttu-id="2f14e-153">(また、他の操作を呼び出す前後にチャネルを明示的に開いたり閉じたりすることもできます)。</span><span class="sxs-lookup"><span data-stu-id="2f14e-153">(Alternatively, you can also explicitly open and close the channel prior to or subsequent to calling other operations.)</span></span>  
  
 <span data-ttu-id="2f14e-154">たとえば、次のようなサービス コントラクトを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-154">For example, if you have the following service contract:</span></span>  
  
```csharp  
namespace Microsoft.ServiceModel.Samples  
{  
    using System;  
    using System.ServiceModel;  
  
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
   {  
        [OperationContract]  
        double Add(double n1, double n2);  
        [OperationContract]  
        double Subtract(double n1, double n2);  
        [OperationContract]  
        double Multiply(double n1, double n2);  
        [OperationContract]  
        double Divide(double n1, double n2);  
    }  
}  
```  
  
```vb  
Namespace Microsoft.ServiceModel.Samples  
  
    Imports System  
    Imports System.ServiceModel  
  
    <ServiceContract(Namespace:= _  
    "http://Microsoft.ServiceModel.Samples")> _   
   Public Interface ICalculator  
        <OperationContract> _   
        Function Add(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Subtract(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
        Function Multiply(n1 As Double, n2 As Double) As Double  
        <OperationContract> _   
     Function Divide(n1 As Double, n2 As Double) As Double  
End Interface  
```  
  
 <span data-ttu-id="2f14e-155">WCF クライアント オブジェクトを作成することで、操作を呼び出すことができ、次のコード例として、そのメソッドを呼び出すことを示します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-155">You can call operations by creating a WCF client object and calling its methods, as the following code example demonstrates.</span></span> <span data-ttu-id="2f14e-156">開始タグを呼び出しと WCF クライアント オブジェクトの終了が 1 つの try/catch ブロック内で発生することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2f14e-156">Note that the opening, calling, and closing of the WCF client object occurs within a single try/catch block.</span></span> <span data-ttu-id="2f14e-157">詳細については、次を参照してください。[にアクセスするサービスの WCF クライアントを使用して](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)と[Using ステートメントに関する問題を回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-157">For more information, see [Accessing Services Using a WCF Client](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md) and [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).</span></span>  
  
 [!code-csharp[C_GeneratedCodeFiles#20](../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#20)]  
  
## <a name="handling-errors"></a><span data-ttu-id="2f14e-158">エラー処理</span><span class="sxs-lookup"><span data-stu-id="2f14e-158">Handling Errors</span></span>  
 <span data-ttu-id="2f14e-159">基になるクライアント チャネルを開いたとき (明示的に開いた場合、または操作を呼び出すことによって自動的に開いた場合)、クライアントまたはチャネル オブジェクトを使用して操作を呼び出したとき、基になるクライアント チャネルを閉じたときときに、クライアント アプリケーションで例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-159">Exceptions can occur in a client application when opening the underlying client channel (whether explicitly or automatically by calling an operation), using the client or channel object to call operations, or when closing the underlying client channel.</span></span> <span data-ttu-id="2f14e-160">少なくともアプリケーションでは、操作から返される SOAP エラーの結果としてスローされる <xref:System.TimeoutException?displayProperty=nameWithType> オブジェクトに加え、可能性のある <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> 例外と <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 例外を処理することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2f14e-160">It is recommended at a minimum that applications expect to handle possible <xref:System.TimeoutException?displayProperty=nameWithType> and <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType> exceptions in addition to any <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> objects thrown as a result of SOAP faults returned by operations.</span></span> <span data-ttu-id="2f14e-161">操作コントラクトで指定されている SOAP エラーは、<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> としてクライアント アプリケーションに送信されます。ここで、型パラメーターは SOAP エラーの詳細な型です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-161">SOAP faults specified in the operation contract are raised to client applications as a <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the type parameter is the detail type of the SOAP fault.</span></span> <span data-ttu-id="2f14e-162">クライアント アプリケーションでエラー状態の処理の詳細については、次を参照してください。[送信と受信エラー](../../../docs/framework/wcf/sending-and-receiving-faults.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-162">For more information about handling error conditions in a client application, see [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span> <span data-ttu-id="2f14e-163">完全なサンプルに示すクライアントでのエラーを処理する方法を参照してください[予想例外](../../../docs/framework/wcf/samples/expected-exceptions.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-163">For a complete sample the shows how to handle errors in a client, see [Expected Exceptions](../../../docs/framework/wcf/samples/expected-exceptions.md).</span></span>  
  
## <a name="configuring-and-securing-clients"></a><span data-ttu-id="2f14e-164">クライアントの構成とセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2f14e-164">Configuring and Securing Clients</span></span>  
 <span data-ttu-id="2f14e-165">クライアントを構成するには、まず、そのクライアントまたはチャネル オブジェクトに必要なターゲット エンドポイント情報を読み込みます。通常は構成ファイルから読み込みますが、クライアント コンストラクターとプロパティを使用してプログラムで読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-165">Configuring a client starts with the required loading of target endpoint information for the client or channel object, usually from a configuration file, although you can also load this information programmatically using the client constructors and properties.</span></span> <span data-ttu-id="2f14e-166">ただし、特定のクライアントの動作を有効にし、多くのセキュリティ シナリオに対応するには、追加の構成手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-166">However, additional configuration steps are required to enable certain client behavior and for many security scenarios.</span></span>  
  
 <span data-ttu-id="2f14e-167">たとえば、サービス コントラクトのセキュリティ要件はサービス コントラクト インターフェイスに宣言します。Svcutil.exe で構成ファイルを作成した場合、通常そのファイルにはサービスのセキュリティ要件に対応できるバインディングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f14e-167">For example, security requirements for service contracts are declared in the service contract interface, and if Svcutil.exe created a configuration file, that file usually contains a binding that is capable of supporting the security requirements of the service.</span></span> <span data-ttu-id="2f14e-168">ただし、クライアント資格情報の構成など、さらに多くのセキュリティ構成が必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-168">In some cases, however, more security configuration may be required, such as configuring client credentials.</span></span> <span data-ttu-id="2f14e-169">WCF クライアントのセキュリティの構成の詳細については、次を参照してください。[クライアントのセキュリティで保護する](../../../docs/framework/wcf/securing-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-169">For complete information about the configuration of security for WCF clients, see [Securing Clients](../../../docs/framework/wcf/securing-clients.md).</span></span>  
  
 <span data-ttu-id="2f14e-170">また、カスタム ランタイム動作など、クライアント アプリケーションでいくつかのカスタム変更を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-170">In addition, some custom modifications can be enabled in client applications, such as custom run-time behaviors.</span></span> <span data-ttu-id="2f14e-171">カスタム クライアント動作を構成する方法の詳細については、次を参照してください。[クライアントの動作を構成する](../../../docs/framework/wcf/configuring-client-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-171">For more information about how to configure a custom client behavior, see [Configuring Client Behaviors](../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
## <a name="creating-callback-objects-for-duplex-services"></a><span data-ttu-id="2f14e-172">双方向サービスのコールバック オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2f14e-172">Creating Callback Objects for Duplex Services</span></span>  
 <span data-ttu-id="2f14e-173">双方向サービスには、コントラクトの要件に従って呼び出すサービスのコールバック オブジェクトを提供するために、クライアント アプリケーションが実装する必要のあるコールバック コントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-173">Duplex services specify a callback contract that the client application must implement in order to provide a callback object for the service to call according to the requirements of the contract.</span></span> <span data-ttu-id="2f14e-174">コールバック オブジェクトは完全なサービスではありません (たとえば、コールバック オブジェクトを使用してチャネルを初期化できません) が、実装と構成という目的においては、一種のサービスとして考えることができます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-174">Although callback objects are not full services (for example, you cannot initiate a channel with a callback object), for the purposes of implementation and configuration they can be thought of as a kind of service.</span></span>  
  
 <span data-ttu-id="2f14e-175">双方向サービスのクライアントでは、以下の処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f14e-175">Clients of duplex services must:</span></span>  
  
-   <span data-ttu-id="2f14e-176">コールバック コントラクト クラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-176">Implement a callback contract class.</span></span>  
  
-   <span data-ttu-id="2f14e-177">コールバック コントラクト実装クラスのインスタンスを作成し、使用して作成する、 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> WCF クライアント コンス トラクターに渡されたオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="2f14e-177">Create an instance of the callback contract implementation class and use it to create the <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> object that you pass to the WCF client constructor.</span></span>  
  
-   <span data-ttu-id="2f14e-178">操作を呼び出し、操作のコールバックを処理します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-178">Invoke operations and handle operation callbacks.</span></span>  
  
 <span data-ttu-id="2f14e-179">双方向の WCF クライアント オブジェクト関数などの双方向の対応すると、例外、コールバック サービスの構成など、コールバックをサポートするために必要な機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-179">Duplex WCF client objects function like their nonduplex counterparts, with the exception that they expose the functionality necessary to support callbacks, including the configuration of the callback service.</span></span>  
  
 <span data-ttu-id="2f14e-180">たとえば、コールバック クラスの <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> 属性のプロパティを使用して、コールバック オブジェクトの実行時の動作のさまざまな局面を制御できます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-180">For example, you can control various aspects of callback object runtime behavior by using properties of the <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType> attribute on the callback class.</span></span> <span data-ttu-id="2f14e-181">また、別の例として、<xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> クラスを使用して、例外情報をコールバック オブジェクトを呼び出したサービスに返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-181">Another example is the use of the <xref:System.ServiceModel.Description.CallbackDebugBehavior?displayProperty=nameWithType> class to enable the return of exception information to services that call the callback object.</span></span> <span data-ttu-id="2f14e-182">詳細については、次を参照してください。[双方向サービス](../../../docs/framework/wcf/feature-details/duplex-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-182">For more information, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span> <span data-ttu-id="2f14e-183">完全なサンプルについてを参照してください。[双方向](../../../docs/framework/wcf/samples/duplex.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-183">For a complete sample, see [Duplex](../../../docs/framework/wcf/samples/duplex.md).</span></span>  
  
 <span data-ttu-id="2f14e-184">インターネット インフォメーション サービス (IIS) 5.1 を実行する Windows XP コンピューターの場合、双方向クライアントでは <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> クラスを使用してクライアントのベース アドレスを指定する必要があります。そうしない場合は例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-184">On Windows XP computers running Internet Information Services (IIS) 5.1, duplex clients must specify a client base address using the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> class or an exception is thrown.</span></span> <span data-ttu-id="2f14e-185">次のコード例は、コードでこれを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-185">The following code example shows how to do this in code.</span></span>  
  
 [!code-csharp[S_DualHttp#8](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#8)]
 [!code-vb[S_DualHttp#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_dualhttp/vb/module1.vb#8)]  
  
 <span data-ttu-id="2f14e-186">次のコードは、構成ファイルでこれを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-186">The following code shows how to do this in a configuration file</span></span>  
  
 [!code-csharp[S_DualHttp#134](../../../samples/snippets/csharp/VS_Snippets_CFX/s_dualhttp/cs/program.cs#134)]  
  
## <a name="calling-services-asynchronously"></a><span data-ttu-id="2f14e-187">サービスの非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f14e-187">Calling Services Asynchronously</span></span>  
 <span data-ttu-id="2f14e-188">操作の呼び出し方法は、クライアント開発者に完全に依存します。</span><span class="sxs-lookup"><span data-stu-id="2f14e-188">How operations are called is entirely up to the client developer.</span></span> <span data-ttu-id="2f14e-189">これは、操作を構成するメッセージは、マネージ コードで表現するときに同期メソッドまたは非同期メソッドのどちらかにマップできるためです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-189">This is because the messages that make up an operation can be mapped to either synchronous or asynchronous methods when expressed in managed code.</span></span> <span data-ttu-id="2f14e-190">したがって、操作を非同期に呼び出すクライアントを作成する場合、Svcutil.exe の `/async` オプションを使用して非同期クライアント コードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-190">Therefore, if you want to build a client that calls operations asynchronously, you can use Svcutil.exe to generate asynchronous client code using the `/async` option.</span></span> <span data-ttu-id="2f14e-191">詳細については、次を参照してください。[する方法: サービスの操作を非同期に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-191">For more information, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
## <a name="calling-services-using-wcf-client-channels"></a><span data-ttu-id="2f14e-192">WCF クライアント チャネルを使用したサービスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="2f14e-192">Calling Services Using WCF Client Channels</span></span>  
 <span data-ttu-id="2f14e-193">WCF クライアント型を拡張する<xref:System.ServiceModel.ClientBase%601>から派生自体<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>基になるチャネル システムを公開するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2f14e-193">WCF client types extend <xref:System.ServiceModel.ClientBase%601>, which itself derives from <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface to expose the underlying channel system.</span></span> <span data-ttu-id="2f14e-194">ターゲットのサービス コントラクトと <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> クラスを使用して、サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2f14e-194">You can invoke services by using the target service contract with the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2f14e-195">詳細については、「 [WCF クライアント アーキテクチャ](../../../docs/framework/wcf/feature-details/client-architecture.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f14e-195">For details, see [WCF Client Architecture](../../../docs/framework/wcf/feature-details/client-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f14e-196">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f14e-196">See Also</span></span>  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
