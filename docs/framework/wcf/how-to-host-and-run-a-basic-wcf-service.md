---
title: '方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: f1c56ed83fa214cf781a833e05642635ac24b0c5
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753501"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>方法 : 基本的な Windows Communication Foundation サービスをホストおよび実行する
Windows Communication Foundation (WCF) アプリケーションの作成に必要な 6 つのタスクのうちの 3 番目がこれです。 6 つのすべてのタスクの概要については、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
 このトピックでは、コンソール アプリケーションで Windows Communication Foundation (WCF) サービスをホストする方法について説明します。 この操作は、次の手順から構成されます。  
  
-   コンソール アプリケーション プロジェクトを作成し、サービスをホストします。  
  
-   サービスのサービス ホストを作成します。  
  
-   メタデータ交換を有効にします。  
  
-   サービス ホストを開きます。  
  
 このタスクで書かれるコードの全容は手順に続いて提供されている例で見ることができます。  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>新しいコンソール アプリケーションを作成し、サービスをホストするには  
  
1.  入門ソリューションを右クリックし、**[追加]**、**[新しいプロジェクト]** の順にクリックして新しいコンソール アプリケーション プロジェクトを作成します。 **[新しいプロジェクトの追加]** ダイアログ ボックスの左側で、**[C#]** または **[VB]** の下にある **[Windows]** を選択します。 ダイアログ ボックスの中央のセクションで、**[コンソール アプリケーション]** を選択します。 プロジェクトに GettingStartedHost という名前を付けます。  
  
2.  ソリューション エクスプローラーで **[GettingStartedHost]** を右クリックし、**[プロパティ]** を選択することで、GettingStartedHost プロジェクトのターゲット フレームワークを .NET Framework 4.5 に設定します。 **[ターゲット フレームワーク]** ボックスの一覧で、**[.NET Framework 4.5]** を選択します。 VB プロジェクトのターゲット フレームワークを設定する方法は多少異なり、GettingStartedHost プロジェクトの [プロパティ] ダイアログ ボックスで、画面左側の **[コンパイル]** タブをクリックし、ダイアログ ボックスの左下隅にある **[詳細コンパイル オプション]** ボタンをクリックします。 次に、**[ターゲット フレームワーク]** ボックスの一覧の **[.NET Framework 4.5]** を選択します。  
  
     ターゲット フレームワークを設定すると、[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] はソリューションを再読み込みします。ダイアログが表示されたら、**[OK]** をクリックします。  
  
3.  GettingStartedLib プロジェクトへの参照を GettingStartedHost プロジェクトに追加します。ソリューション エクスプローラーで GettingStartedHost プロジェクトの **[参照]** フォルダーを右クリックし、**[参照の追加]** をクリックします。 **[参照の追加]** ダイアログで、ダイアログの左側の **[ソリューション]** を選択します。ダイアログの中央セクションで [GettingStartedLib] を選択し、**[追加]** をクリックします。 これにより、GettingStartedLib に定義されている型を GettingStartedHost プロジェクトで利用できるようになります。  
  
4.  ソリューション エクスプローラーで GettingStartedHost プロジェクトの **[参照]** フォルダーを右クリックし、**[参照の追加]** を選択することで、System.ServiceModel の参照を GettingStartedHost プロジェクトに追加します。 **[参照の追加]** ダイアログ ボックスの左側で、**[フレームワーク]** を選択します。 [アセンブリの検索] ボックスに「`System.ServiceModel`」と入力します。 ダイアログ ボックスの中央のセクションで、**[System.ServiceModel]** を選択し、**[追加]** をクリックして、**[閉じる]** をクリックします。 メイン メニューの [すべて保存] をクリックして、ソリューションを保存します。  
  
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
  
    1.  手順 1 - サービスのベース アドレスを保持する Uri クラスのインスタンスを作成します。 サービスは、ベース アドレスとオプションの URI を含む URL によって識別されます。 ベース アドレスの書式は、[トランスポート]://[コンピューター名またはドメイン][:省略可能なポート番号]/[省略可能な URI セグメント] です。電卓サービスのベース アドレスは、電卓サービスのベース アドレスを使用して HTTP トランスポート、localhost、ポート 8000、および URI セグメント "GettingStarted" を使用します。  
  
    2.  手順 2 - サービスをホストする <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。 コンストラクターは、サービス コントラクトを実装するクラスの型と、サービスのベース アドレスの、2 つのパラメーターを受け取ります。  
  
    3.  手順 3 - <xref:System.ServiceModel.Description.ServiceEndpoint> インスタンスを作成します。 サービス エンドポイントは、アドレス、バインディング、およびサービス コントラクトから構成されます。 <xref:System.ServiceModel.Description.ServiceEndpoint> コンストラクターは、サービス コントラクト インターフェイスの型、バインディング、およびアドレスを受け取ります。 サービス コントラクトは、サービス型に定義および実装した `ICalculator` です。 このサンプルで使用するバインディングは、WS-* 仕様に準拠するエンドポイントへの接続に使用される組み込みのバインディングである <xref:System.ServiceModel.WSHttpBinding> です。 WCF バインディングの詳細については、[WCF バインディングの概要](../../../docs/framework/wcf/bindings-overview.md)に関するページを参照してください。 エンドポイントを識別するために、ベース アドレスにアドレスが追加されます。 このコードに指定されているアドレスは "CalculatorService" です。そのため、エンドポイントの完全修飾アドレスは `"http://localhost:8000/GettingStarted/CalculatorService"` になります。 .NET Framework 4.0 以降を使用するとき、サービス エンドポイントの追加は任意です。 これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。 既定のエンドポイントの詳細については、「[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」 (エンドポイント アドレスの指定) を参照してください。 既定のエンドポイントについては、「[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。  
  
        > [!IMPORTANT]
        >  サービス エンドポイントの追加は、.NET Framework 4 以降を使用する場合は省略可能です。 これらのバージョンでは、エンドポイントがコードまたは構成で指定されていない場合、WCF は、サービスで実装されたベース アドレスとコントラクトの組み合わせごとに、1 つの既定のエンドポイントを追加します。 既定のエンドポイントの詳細については、「[Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md)」 (エンドポイント アドレスの指定) を参照してください。 既定のエンドポイントについては、「[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)」 (簡易構成) と「[Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」 (WCF サービスの簡易構成) を参照してください。  
  
    4.  手順 4 - メタデータ交換を有効にします。 クライアントは、サービス操作を呼び出すために使用されるプロキシの生成にメタデータ交換を使用します。 メタデータ交換を有効化するには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成してその <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定し、動作を <xref:System.ServiceModel.ServiceHost> インスタンスの <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` コレクションに追加します。  
  
    5.  手順 5 - 受信メッセージをリッスンするために <xref:System.ServiceModel.ServiceHost> を開きます。 コードでは、ユーザーによる Enter キーの押下を待機しています。 この動作を行わない場合、アプリは直ちに終了し、サービスはシャットダウンします。また、try/catch ブロックが使用されている点にも注意してください。 <xref:System.ServiceModel.ServiceHost> がインスタンス化された後、他のコードはすべて try/catch ブロックに配置されます。 <xref:System.ServiceModel.ServiceHost> によってスローされた例外を安全にキャッチする方法の詳細については、「[Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)」 (using ステートメントで問題を回避する) を参照してください。  
  
### <a name="to-verify-the-service-is-working"></a>サービスが正常に機能していることを確認するには  
  
1.  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 内から GettingStartedHost コンソール アプリケーションを実行します。 [!INCLUDE[wv](../../../includes/wv-md.md)] 以降のオペレーティング システムでは、サービスを管理者権限で実行する必要があります。 Visual Studio が管理者権限で実行されるため、GettingStartedHost も管理者権限で実行されます。 新しいコマンド プロンプトを管理者権限で開いて、service.exe をその中で実行することもできます。  
  
2.  Internet Explorer を開き、サービスのデバッグ ページ (`http://localhost:8000/GettingStarted/CalculatorService`) に移動します。  
  
## <a name="example"></a>例  
 次の例では、チュートリアルの前の手順で作成したサービス コントラクトと実装を含め、コンソール アプリケーションでサービスをホストします。  
  
 コマンド ライン コンパイラでこれをコンパイルするには、`System.ServiceModel.dll` を参照するクラス ライブラリに IService1.cs と Service1.cs をコンパイルします。 さらに、Program.cs をコンソール アプリケーションにコンパイルします。  
  
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
>  このようなサービスには、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。 管理者アカウントにはこのアクセス許可がありますが、管理者以外のアカウントの場合は、HTTP 名前空間へのアクセス許可を付与する必要があります。 名前空間の予約を構成する方法については、「[Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)」 (HTTP と HTTPS を構成する) を参照してください。 Visual Studio で service.exe を実行するには、管理者権限が必要です。  
  
 これでサービスが実行されていることが確認できました。 [クライアントの作成方法](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)に関するページにお進みください。 トラブルシューティングについては、「[Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)」 (チュートリアル入門のトラブルシューティング) を参照してください。  
  
## <a name="see-also"></a>参照  
 [はじめに](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自己ホスト](../../../docs/framework/wcf/samples/self-host.md)
