---
title: "方法 : 双方向コントラクトを使用してサービスにアクセスする"
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
helpviewer_keywords: duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4c273e674fb7cb0f2801d9858d598baab5973a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="178e8-102">方法 : 双方向コントラクトを使用してサービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="178e8-102">How to: Access Services with a Duplex Contract</span></span>
<span data-ttu-id="178e8-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能の 1 つに、双方向のメッセージング パターンを使用するサービスを作成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="178e8-103">One feature of [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="178e8-104">双方向のメッセージング パターンを使用するサービスは、コールバックを通じてクライアントと通信できます。</span><span class="sxs-lookup"><span data-stu-id="178e8-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="178e8-105">ここでは、コールバック インターフェイスを実装するクライアント クラス内に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="178e8-105">This topic shows the steps to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client in a client class that implements the callback interface.</span></span>  
  
 <span data-ttu-id="178e8-106">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="178e8-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="178e8-107">クライアントは、セキュリティを使用して信頼するサービスだけに接続できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="178e8-107">The client should use security to ensure that it connects only to services it trusts.</span></span>  
  
 <span data-ttu-id="178e8-108">基本的な作成に関するチュートリアルについては[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスとクライアントを参照してください[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)です。</span><span class="sxs-lookup"><span data-stu-id="178e8-108">For a tutorial on creating a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and client, see [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
### <a name="to-access-a-duplex-service"></a><span data-ttu-id="178e8-109">双方向サービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="178e8-109">To access a duplex service</span></span>  
  
1.  <span data-ttu-id="178e8-110">2 つのインターフェイスを含むサービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="178e8-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="178e8-111">1 つ目のインターフェイスはサービスに使用し、2 つ目のインターフェイスはコールバックに使用します。</span><span class="sxs-lookup"><span data-stu-id="178e8-111">The first interface is for the service, the second is for the callback.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="178e8-112">双方向サービスを作成するを参照してください[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="178e8-112"> creating a duplex service, see [How to: Create a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
2.  <span data-ttu-id="178e8-113">サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="178e8-113">Run the service.</span></span>  
  
3.  <span data-ttu-id="178e8-114">使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)クライアントのコントラクト (インターフェイス) を生成します。</span><span class="sxs-lookup"><span data-stu-id="178e8-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="178e8-115">これを行う方法については、次を参照してください。[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="178e8-115">For information about how to do this, see  [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
4.  <span data-ttu-id="178e8-116">次の例に示すように、クライアント クラスにコールバック インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="178e8-116">Implement the callback interface in the client class, as shown in the following example.</span></span>  
  
    ```csharp  
    public class CallbackHandler : ICalculatorDuplexCallback  
    {  
        public void Result(double result)  
        {  
            Console.WriteLine("Result ({0})", result);  
        }  
        public void Equation(string equation)  
        {  
            Console.WriteLine("Equation({0})", equation);  
        }  
    }  
    ```  
  
    ```vb  
    Public Class CallbackHandler   
    Implements ICalculatorDuplexCallback  
       Public Sub Result (ByVal result As Double)  
          Console.WriteLine("Result ({0})", result)  
       End Sub  
        Public Sub Equation(ByVal equation As String)  
            Console.Writeline("Equation({0})", equation)  
        End Sub  
    End Class  
    ```  
  
5.  <span data-ttu-id="178e8-117"><xref:System.ServiceModel.InstanceContext> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="178e8-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="178e8-118">コンストラクターには、クライアント クラスのインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="178e8-118">The constructor requires an instance of the client class.</span></span>  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <span data-ttu-id="178e8-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクトを必要とするコンストラクターを使用して、<xref:System.ServiceModel.InstanceContext> クライアントのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="178e8-119">Create an instance of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="178e8-120">コンストラクターの 2 番目のパラメーターは、構成ファイルに含まれるエンドポイントの名前です。</span><span class="sxs-lookup"><span data-stu-id="178e8-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  <span data-ttu-id="178e8-121">必要に応じて、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="178e8-121">Call the methods of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="178e8-122">例</span><span class="sxs-lookup"><span data-stu-id="178e8-122">Example</span></span>  
 <span data-ttu-id="178e8-123">双方向コントラクトにアクセスするクライアント クラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="178e8-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="178e8-124">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="178e8-124">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178e8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="178e8-125">See Also</span></span>  
 [<span data-ttu-id="178e8-126">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="178e8-126">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="178e8-127">方法: 双方向コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="178e8-127">How to: Create a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="178e8-128">ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="178e8-128">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="178e8-129">方法: クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="178e8-129">How to: Create a Client</span></span>](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="178e8-130">方法: ChannelFactory を使用</span><span class="sxs-lookup"><span data-stu-id="178e8-130">How to: Use the ChannelFactory</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
