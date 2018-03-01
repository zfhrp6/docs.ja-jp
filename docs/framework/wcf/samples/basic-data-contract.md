---
title: "基本的なデータ コントラクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Contract
ms.assetid: b124e9e0-cb73-4ae0-b9c3-e6cdf5eced98
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8beb306321c5cf334951d54dd8da80892005c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="basic-data-contract"></a><span data-ttu-id="186b1-102">基本的なデータ コントラクト</span><span class="sxs-lookup"><span data-stu-id="186b1-102">Basic Data Contract</span></span>
<span data-ttu-id="186b1-103">このサンプルでは、データ コントラクトを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="186b1-103">This sample demonstrates how to implement a data contract.</span></span> <span data-ttu-id="186b1-104">データ コントラクトを使用すると、サービスと構造化データをやり取りできます。</span><span class="sxs-lookup"><span data-stu-id="186b1-104">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="186b1-105">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)しますが、基本的な数値型ではなく複素数を使用します。</span><span class="sxs-lookup"><span data-stu-id="186b1-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) but uses complex numbers instead of basic numeric types.</span></span>  
  
 <span data-ttu-id="186b1-106">この例では、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="186b1-106">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="186b1-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="186b1-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="186b1-108">このサービスのサービス コントラクトでは複素数を使用します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="186b1-108">The service contract for this service uses complex numbers, as shown in the following sample code.</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="186b1-109"><xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性は `ComplexNumber` クラスの定義に適用され、クラスのどのフィールドがクライアントとサービス間のネットワーク経由で渡されるかを示します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="186b1-109">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes have been applied to the definition of the `ComplexNumber` class to indicate which fields of the class can be passed over the wire between the client and the service, as shown in the following sample code.</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class ComplexNumber  
{  
    [DataMember]  
    public double Real = 0.0D;  
    [DataMember]  
    public double Imaginary = 0.0D;  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
 <span data-ttu-id="186b1-110">サービス実装は計算を行い、結果を返します。つまり、`ComplexNumber` 型の数値を受け入れて返します。</span><span class="sxs-lookup"><span data-stu-id="186b1-110">The service implementation calculates and returns the appropriate result, accepting and returning numbers of the `ComplexNumber` type.</span></span>  
  
```  
// This is the service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
  
    public ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real - n2.Real, n1.Imaginary -   
                                                     n2.Imaginary);  
    }  
    public ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2)  
    {  
        double real1 = n1.Real * n2.Real;  
        double imaginary1 = n1.Real * n2.Imaginary;  
        double imaginary2 = n2.Real * n1.Imaginary;  
        double real2 = n1.Imaginary * n2.Imaginary * -1;  
        return new ComplexNumber(real1 + real2, imaginary1 +   
                                                 imaginary2);  
    }  
  
    public ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2)  
    {  
         ComplexNumber conjugate =   
              new ComplexNumber(n2.Real, -1*n2.Imaginary);  
         ComplexNumber numerator = Multiply(n1, conjugate);  
         ComplexNumber denominator = Multiply(n2, conjugate);  
         return new ComplexNumber(numerator.Real / denominator.Real,  
                                               numerator.Imaginary);  
    }  
}  
```  
  
 <span data-ttu-id="186b1-111">クライアント実装でも複素数を使用します。</span><span class="sxs-lookup"><span data-stu-id="186b1-111">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="186b1-112">サービス コントラクトとデータ コントラクトの両方がによって生成されるソース ファイル generatedClient.cs で定義されている、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータからです。</span><span class="sxs-lookup"><span data-stu-id="186b1-112">Both the service contract and the data contract are defined in the source file generatedClient.cs, which is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span>  
  
```  
// Create a client.  
DataContractCalculatorClient client = new DataContractCalculatorClient();  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();   
value1.Real = 1;   
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();   
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = proxy.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
      value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,   
      result.Real, result.Imaginary);   
    …  
}  
```  
  
 <span data-ttu-id="186b1-113">このサンプルを実行する場合は、操作の要求や応答はクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="186b1-113">When you run the sample, the requests and responses of the operation are displayed in the client console window.</span></span> <span data-ttu-id="186b1-114">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="186b1-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 41i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="186b1-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="186b1-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="186b1-116">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="186b1-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="186b1-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="186b1-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="186b1-118">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="186b1-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="186b1-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="186b1-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="186b1-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="186b1-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="186b1-121">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="186b1-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="186b1-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="186b1-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\Basic`  
  
## <a name="see-also"></a><span data-ttu-id="186b1-123">参照</span><span class="sxs-lookup"><span data-stu-id="186b1-123">See Also</span></span>
