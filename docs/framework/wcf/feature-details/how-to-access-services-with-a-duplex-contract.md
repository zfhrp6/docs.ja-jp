---
title: '方法: 双方向コントラクトでサービスへのアクセス'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: 6675da079b343b1b80477c65260ee8a1f44df72a
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027903"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a>方法: 双方向コントラクトでサービスへのアクセス

Windows Communication Foundation (WCF) の 1 つの機能は、双方向のメッセージング パターンを使用してサービスを作成する機能です。 双方向のメッセージング パターンを使用するサービスは、コールバックを通じてクライアントと通信できます。 このトピックでは、コールバック インターフェイスを実装するクライアント クラスで、WCF クライアントを作成する手順を示します。

二重バインディングでは、クライアントの IP アドレスをサービスに公開します。 クライアントは、セキュリティを使用して信頼するサービスだけに接続できるようにする必要があります。

基本的な WCF サービスとクライアントを作成する方法のチュートリアルを参照してください。[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)です。

## <a name="to-access-a-duplex-service"></a>双方向サービスにアクセスするには

1. 2 つのインターフェイスを含むサービスを作成します。 1 つ目のインターフェイスはサービスに使用し、2 つ目のインターフェイスはコールバックに使用します。 双方向サービスの作成の詳細については、次を参照してください。[する方法: 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。

2. サービスを実行します。

3. 使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)クライアントのコントラクト (インターフェイス) を生成します。 これを行う方法については、次を参照してください。[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。

4. 次の例に示すように、クライアント クラスにコールバック インターフェイスを実装します。

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

5. <xref:System.ServiceModel.InstanceContext> クラスのインスタンスを作成します。 コンストラクターには、クライアント クラスのインスタンスが必要です。

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. 必要とするコンス トラクターを使用して WCF クライアントのインスタンスを作成、<xref:System.ServiceModel.InstanceContext>オブジェクト。 コンストラクターの 2 番目のパラメーターは、構成ファイルに含まれるエンドポイントの名前です。

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. 必要に応じて、WCF クライアントのメソッドを呼び出します。

## <a name="example"></a>例

双方向コントラクトにアクセスするクライアント クラスを作成する方法を次のコード例に示します。

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a>関連項目

[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)  
[方法 : 双方向コントラクトを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
[方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
[方法 : ChannelFactory を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
