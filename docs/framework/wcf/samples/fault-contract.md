---
title: "エラー コントラクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf0f615ae338d9ad52cc8c40096e7130fb111ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="fault-contract"></a><span data-ttu-id="f97e6-102">エラー コントラクト</span><span class="sxs-lookup"><span data-stu-id="f97e6-102">Fault Contract</span></span>
<span data-ttu-id="f97e6-103">エラー コントラクトのサンプルでは、エラー情報をサービスからクライアントに通信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f97e6-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="f97e6-104">サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に追加のコードは内部例外をエラーに変換するサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="f97e6-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="f97e6-105">クライアントは 0 による除算を試行し、サービスを強制的にエラー状態にします。</span><span class="sxs-lookup"><span data-stu-id="f97e6-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f97e6-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f97e6-107">電卓コントラクトは、<xref:System.ServiceModel.FaultContractAttribute> が含まれるように変更されています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="f97e6-108"><xref:System.ServiceModel.FaultContractAttribute> 属性は、`Divide` 操作が型 `MathFault` のエラーを返すことができることを示します。</span><span class="sxs-lookup"><span data-stu-id="f97e6-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="f97e6-109">シリアル化可能な任意の型のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f97e6-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="f97e6-110">この場合、`MathFault` は次のようなデータ コントラクトになります。</span><span class="sxs-lookup"><span data-stu-id="f97e6-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="f97e6-111">0 による除算の例外が発生すると、`Divide` メソッドは <xref:System.ServiceModel.FaultException%601> 例外をスローします。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="f97e6-112">この例外により、クライアントにエラーが送信されます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-112">This exception results in a fault being sent to the client.</span></span>  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="f97e6-113">クライアント コードは、0 による除算を要求することで強制的にエラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="f97e6-114">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f97e6-115">0 による除算がエラーとして報告されたことが示されます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="f97e6-116">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="f97e6-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f97e6-117">クライアントでこれを行うには、適切な `FaultException<MathFault>` 例外を次のようにキャッチします。</span><span class="sxs-lookup"><span data-stu-id="f97e6-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="f97e6-118">既定では、サービス実装の詳細がサービスのセキュリティの境界から漏えいするのを回避するため、予期しない例外の詳細はクライアントに送信されません。</span><span class="sxs-lookup"><span data-stu-id="f97e6-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="f97e6-119">`FaultContract` では、コントラクトでエラーを説明し、例外の特定の型がクライアントへの転送に適しているとマークできます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="f97e6-120">`FaultException<T>` には、エラーをコンシューマーに送信するためのランタイム機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f97e6-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="f97e6-121">ただし、デバッグ時にはサービス エラーの内部詳細を確認することが役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="f97e6-122">前に説明したセキュリティ動作を無効にするには、サーバーで未処理のすべての例外の詳細を、クライアントに送信するエラーに含めるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="f97e6-123">これは、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> を `true` に設定することによって行います。</span><span class="sxs-lookup"><span data-stu-id="f97e6-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="f97e6-124">次の例に示すように、コードまたは構成のどちらを使用しても設定できます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f97e6-125">さらに、動作する必要があります、サービスに関連付けを設定して、 `behaviorConfiguration` "CalculatorServiceBehavior"に構成ファイル内のサービスの属性です。</span><span class="sxs-lookup"><span data-stu-id="f97e6-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="f97e6-126">こうしたエラーをクライアントでキャッチするには、非ジェネリックの <xref:System.ServiceModel.FaultException> をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f97e6-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="f97e6-127">この動作はデバッグ目的でのみ使用し、製品版では有効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f97e6-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f97e6-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f97e6-129">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="f97e6-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f97e6-130">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f97e6-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f97e6-131">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="f97e6-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f97e6-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f97e6-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f97e6-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f97e6-134">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f97e6-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f97e6-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f97e6-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="f97e6-136">参照</span><span class="sxs-lookup"><span data-stu-id="f97e6-136">See Also</span></span>
