---
title: "プログラムを使用して探索可能性に WCF サービスとクライアントを追加する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# プログラムを使用して探索可能性に WCF サービスとクライアントを追加する方法
このトピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを探索可能にする方法について説明します。 基にして、[自己ホスト](http://go.microsoft.com/fwlink/?LinkId=145523)サンプルです。  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>既存の自己ホスト サービス サンプルを探索用に構成するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] で自己ホスト ソリューションを開きます。 このサンプルは、TechnologySamples\Basic\Service\Hosting\SelfHost ディレクトリにあります。  
  
2.  `System.ServiceModel.Discovery.dll` への参照をサービス プロジェクトに追加します。 "System. ServiceModel.Discovery.dll またはその依存関係の&1; つの以降のバージョンが必要です、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]プロジェクト... に指定されているよりも" ソリューション エクスプ ローラーでプロジェクトを右クリックして、このメッセージを表示する場合は**プロパティ**します。 **プロジェクトのプロパティ**ウィンドウことを確認して、**ターゲット フレームワーク**は[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]です。  
  
3.  Service.cs ファイルを開き、次の `using` ステートメントを追加します。  
  
    ```  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  `Main()`メソッド内で、`using`ステートメントを追加、 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>をサービス ホストのインスタンス。  
  
    ```  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
  
            // ...  
        }  
    }  
    ```  
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>に適用されたサービスが探索可能なことを指定します。  
  
5.  追加、 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 、サービス ホストを追加するコードの直後後に、 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>します。  
  
    ```  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     このコードは、探索メッセージを標準の UDP 探索エンドポイントに送信する必要があることを指定します。  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>探索を使用してサービスを呼び出すクライアント アプリケーションを作成するには  
  
1.  新しいコンソール アプリケーションを `DiscoveryClientApp` というソリューションに追加します。  
  
2.  `System.ServiceModel.dll` および `System.ServiceModel.Discovery.dll` への参照を追加します。  
  
3.  GeneratedClient.cs ファイルおよび App.config ファイルを、既存のクライアント プロジェクトから新しい DiscoveryClientApp プロジェクトに追加します。 これを行うには、内のファイルを右クリックし、**ソリューション エクスプ ローラー**を選択**コピー**、クリックして、 **DiscoveryClientApp**プロジェクトを右クリックして選択**貼り付け**します。  
  
4.  Program.cs を開きます。  
  
5.  次の `using` ステートメントを追加します。  
  
    ```  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
  
    ```  
  
6.  `FindCalculatorServiceAddress()` という静的メソッドを `Program` クラスに追加します。  
  
    ```  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     このメソッドは、探索を使用して `CalculatorService` サービスを検索します。  
  
7.  内部、`FindCalculatorServiceAddress`メソッドを新規作成<xref:System.ServiceModel.Discovery.DiscoveryClient>を渡して、インスタンス、 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>コンス トラクターにします。  
  
    ```  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     これにより[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を<xref:System.ServiceModel.Discovery.DiscoveryClient>クラスは、標準の UDP 探索エンドポイントを使用して探索メッセージを送受信する必要があります。  
  
8.  次の行で、<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>メソッドを指定し、 <xref:System.ServiceModel.Discovery.FindCriteria>を検索する対象のサービス コントラクトを格納しているインスタンス。 ここでは、`ICalculator` を指定します。  
  
    ```  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. 呼び出しの後に<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>、少なくとも&1; つの一致するサービスがないかどうかを確認し、返す、 <xref:System.ServiceModel.EndpointAddress>最初に一致するサービスのです。 一致するサービスがない場合は `null` を返します。  
  
    ```  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. `InvokeCalculatorService` という名前の静的メソッドを `Program` クラスに追加します。  
  
    ```  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     このメソッドは、`FindCalculatorServiceAddress` から返されたエンドポイント アドレスを使用して、電卓サービスを呼び出します。  
  
11. `InvokeCalculatorService` メソッド内で、`CalculatorServiceClient` クラスのインスタンスを作成します。 このクラスは、[自己ホスト](http://go.microsoft.com/fwlink/?LinkId=145523)サンプルです。 これは、Svcutil.exe を使用して生成されました。  
  
    ```  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. 次の行では、クライアントのエンドポイント アドレスを、`FindCalculatorServiceAddress()` から返されたエンドポイント アドレスに設定します。  
  
    ```  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. 前の手順のコードの直後に、電卓サービスで公開されたメソッドを呼び出します。  
  
    ```  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. `Main()` クラスの `Program` メソッドにコードを追加して、`FindCalculatorServiceAddress` を呼び出します。  
  
    ```  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. 次の行では、`InvokeCalculatorService()` を呼び出し、`FindCalculatorServiceAddress()` から返されたエンドポイント アドレスを渡します。  
  
    ```  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  権限のレベルが高いコマンド プロンプトを開き、Service.exe を実行します。  
  
2.  コマンド プロンプトを開き、Discoveryclientapp.exe を実行します。  
  
3.  Service.exe からの出力は次のようになります。  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  Discoveryclientapp.exe からの出力は次のようになります。  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>例  
 このサンプルで使用されているコード全体の一覧を次に示します。 このコードに基づいているため、[自己ホスト](http://go.microsoft.com/fwlink/?LinkId=145523)サンプルを変更されているファイルのみが一覧表示します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]自己ホスト サンプルを参照してください[のセットアップ手順](http://go.microsoft.com/fwlink/?LinkId=145522)します。  
  
```  
  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints              
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  
  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## <a name="see-also"></a>関連項目  
 [WCF Discovery の概要](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)   
 [WCF Discovery オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)