---
title: "入門サンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f97ad418f3d5ed197e8c35edf9e897eb393ef18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-sample"></a><span data-ttu-id="c1cde-102">入門サンプル</span><span class="sxs-lookup"><span data-stu-id="c1cde-102">Getting Started Sample</span></span>
<span data-ttu-id="c1cde-103">この入門サンプルでは、一般的なサービスと一般的なクライアントを、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="c1cde-104">このサンプルは、他のすべての基本的な技術サンプルの基礎になります。</span><span class="sxs-lookup"><span data-stu-id="c1cde-104">This sample is the basis for all other basic technology samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1cde-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1cde-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c1cde-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c1cde-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c1cde-108">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c1cde-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 <span data-ttu-id="c1cde-110">サービスが実行する操作は、メタデータとしてパブリックに公開するサービス コントラクト内に表されています。</span><span class="sxs-lookup"><span data-stu-id="c1cde-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="c1cde-111">また、サービスにはその操作を実装するためのコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1cde-111">The service also contains the code to implement the operations.</span></span>  
  
 <span data-ttu-id="c1cde-112">クライアントには、サービス コントラクトの定義と、サービスにアクセスするためのプロキシ クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1cde-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="c1cde-113">使用してサービス メタデータからプロキシ コードを生成、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1cde-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 <span data-ttu-id="c1cde-114">[!INCLUDE[wv](../../../../includes/wv-md.md)] では、サービスは Windows アクティベーション サービス (WAS) 内でホストされます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="c1cde-115">[!INCLUDE[wxp](../../../../includes/wxp-md.md)] と [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では、インターネット インフォメーション サービス (IIS) と ASP.NET によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="c1cde-116">サービスを IIS または WAS でホストすることにより、サービスに初めてアクセスしたときにそのサービスを自動的にアクティブ化できます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1cde-117">IIS ではなく、コンソール アプリケーションでサービスをホストする場合は、サンプルを使用して作業を開始する場合を参照してください、[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c1cde-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
 <span data-ttu-id="c1cde-118">サービスとクライアントは、アクセスの詳細を構成ファイルの設定により指定します。この方法によって展開時の柔軟性が得られます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="c1cde-119">この設定には、アドレス、バインディング、およびコントラクトを指定するエンドポイント定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="c1cde-120">バインディングは、サービスへのアクセス方法を示すためのトランスポートとセキュリティの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>  
  
 <span data-ttu-id="c1cde-121">サービスは、メタデータを公開するようにランタイムの動作を構成します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-121">The service configures a run-time behavior to publish its metadata.</span></span>  
  
 <span data-ttu-id="c1cde-122">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c1cde-123">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="c1cde-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="c1cde-124">クライアントは指定された算術演算を要求し、サービスは結果と共に応答します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c1cde-125">サービスは、次に示すコードで定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>  
  
```vb  
' Define a service contract.  
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>  
     Public Interface ICalculator  
        <OperationContract()>  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
```  
  
```csharp  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
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
```  
  
 <span data-ttu-id="c1cde-126">サービス実装は計算を行い、結果を返します。次のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>  
  
```vb  
' Service class which implements the service contract.  
Public Class CalculatorService  
Implements ICalculator  
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
Return n1 + n2  
End Function  
  
Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
Return n1 - n2  
End Function  
  
Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
Return n1 * n2  
End Function  
  
Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
Return n1 / n2  
End Function  
End Class  
```  
  
```csharp  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="c1cde-127">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (Web.config) を使用して定義します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>  
  
```xaml  
<services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- ICalculator is exposed at the base address provided by  
         host: http://localhost/servicemodelsamples/service.svc.  -->  
       <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
       ...  
    </service>  
</services>  
```  
  
 <span data-ttu-id="c1cde-128">サービスは、IIS ホストまたは WAS ホストから提供されるベース アドレスで、エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="c1cde-129">バインディングの構成には、標準の <xref:System.ServiceModel.WSHttpBinding> を使用します。これは HTTP 通信と Web サービスの標準プロトコルを提供し、アドレス指定とセキュリティをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c1cde-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="c1cde-130">コントラクトは、サービスによって実装される `ICalculator` です。</span><span class="sxs-lookup"><span data-stu-id="c1cde-130">The contract is the `ICalculator` implemented by the service.</span></span>  
  
 <span data-ttu-id="c1cde-131">前の構成では、サービスと同じコンピューター上にあるクライアントは、http://localhost/servicemodelsamples/service.svc でサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-131">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="c1cde-132">リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1cde-132">For clients on remote computersto access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="c1cde-133">既定では、フレームワークはメタデータを公開しません。</span><span class="sxs-lookup"><span data-stu-id="c1cde-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="c1cde-134">そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を有効にし、Metadata Exchange (MEX) エンドポイントを http://localhost/servicemodelsamples/service.svc/mex で公開します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="c1cde-135">これを設定する構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-135">The following configuration demonstrates this.</span></span>  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
       http://localhost/servicemodelsamples/service.svc/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults  
   attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c1cde-136">によって生成されたクライアント クラスを使用して特定のコントラクト型を使用して、クライアントは通信、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1cde-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="c1cde-137">このように生成されたクライアントは、ファイル generatedClient.cs または generatedClient.vb に含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1cde-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="c1cde-138">このユーティリティは、特定のサービス用のメタデータを取得し、特定のコントラクト型を使用して通信するクライアント アプリケーションによって使用されるクライアントを生成します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="c1cde-139">クライアント コードを生成するには、ホストされるサービスを利用できる必要があります。このサービスは、更新されたメタデータの取得に使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="c1cde-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>  
  
 <span data-ttu-id="c1cde-140">次のコマンドをクライアント ディレクトリで SDK コマンド プロンプトから実行して、型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 <span data-ttu-id="c1cde-141">Visual Basic でクライアントを生成するには、次のコマンドを SDK コマンド プロンプトから入力します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 <span data-ttu-id="c1cde-142">生成されたクライアントを使用することにより、クライアントは適切なアドレスとバインディングを構成して、指定のサービス エンドポイントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="c1cde-143">サービスと同様、クライアントは構成ファイル (App.config) を使用して、通信するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="c1cde-144">クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="c1cde-145">クライアント実装はクライアントをインスタンス化し、型指定のあるインターフェイスを使用してサービスとの通信を開始します。次のコード例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1cde-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>  
  
```vb  
' Create a client  
Dim client As New CalculatorClient()  
  
' Call the Add service operation.  
            Dim value1 = 100.0R  
            Dim value2 = 15.99R  
            Dim result = client.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
' Call the Subtract service operation.  
value1 = 145.00R  
value2 = 76.54R  
result = client.Subtract(value1, value2)  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
' Call the Multiply service operation.  
value1 = 9.00R  
value2 = 81.25R  
result = client.Multiply(value1, value2)  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
' Call the Divide service operation.  
value1 = 22.00R  
value2 = 7.00R  
result = client.Divide(value1, value2)  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
'Closing the client gracefully closes the connection and cleans up resources  
```  
  
```csharp  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client releases all communication resources.  
client.Close();  
```  
  
 <span data-ttu-id="c1cde-146">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1cde-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c1cde-147">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-147">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c1cde-148">この入門サンプルでは、サービスとクライアントの標準的な作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c1cde-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="c1cde-149">他の[基本](../../../../docs/framework/wcf/samples/basic-sample.md)で特定の製品の機能を示すには、このサンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c1cde-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c1cde-150">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="c1cde-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c1cde-151">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1cde-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c1cde-152">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c1cde-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c1cde-153">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1cde-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cde-154">参照</span><span class="sxs-lookup"><span data-stu-id="c1cde-154">See Also</span></span>  
 [<span data-ttu-id="c1cde-155">方法: マネージ アプリケーションで WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="c1cde-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="c1cde-156">方法 : IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="c1cde-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
