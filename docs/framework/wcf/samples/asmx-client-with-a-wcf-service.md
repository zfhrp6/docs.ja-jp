---
title: WCF サービス付き ASMX クライアント
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 93a881e486d82183fc42c524f3d83527c649516d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805130"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="22910-102">WCF サービス付き ASMX クライアント</span><span class="sxs-lookup"><span data-stu-id="22910-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="22910-103">このサンプルでは、Windows Communication Foundation (WCF) を使用してサービスを作成し、ASMX クライアントなど、WCF 以外のクライアントからサービスにアクセスする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="22910-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22910-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22910-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="22910-105">このサンプルは、クライアント コンソール プログラム (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll) で構成されています。</span><span class="sxs-lookup"><span data-stu-id="22910-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="22910-106">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="22910-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="22910-107">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (`Add`、`Subtract`、`Multiply`、`Divide`) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="22910-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="22910-108">ASMX クライアントは算術演算を同期要求し、サービスは結果を添えて応答します。</span><span class="sxs-lookup"><span data-stu-id="22910-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="22910-109">サービスは、次に示すコードで定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="22910-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
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
  
 <span data-ttu-id="22910-110"><xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Xml.Serialization.XmlSerializer> は、CLR 型を XML 表現にマップします。</span><span class="sxs-lookup"><span data-stu-id="22910-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="22910-111"><xref:System.Runtime.Serialization.DataContractSerializer> は一部の XML 表現を、XmlSerializer とは異なる方法で解釈します。</span><span class="sxs-lookup"><span data-stu-id="22910-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="22910-112">Wsdl.exe などの非 WCF プロキシ ジェネレーターは、XmlSerializer を使用しているときより使いやすいインターフェイスを生成します。</span><span class="sxs-lookup"><span data-stu-id="22910-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="22910-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute>に適用される、`ICalculator`インターフェイスを XML に CLR 型のマッピングに対して XmlSerializer を使用することを確認します。</span><span class="sxs-lookup"><span data-stu-id="22910-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="22910-114">このサービス実装は、計算を行い、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="22910-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="22910-115">サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル (Web.config) で定義します。</span><span class="sxs-lookup"><span data-stu-id="22910-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="22910-116">エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。</span><span class="sxs-lookup"><span data-stu-id="22910-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="22910-117">サービスは、インターネット インフォメーション サービス (IIS) ホストから提供されるベース アドレスで、エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="22910-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="22910-118">`binding` 属性は basicHttpBinding に設定されます。これにより、WS-I Basic Profile 1.1 に準拠した SOAP 1.1 を使用する HTTP 通信を実現します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22910-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="22910-119">ASMX クライアントは、Web サービス記述言語 (WSDL) ユーティリティ (Wsdl.exe) によって生成される型指定されたプロキシを使用して WCF サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="22910-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="22910-120">型指定のあるプロキシは、ファイル generatedClient.cs に含まれています。</span><span class="sxs-lookup"><span data-stu-id="22910-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="22910-121">WSDL ユーティリティは、指定されたサービスが使用するメタデータを取得し、クライアントが通信に使用する型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="22910-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="22910-122">既定では、フレームワークはメタデータを公開しません。</span><span class="sxs-lookup"><span data-stu-id="22910-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="22910-123">プロキシを生成するために必要なメタデータを公開するを追加する必要があります、 [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)設定とその`httpGetEnabled`属性を`True`次の構成で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="22910-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="22910-124">次のコマンドをクライアント ディレクトリでコマンド プロンプトから実行して、型指定のあるプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="22910-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="22910-125">生成された型指定のあるプロキシを使用することにより、クライアントは適切なアドレスを構成して、指定のサービス エンドポイントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="22910-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="22910-126">クライアントは構成ファイル (App.config) を使用して、通信するエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="22910-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="22910-127">クライアント実装は型指定のあるプロキシのインスタンスを構築し、サービスとの通信を開始します。</span><span class="sxs-lookup"><span data-stu-id="22910-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
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
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="22910-128">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="22910-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="22910-129">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="22910-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22910-130">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="22910-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="22910-131">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="22910-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="22910-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="22910-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="22910-133">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="22910-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22910-134">詳細については、渡すと、複雑なデータを返す型を参照してください: [Windows フォーム クライアントでのデータ バインディング](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md)、 [Windows Presentation Foundation クライアントでのデータ バインディング](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)、および[データASP.NET クライアントでバインディング](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="22910-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22910-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="22910-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="22910-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="22910-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="22910-137">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="22910-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22910-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="22910-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="22910-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="22910-139">See Also</span></span>
