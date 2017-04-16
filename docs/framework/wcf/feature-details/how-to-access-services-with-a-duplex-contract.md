---
title: "方法 : 双方向コントラクトを使用してサービスにアクセスする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "双方向コントラクト [WCF]"
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 方法 : 双方向コントラクトを使用してサービスにアクセスする
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能の 1 つに、双方向のメッセージング パターンを使用するサービスを作成する機能があります。双方向のメッセージング パターンを使用するサービスは、コールバックを通じてクライアントと通信できます。ここでは、コールバック インターフェイスを実装するクライアント クラス内に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを作成する手順を示します。  
  
 二重バインディングでは、クライアントの IP アドレスをサービスに公開します。クライアントは、セキュリティを使用して信頼するサービスだけに接続できるようにする必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の基本的なサービスとクライアントの作成方法に関するチュートリアルについては、「[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
### 双方向サービスにアクセスするには  
  
1.  2 つのインターフェイスを含むサービスを作成します。1 つ目のインターフェイスはサービスに使用し、2 つ目のインターフェイスはコールバックに使用します。双方向サービスを作成する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)」を参照してください。  
  
2.  サービスを実行します。  
  
3.  [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、クライアントのコントラクト \(インターフェイス\) を生成します。これを実行する方法については、「[方法 : クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)」を参照してください。  
  
4.  次の例に示すように、クライアント クラスにコールバック インターフェイスを実装します。  
  
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
  
5.  <xref:System.ServiceModel.InstanceContext> クラスのインスタンスを作成します。コンストラクターには、クライアント クラスのインスタンスが必要です。  
  
    ```csharp  
    InstanceContext site = new InstanceContext(new CallbackHandler());  
    ```  
  
    ```vb  
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())  
    ```  
  
6.  <xref:System.ServiceModel.InstanceContext> オブジェクトを必要とするコンストラクターを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのインスタンスを作成します。コンストラクターの 2 番目のパラメーターは、構成ファイルに含まれるエンドポイントの名前です。  
  
    ```csharp  
    CalculatorDuplexClient wcfClient =   
    new CalculatorDuplexClient(site, "default")  
    ```  
  
    ```vb  
    Dim wcfClient As New CalculatorDuplexClient(site, "default")  
    ```  
  
7.  必要に応じて、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントのメソッドを呼び出します。  
  
## 使用例  
 双方向コントラクトにアクセスするクライアント クラスを作成する方法を次のコード例に示します。  
  
 [!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
 [!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]  
  
## .NET Framework セキュリティ  
  
## 参照  
 [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)   
 [方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)   
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [方法 : クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [方法 : ChannelFactory を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)