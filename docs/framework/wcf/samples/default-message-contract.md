---
title: "既定のメッセージ コントラクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 407fa758c6564c3b7a5a8573acef1b6e181399d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="default-message-contract"></a><span data-ttu-id="7de6e-102">既定のメッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="7de6e-102">Default Message Contract</span></span>
<span data-ttu-id="7de6e-103">既定のメッセージ コントラクトのサンプルでは、ユーザー定義のカスタム メッセージをサービス操作に渡したり、サービス操作から渡されたりするサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="7de6e-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="7de6e-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に型指定されたサービスとしての電卓インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="7de6e-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="7de6e-105">加算、減算、乗算、および除算に使用するための個々 のサービス操作ではなく、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)、このサンプルには、オペランドと演算子の両方を格納して返すカスタム メッセージが渡されます。算術演算の結果の結果。</span><span class="sxs-lookup"><span data-stu-id="7de6e-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="7de6e-106">クライアントはコンソール プログラム (.exe) であり、サービス ライブラリはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7de6e-107">クライアント アクティビティは、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7de6e-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de6e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7de6e-109">このサービスでは、型 `MyMessage` のカスタム メッセージを受け入れて返す、1 つのサービス操作が定義されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="7de6e-110">このサンプルでは要求および応答のメッセージの型は同じですが、もちろん、メッセージ コントラクトは必要に応じて変えることができます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="7de6e-111">カスタム メッセージ `MyMessage` は、<xref:System.ServiceModel.MessageContractAttribute>、<xref:System.ServiceModel.MessageHeaderAttribute>、および <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性が付いたクラスで定義されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="7de6e-112">このサンプルで使用するのは 3 番目のコンストラクタだけです。</span><span class="sxs-lookup"><span data-stu-id="7de6e-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="7de6e-113">メッセージ コントラクトを使用すると、SOAP メッセージを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="7de6e-114">このサンプルでは、<xref:System.ServiceModel.MessageHeaderAttribute> 属性を使用して SOAP ヘッダーに `Operation` を格納します。</span><span class="sxs-lookup"><span data-stu-id="7de6e-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="7de6e-115">オペランド `N1`、`N2`、および `Result` は SOAP 本文内に示されます。これらのオペランドには <xref:System.ServiceModel.MessageBodyMemberAttribute> 属性が適用されているためです。</span><span class="sxs-lookup"><span data-stu-id="7de6e-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```  
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="7de6e-116">実装クラスには、`Calculate` サービス処理用のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7de6e-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="7de6e-117">`CalculateService` クラスは、オペランドと演算子を要求メッセージから取得し、要求された計算結果が含まれる応答メッセージを作成します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7de6e-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```  
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="7de6e-118">クライアントの生成されたクライアント コードで作成された、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールです。</span><span class="sxs-lookup"><span data-stu-id="7de6e-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="7de6e-119">このツールでは、必要に応じて、生成済みのクライアント コード内にメッセージ コントラクト型が自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="7de6e-120">`/messageContract` コマンド オプションを指定すると、メッセージ コントラクトを強制的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="7de6e-121">`MyMessage` メッセージを使用するクライアントを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="7de6e-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="7de6e-122">サンプルを実行すると、クライアント コンソール ウィンドウに計算が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="7de6e-123">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7de6e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7de6e-124">この時点で、ユーザー定義のカスタム メッセージがクライアントとサービスの操作間で渡されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="7de6e-125">メッセージ コントラクトでは、オペランドと結果はメッセージ本文内にあり、演算子はメッセージ ヘッダー内にあることが定義されました。</span><span class="sxs-lookup"><span data-stu-id="7de6e-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="7de6e-126">このメッセージ構造を監視するために、メッセージ ログ記録を設定できます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7de6e-127">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7de6e-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7de6e-128">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7de6e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7de6e-129">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7de6e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7de6e-130">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7de6e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7de6e-131">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7de6e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7de6e-132">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7de6e-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7de6e-133">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7de6e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7de6e-134">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7de6e-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a><span data-ttu-id="7de6e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7de6e-135">See Also</span></span>
