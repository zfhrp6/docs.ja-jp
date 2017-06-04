---
title: "方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "WCF サービス [WCF]"
  - "WCF サービス [WCF], 実行"
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
caps.latest.revision: 58
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 58
---
# 方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する
これは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうち、3 番目のタスクです。6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
 このトピックでは、コンソール アプリケーションで [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスをホストする方法について説明します。この操作は、次の手順から構成されます。  
  
-   コンソール アプリケーション プロジェクトを作成し、サービスをホストします。  
  
-   サービスのサービス ホストを作成します。  
  
-   メタデータ交換を有効にします。  
  
-   サービス ホストを開きます。  
  
 このタスクで書かれるコードの全容は手順に続いて提供されている例で見ることができます。  
  
### 新しいコンソール アプリケーションを作成し、サービスをホストするには  
  
1.  新しいコンソール アプリケーション プロジェクトを作成します。入門ソリューションを右クリックし、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。**\[新しいプロジェクトの追加\]** ダイアログ ボックスの左側で、**\[C\#\]** または **\[VB\]** の **\[Windows\]** をクリックします。ダイアログ ボックスの中央のセクションで、**\[コンソール アプリケーション\]** を選択します。プロジェクトに GettingStartedHost という名前を付けます。  
  
2.  GettingStartedHost プロジェクトのターゲット フレームワークを .NET Framework 4.5 に設定します。ソリューション エクスプローラーで **\[GettingStartedHost\]** を右クリックし、**\[プロパティ\]** を選択します。**\[ターゲット フレームワーク\]** ボックスの一覧の **\[.NET Framework 4.5\]** をクリックします。VB プロジェクトのターゲット フレームワークを設定する方法は多少異なり、GettingStartedHost プロジェクトの \[プロパティ\] ダイアログ ボックスで、画面左側の **\[コンパイル\]** タブをクリックし、ダイアログ ボックスの左下隅にある **\[詳細コンパイル オプション\]** をクリックします。次に、**\[ターゲット フレームワーク\]** ボックスの一覧の **\[.NET Framework 4.5\]** をクリックします。  
  
     ターゲット フレームワークを設定すると、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] はソリューションを再読み込みします。ダイアログが表示されたら、**\[OK\]** をクリックします。  
  
3.  GettingStartedLib プロジェクトへの参照を GettingStartedHost プロジェクトに追加します。ソリューション エクスプローラーで GettingStartedHost プロジェクトの **\[参照\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックします。**\[参照の追加\]** ダイアログで、ダイアログの左側の **\[ソリューション\]** を選択します。ダイアログの中央セクションで \[GettingStartedLib\] を選択し、**\[追加\]** をクリックします。これにより、GettingStartedLib に定義されている型を GettingStartedHost プロジェクトで利用できるようになります。  
  
4.  System.ServiceModel への参照を GettingStartedHost プロジェクトに追加します。ソリューション エクスプローラーで GettingStartedHost プロジェクトの **\[参照\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックします。**\[参照の追加\]** ダイアログ ボックスの左側で、**\[フレームワーク\]** を選択します。\[アセンブリの検索\] ボックスに「`System.ServiceModel`」と入力します。ダイアログ ボックスの中央のセクションで、**\[System.ServiceModel\]** を選択し、**\[追加\]**、**\[閉じる\]** の順にクリックします。メイン メニューの \[すべて保存\] をクリックして、ソリューションを保存します。  
  
### サービスをホストするには  
  
-   Program.cs ファイルまたは Module.vb ファイルを開き、次のコードを追加します。  
  
    ```  
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
  
    ```  
  
    ```  
    ‘Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
  
    ```  
  
    1.  手順 1 \- サービスのベース アドレスを保持する Uri クラスのインスタンスを作成します。サービスは、ベース アドレスとオプションの URI を含む URL によって識別されます。ベース アドレスの書式は、\[トランスポート\]:\/\/\[コンピューター名またはドメイン\]\[:省略可能なポート \#\]\/\[省略可能な URI セグメント\] です。電卓サービスのベース アドレスは、電卓サービスのベース アドレスを使用して HTTP トランスポート、localhost、ポート 8000、および URI セグメント "GettingStarted" を使用します。  
  
    2.  手順 2 \- サービスをホストする <xref:System.ServiceModel.ServicHost> クラスのインスタンスを作成します。コンストラクターは、サービス コントラクトを実装するクラスの型と、サービスのベース アドレスの、2 つのパラメーターを受け取ります。  
  
    3.  手順 3 \- <xref:System.ServiceModel.ServiceEndpoint> インスタンスを作成します。サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。<xref:System.ServiceModel.ServiceEndpoint> コンストラクターは、サービス コントラクト インターフェイスの型、バインディング、およびアドレスを受け取ります。サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。このサンプルで使用するバインディングは、WS\-\* 仕様に準拠するエンドポイントへの接続に使用される組み込みのバインディングである <xref:System.ServiceModel.WSHttpBinding> です。WCF バインディングの詳細については、「[WCF のバインディングの概要](../../../docs/framework/wcf/bindings-overview.md)」を参照してください。エンドポイントを識別するために、ベース アドレスにアドレスが追加されます。このコードで指定されるアドレスは、"Calculator" です。したがって、エンドポイントの完全修飾アドレスは `“http://localhost:8000/GettingStartedService/Calculator”` です。  
  
        > [!IMPORTANT]
        >  サービス エンドポイントの追加は、.NET Framework 4 以降を使用する場合は省略可能です。これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。既定のエンドポイントの詳細については、「[エンドポイント アドレスの指定](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」を参照してください。既定のエンドポイント、バインディング、および動作[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[簡略化された構成](../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
    4.  手順 4 \- メタデータ交換を有効にします。クライアントは、サービス操作を呼び出すために使用されるプロキシの生成にメタデータ交換を使用します。メタデータ交換を有効化するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成し、その <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。さらに、動作を <xref:System.ServiceModel.ServiceHost> インスタンスの <xref:System.ServiceModel.ServiceHost.Behaviors%2A> コレクションに追加します。  
  
    5.  手順 5 \- 受信メッセージをリッスンするために <xref:System.ServiceModel.ServiceHost> を開きます。コードでは、ユーザーによる Enter キーの押下を待機しています。この動作を行わない場合、アプリは直ちに終了し、サービスはシャットダウンします。また、try\/catch ブロックが使用されている点にも注意してください。<xref:System.ServiceModel.ServiceHost> がインスタンス化された後、他のコードはすべて try\/catch ブロックに配置されます。<xref:System.ServiceModel.ServiceHost> によってスローされた例外を安全にキャッチする方法の詳細については、「[Using ステートメントに関する問題の回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)」を参照してください。  
  
### サービスが正常に機能していることを確認するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 内から GettingStartedHost コンソール アプリケーションを実行します。[!INCLUDE[wv](../../../includes/wv-md.md)] 以降のオペレーティング システムでは、サービスを管理者権限で実行する必要があります。[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] は管理者権限で実行されているため、GettingStartedHost も管理者権限で実行される必要があります。新しいコマンド プロンプトを管理者権限で開いて、service.exe をその中で実行することもできます。  
  
2.  Internet Explorer を開き、サービスのデバッグ ページ \(`http://localhost:8000/GettingStarted/CalculatorService`\) に移動します。  
  
## 使用例  
 次の例では、チュートリアルの前の手順で作成したサービス コントラクトと実装を含め、コンソール アプリケーションでサービスをホストします。  
  
 コマンド ライン コンパイラでこれをコンパイルするには、`System.ServiceModel.dll` を参照するクラス ライブラリに IService1.cs と Service2.cs をコンパイルします。さらに、Program.cs をコンソール アプリケーションにコンパイルします。  
  
```  
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
  
```  
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
  
```  
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
```  
‘IService1.vb  
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
  
```  
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
  
```  
‘Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
  
```  
  
> [!NOTE]
>  このようなサービスには、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。名前空間予約の構成方法[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[HTTP および HTTPS の構成](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)」を参照してください。[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] での service.exe の実行には、管理者権限が必要です。  
  
 これでサービスが実行されていることが確認できました。「[方法 : クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)」に進んでください。トラブルシューティングの詳細については、「[チュートリアル入門のトラブルシューティング](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)」を参照してください。  
  
## 参照  
 [概要](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)