---
title: "方法 : Windows Communication Foundation サービス コントラクトを実装する"
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
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bf590b2f508cc6661b5acb045a7d66b38ed169c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="074ba-102">方法 : Windows Communication Foundation サービス コントラクトを実装する</span><span class="sxs-lookup"><span data-stu-id="074ba-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="074ba-103">これは、基本的な [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスとそのサービスを呼び出すことができるクライアントの作成に必要な 6 つのタスクのうち、2 番目のタスクです。</span><span class="sxs-lookup"><span data-stu-id="074ba-103">This is the second of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service and a client that can call the service.</span></span> <span data-ttu-id="074ba-104">6 つのすべてのタスクの概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="074ba-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="074ba-105">WCF アプリケーションの作成における次の手順では、サービス インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="074ba-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="074ba-106">これには、ユーザー定義の `CalculatorService` インターフェイスを実装する `ICalculator` というクラスの作成も含まれます。</span><span class="sxs-lookup"><span data-stu-id="074ba-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>  
  
### <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="074ba-107">WCF サービス コントラクトを実装するには</span><span class="sxs-lookup"><span data-stu-id="074ba-107">To implement a WCF service contract</span></span>  
  
1.  <span data-ttu-id="074ba-108">Service1.cs ファイルまたは Service1.vb ファイルを開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="074ba-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>  
  
    ```csharp  
    //Service1.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
        public class CalculatorService : ICalculator  
        {  
            public double Add(double n1, double n2)  
            {  
                double result = n1 + n2;  
                Console.WriteLine("Received Add({0},{1})", n1, n2);  
                // Code added to write output to the console window.  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Subtract(double n1, double n2)  
            {  
                double result = n1 - n2;  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Multiply(double n1, double n2)  
            {  
                double result = n1 * n2;  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
  
            public double Divide(double n1, double n2)  
            {  
                double result = n1 / n2;  
                Console.WriteLine("Received Divide({0},{1})", n1, n2);  
                Console.WriteLine("Return: {0}", result);  
                return result;  
            }  
        }  
    }  
    ```  
  
    ```vb
    ‘Service1.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        Public Class CalculatorService  
            Implements ICalculator  
  
            Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
                Dim result As Double = n1 + n2  
                ' Code added to write output to the console window.  
                Console.WriteLine("Received Add({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
            End Function  
  
            Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
                Dim result As Double = n1 - n2  
                Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
  
            Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
                Dim result As Double = n1 * n2  
                Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
  
            Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
                Dim result As Double = n1 / n2  
                Console.WriteLine("Received Divide({0},{1})", n1, n2)  
                Console.WriteLine("Return: {0}", result)  
                Return result  
  
            End Function  
        End Class  
    End Namespace  
    ```  
  
     <span data-ttu-id="074ba-109">各メソッドは、電卓操作を実装し、テストしやすいように、いくつかのテキストをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="074ba-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="074ba-110">例</span><span class="sxs-lookup"><span data-stu-id="074ba-110">Example</span></span>  
 <span data-ttu-id="074ba-111">コントラクトを定義するインターフェイスのコードとそのインターフェイスを実装するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="074ba-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
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
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```vb
‘IService.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
 <span data-ttu-id="074ba-112">サービス コントラクトが作成されて実装されます。</span><span class="sxs-lookup"><span data-stu-id="074ba-112">Now the service contract is created and implemented.</span></span> <span data-ttu-id="074ba-113">コンパイル エラーがないことを確認するようにソリューションをビルドおよびに進みます[する方法: ホストおよび基本的なサービスを実行](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="074ba-113">Build the solution to ensure there are no compilation errors and then proceed to [How to: Host and Run a Basic Service](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) to run the service.</span></span> <span data-ttu-id="074ba-114">情報をトラブルシューティングするには、次を参照してください。[チュートリアル入門のトラブルシューティング](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="074ba-114">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="074ba-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="074ba-115">Compiling the Code</span></span>  
 <span data-ttu-id="074ba-116">Visual Studio を使用している場合、ビルド メニュー ソリューションのビルド をクリックして (または CTRL + SHIFT + B キーを押します)。</span><span class="sxs-lookup"><span data-stu-id="074ba-116">If you are using Visual Studio, on the Build menu click Build Solution (or press CTRL+SHIFT+B).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074ba-117">参照</span><span class="sxs-lookup"><span data-stu-id="074ba-117">See Also</span></span>  
 [<span data-ttu-id="074ba-118">はじめに</span><span class="sxs-lookup"><span data-stu-id="074ba-118">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="074ba-119">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="074ba-119">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
