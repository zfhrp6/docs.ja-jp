---
title: '方法 : Windows Communication Foundation クライアントを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 6667a8e9862054d7d8d5b20e70dfbe699de02eab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>方法 : Windows Communication Foundation クライアントを使用する
これは、基本的な Windows Communication Foundation (WCF) アプリケーションを作成するために必要な 6 つのタスクの最後のタスクです。 タスクの 6 つのすべての概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。  
  
 Windows Communication Foundation (WCF) プロキシを作成して、構成、クライアント インスタンスを作成すると、クライアント アプリケーションのコンパイルし通信するために使用されることができます、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]サービス。 このトピックでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントをインスタンス化し、使用する手順について説明します。 この手順は、次の 3 つの手順で構成されます。  
  
1.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントをインスタンス化します。  
  
2.  生成されたプロキシからサービス操作を呼び出します。  
  
3.  操作の呼び出しが完了したらクライアントを閉じます。  
  
### <a name="to-use-a-windows-communication-foundation-client"></a>Windows Communication Foundation クライアントを使用するには  
  
1.  GettingStartedClient プロジェクトの Program.cs ファイルまたは Program.vb ファイルを開き、既存のコードを次のコードで置き換えます。  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
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
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     GettingStartedClient.ServiceReference1 をインポートする using または imports ステートメントに注意してください。 これによって、Visual Studio の "サービス参照の追加" によって生成されたコードがインポートされます。 そのコードは WCF プロキシをインスタンス化してから、電卓サービスによって公開されている各サービス操作を呼び出し、プロキシを閉じて終了します。  
  
 これで、チュートリアルは終了です。 サービス コントラクトの定義、サービス コントラクトの実装、WCF プロキシの生成、WCF クライアント アプリケーションの構成、そしてプロキシの使用によるサービス操作の呼び出しを行いました。 アプリケーションをテストするには、まず GettingStartedHost を実行してサービスを開始し、次に GettingStartedClient を実行します。 GettingStartedHost からの出力は、次のようになります。  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 GettingStartedClient からの出力は、次のようになります。  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a>関連項目  
 [クライアントを構築する](../../../docs/framework/wcf/building-clients.md)  
 [方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [方法 : 双方向コントラクトを作成する](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [方法 : 双方向コントラクトを使用してサービスにアクセスする](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
