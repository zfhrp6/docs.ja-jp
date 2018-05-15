---
title: 本文別のルーティング
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: e9a0c947a1dd7ac2a6c7af74baaa072aae67358c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="route-by-body"></a><span data-ttu-id="5947d-102">本文別のルーティング</span><span class="sxs-lookup"><span data-stu-id="5947d-102">Route by Body</span></span>
<span data-ttu-id="5947d-103">このサンプルでは、任意の SOAP アクションでメッセージ オブジェクトを受け入れるサービスを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5947d-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="5947d-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5947d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5947d-105">このサービスは、`Calculate` 要求パラメータを受け入れる 1 つの <xref:System.ServiceModel.Channels.Message> 操作を実装して、<xref:System.ServiceModel.Channels.Message> 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="5947d-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="5947d-106">このサンプルでは、クライアントはコンソール アプリケーション (.exe) で、サービスは IIS によってホストされています。</span><span class="sxs-lookup"><span data-stu-id="5947d-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5947d-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5947d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5947d-108">このサンプルでは、本文の内容に基づくメッセージ ディスパッチを示します。</span><span class="sxs-lookup"><span data-stu-id="5947d-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="5947d-109">組み込みの Windows Communication Foundation (WCF) サービス モデル メッセージ ディスパッチ メカニズムは、メッセージの Action に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5947d-109">The built-in Windows Communication Foundation (WCF) service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="5947d-110">ただし既存の多くの Web サービスでは、すべての操作が Action="" で定義されています。</span><span class="sxs-lookup"><span data-stu-id="5947d-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="5947d-111">アクション情報に基づいてディスパッチ要求メッセージを保持する WSDL を基準として、サービスを構築することはできません。</span><span class="sxs-lookup"><span data-stu-id="5947d-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="5947d-112">このサンプルでは、WSDL に基づくサービス コントラクトを示します (WSDL はこのサンプルに含まれる Service.wsdl 内に格納されています)。</span><span class="sxs-lookup"><span data-stu-id="5947d-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="5947d-113">サービス コントラクトはで使用されるように、電卓[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="5947d-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="5947d-114">ただし、`[OperationContract]` は、すべての操作に対して `Action=""` を指定します。</span><span class="sxs-lookup"><span data-stu-id="5947d-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="5947d-115">コントラクトが指定されている場合、サービスはカスタムのディスパッチ動作 `DispatchByBodyBehavior` に対して、複数の操作間でメッセージをディスパッチするように要求します。</span><span class="sxs-lookup"><span data-stu-id="5947d-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="5947d-116">このディスパッチ動作を初期化、`DispatchByBodyElementOperationSelector`それぞれのラッパー要素の QName をキーとした操作名のテーブルでのカスタム操作セレクター。</span><span class="sxs-lookup"><span data-stu-id="5947d-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="5947d-117">`DispatchByBodyElementOperationSelector` は本文の最初の子の開始タグを参照し、前述のテーブルを使用して操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="5947d-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="5947d-118">クライアントを使用して、サービスによってエクスポートされた WSDL から自動生成されたプロキシを使用して[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="5947d-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="5947d-119">すべての操作のアクションが空であっても、クライアント コードには影響ありません。ただし、自動生成されたプロキシ内の Action パラメータは例外です。</span><span class="sxs-lookup"><span data-stu-id="5947d-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="5947d-120">クライアント コードは、複数の計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="5947d-120">The client code performs several calculations.</span></span> <span data-ttu-id="5947d-121">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="5947d-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5947d-122">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="5947d-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5947d-123">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="5947d-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5947d-124">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="5947d-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5947d-125">指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="5947d-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5947d-126">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="5947d-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5947d-127">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5947d-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5947d-128">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5947d-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5947d-129">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="5947d-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5947d-130">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5947d-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="5947d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="5947d-131">See Also</span></span>
