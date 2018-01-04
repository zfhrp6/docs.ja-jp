---
title: "方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e1c00abfec36622f5da493165259fb1786ab8d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する
これは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションの作成に必要な 6 つのタスクのうち、3 番目のタスクです。 タスクの 6 つのすべての概要については、次を参照してください。、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)トピックです。  
  
 このトピックでは、コンソール アプリケーションで [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスをホストする方法について説明します。 この操作は、次の手順から構成されます。  
  
-   コンソール アプリケーション プロジェクトを作成し、サービスをホストします。  
  
-   サービスのサービス ホストを作成します。  
  
-   メタデータ交換を有効にします。  
  
-   サービス ホストを開きます。  
  
 このタスクで書かれるコードの全容は手順に続いて提供されている例で見ることができます。  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>新しいコンソール アプリケーションを作成し、サービスをホストするには  
  
1.  はじめにソリューションを選択するを右クリックして新しいコンソール アプリケーション プロジェクトを作成する**追加**、**新しいプロジェクト**です。 **新しいプロジェクトの追加**ダイアログの の左側でダイアログ**Windows**  **c#**または**VB**です。 ダイアログの中央のセクションで選択**コンソール アプリケーション**です。 プロジェクトに GettingStartedHost という名前を付けます。  
  
2.  右クリックで GettingStartedHost プロジェクトのターゲット フレームワークを .NET Framework 4.5 に設定**GettingStartedHost**ソリューション エクスプ ローラーを選択して**プロパティ**です。 ラベルの付いたボックスの一覧で**ターゲット フレームワーク**選択**.NET Framework 4.5**です。 VB プロジェクトは少し異なり、GettingStartedHost プロジェクトのプロパティ ダイアログ ボックスのターゲット フレームワークを設定をクリックして、**コンパイル**、画面の左側にあるタブをクリックして、**高度なコンパイルオプション**ダイアログ ボックスの左下隅にあるボタンをクリックします。 選択し、 **.NET Framework 4.5**というドロップダウン ボックスで**ターゲット フレームワーク**です。  
  
     ターゲット フレームワークと、設定[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]キーを押して、ソリューションを再読み込みする**OK**が表示されたらです。  
  
3.  右クリック GettingStartedLib プロジェクトへの参照を GettingStartedHost プロジェクトに追加、**参照**フォルダーをクリックし、ソリューション エクスプ ローラーで GettingStartedHost プロジェクトの **参照の追加**. **参照の追加**ダイアログで、**ソリューション**をクリックして、ダイアログの中央のセクションで GettingStartedLib、ダイアログの左側にある**追加**です。 これにより、GettingStartedLib に定義されている型を GettingStartedHost プロジェクトで利用できるようになります。  
  
4.  右クリックして System.ServiceModel への参照を GettingStartedHost プロジェクトに追加、**参照**フォルダーをクリックし、ソリューション エクスプ ローラーで GettingStartedHost プロジェクトの **追加**参照。 **参照の追加**ダイアログの  **Framework**ダイアログ ボックスの左側にあります。 [アセンブリの検索] ボックスに「`System.ServiceModel`」と入力します。 ダイアログの中央のセクションで選択**System.ServiceModel**をクリックして、**追加**ボタンをクリックし、をクリックして、**閉じる**ボタンをクリックします。 メイン メニューの [すべて保存] をクリックして、ソリューションを保存します。  
  
### <a name="to-host-the-service"></a>サービスをホストするには  
  
-   Program.cs ファイルまたは Module.vb ファイルを開き、次のコードを追加します。  
  
    ```csharp
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
  
    ```vb
    'Module1.vb  
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
  
    1.  手順 1 - サービスのベース アドレスを保持する Uri クラスのインスタンスを作成します。 サービスは、ベース アドレスとオプションの URI を含む URL によって識別されます。 ベース アドレスは次の形式:://[トランスポート] [コンピューター名またはドメイン] [: 省略可能なポート番号]/[省略可能な URI セグメント]、電卓サービスのベース アドレスは、HTTP トランスポートを使用して、localhost、ポート 8000、および URI セグメント"GettingStarted"  
  
    2.  手順 2 - サービスをホストする <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。 コンストラクターは、サービス コントラクトを実装するクラスの型と、サービスのベース アドレスの、2 つのパラメーターを受け取ります。  
  
    3.  手順 3: 作成、 <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`インスタンス。 サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。 <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`コンス トラクターは、サービス コントラクト インターフェイスの型、バインディング、およびアドレスにためかかります。 サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。 このサンプルで使用するバインディングは、WS-* 仕様に準拠するエンドポイントへの接続に使用される組み込みのバインディングである <xref:System.ServiceModel.WSHttpBinding> です。 WCF バインディングの詳細については、次を参照してください。 [WCF のバインディングの概要](../../../docs/framework/wcf/bindings-overview.md)です。 エンドポイントを識別するために、ベース アドレスにアドレスが追加されます。 このコードで指定されたアドレスは"CalculatorService"エンドポイントの完全修飾アドレスは`"http://localhost:8000/GettingStarted/CalculatorService"`.NET Framework 4.0 を使用する場合は省略可能なまたはそれ以降は、サービス エンドポイントを追加します。 これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。 詳細については、既定のエンドポイントを参照してください[エンドポイント アドレスを指定する](../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] については、「 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) 」および「 [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
        > [!IMPORTANT]
        >  サービス エンドポイントの追加は、.NET Framework 4 以降を使用する場合は省略可能です。 これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。 詳細については、既定のエンドポイントを参照してください[エンドポイント アドレスを指定する](../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。 [!INCLUDE[crabout](../../../includes/crabout-md.md)] については、「 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) 」および「 [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
    4.  手順 4 - メタデータ交換を有効にします。 クライアントは、サービス操作を呼び出すために使用されるプロキシの生成にメタデータ交換を使用します。 メタデータ交換の作成を有効にする、<xref:System.ServiceModel.Description.ServiceMetadataBehavior>インスタンス、設定の<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A>プロパティを`true`の動作を追加し、 <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A`のコレクション、<xref:System.ServiceModel.ServiceHost>インスタンス。  
  
    5.  手順 5 - 受信メッセージをリッスンするために <xref:System.ServiceModel.ServiceHost> を開きます。 コードでは、ユーザーによる Enter キーの押下を待機しています。 この動作を行わない場合、アプリは直ちに終了し、サービスはシャットダウンします。また、try/catch ブロックが使用されている点にも注意してください。 <xref:System.ServiceModel.ServiceHost> がインスタンス化された後、他のコードはすべて try/catch ブロックに配置されます。 詳細については、安全にによってスローされる例外をキャッチ<xref:System.ServiceModel.ServiceHost>を参照してください[Using ステートメントに関する問題の回避](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
### <a name="to-verify-the-service-is-working"></a>サービスが正常に機能していることを確認するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 内から GettingStartedHost コンソール アプリケーションを実行します。 [!INCLUDE[wv](../../../includes/wv-md.md)] 以降のオペレーティング システムでは、サービスを管理者権限で実行する必要があります。 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] は管理者権限で実行されているため、GettingStartedHost も管理者権限で実行される必要があります。 新しいコマンド プロンプトを管理者権限で開いて、service.exe をその中で実行することもできます。  
  
2.  Internet Explorer を開き、サービスのデバッグ ページ (`http://localhost:8000/GettingStarted/CalculatorService`) に移動します。  
  
## <a name="example"></a>例  
 次の例では、チュートリアルの前の手順で作成したサービス コントラクトと実装を含め、コンソール アプリケーションでサービスをホストします。  
  
 コマンド ライン コンパイラでコンパイルを参照するクラス ライブラリに IService1.cs と Service1.cs をコンパイル`System.ServiceModel.dll`です。 さらに、Program.cs をコンソール アプリケーションにコンパイルします。  
  
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
  
```csharp
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
  
```vb
'IService1.vb  
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
'Service1.vb  
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
  
```vb
'Module1.vb  
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
>  このようなサービスには、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。 管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]参照してください、名前空間の予約を構成する方法[を構成する HTTP および HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)です。 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] での service.exe の実行には、管理者権限が必要です。  
  
 これでサービスが実行されていることが確認できました。 進みます[する方法: クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。 情報をトラブルシューティングするには、次を参照してください。[チュートリアル入門のトラブルシューティング](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)です。  
  
## <a name="see-also"></a>参照  
 [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
