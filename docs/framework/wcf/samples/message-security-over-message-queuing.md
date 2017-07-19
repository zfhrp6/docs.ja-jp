---
title: "メッセージ キューを介したメッセージ セキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: 22
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 22
---
# メッセージ キューを介したメッセージ セキュリティ
このサンプルでは、クライアントの認証で X.509v3 証明書による WS\-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509v3 証明書を MSMQ 経由で使用するサーバー認証が必要です。MSMQ ストア内のメッセージの暗号化を保持したり、アプリケーションで独自のメッセージ認証を実行できるようにするには、メッセージ セキュリティの使用が望ましい場合があります。  
  
 このサンプルは、「[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)」のサンプルに基づいています。メッセージは暗号化されて署名されます。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。キューが存在しない場合、サービスによってキューが作成されます。最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  **\[機能\]** タブを展開します。  
  
    3.  **\[プライベート メッセージ キュー\]** を右クリックし、**\[新規作成\]**、**\[専用キュー\]** の順にクリックします。  
  
    4.  **\[トランザクション\]** ボックスをオンにします。  
  
    5.  新しいキューの名前として、「`ServiceModelSamplesTransacted`」と入力します。  
  
3.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
### サンプルを同じコンピューターで実行するには  
  
1.  Makecert.exe と FindPrivateKey.exe を格納するフォルダーがパスに含まれていることを確認します。  
  
2.  Setup.bat をサンプルのインストール フォルダで実行します。これにより、サンプルの実行に必要なすべての証明書がインストールされます。  
  
    > [!NOTE]
    >  サンプルの実行後は、Cleanup.bat を実行して証明書を削除してください。他のセキュリティ サンプルでも同じ証明書を使用します。  
  
3.  Service.exe を \\service\\bin で起動します。  
  
4.  Client.exe を \\client\\bin で起動します。クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
5.  クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルを複数のコンピューターで実行するには  
  
1.  Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルをサービス コンピューターにコピーします。  
  
2.  クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。  
  
3.  クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。  
  
4.  サーバーで `setup.bat service` を実行します。`setup.bat` に `service` 引数を指定して実行すると、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、Service.cer というファイルにエクスポートされます。  
  
5.  サービスの service.exe.config を編集して、新しい証明書名 \([\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)の `findValue` 属性\) を反映します。これは、コンピューターの完全修飾ドメイン名と同じです。  
  
6.  Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
7.  クライアントで `setup.bat client` を実行します。`setup.bat` に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。  
  
8.  クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。さらに、サービス証明書の名前を、サービス コンピューターの完全修飾ドメイン名 \(`clientCredentials` の下にある `serviceCertificate` の `defaultCertificate` 要素の `findValue` 属性\) と同じ名前に変更する必要があります。  
  
9. Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。  
  
10. クライアントで `ImportServiceCert.bat` を実行します。これにより、サービス証明書が Service.cer ファイルから CurrentUser \- TrustedPeople ストアにインポートされます。  
  
11. サーバーで `ImportClientCert.bat` を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine \- TrustedPeople ストアにインポートされます。  
  
12. サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。  
  
13. クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルの実行後にクリーンアップするには  
  
-   サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  
  
    > [!NOTE]
    >  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。複数のコンピューターで証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルを実行した場合は、CurrentUser \- TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。  
  
## 必要条件  
 このサンプルでは、MSMQ がインストールされて実行中であることが必要です。  
  
## 使用例  
 クライアントは、サービスの公開キーを使用してメッセージを暗号化し、独自の証明書を使用してメッセージ署名を行います。キューからのメッセージを読み込むサービスは、信頼されたユーザーのストア内の証明書を使用して、クライアント証明書を認証します。次にメッセージを復号化し、サービス操作にディスパッチします。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] メッセージは MSMQ メッセージの本文のペイロードとして送信されるので、メッセージ本文は MSMQ ストアで暗号化されたまま残ります。これによりメッセージは、望ましくない公開から保護されます。MSMQ 自体では、送信されるメッセージが暗号化されているかどうかは認識されません。  
  
 このサンプルは、MSMQ でメッセージ レベルの相互認証を使用する方法を示します。証明書は、帯域外で交換されます。サービスとクライアントは同時に実行される必要がないため、キューに置かれたアプリケーションでは常にその状態です。  
  
## 説明  
 クライアントとサービス コードのこのサンプルは、1 つの違いを除き、「[トランザクション MSMQ バインディング](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)」と同じです。操作コントラクトには、メッセージの署名および暗号化が必要であることを示す注釈が保護レベルで付けられます。  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 メッセージが、サービスとクライアントの識別に必要なトークンを使用してセキュリティ保護されるには、App.config に資格情報を格納する必要があります。  
  
 クライアント構成では、サービスを認証するサービス証明書を指定します。また、LocalMachine のストアを信頼されるストアとして使用し、サービスの有効性を信頼します。さらに、クライアントのサービス認証用として、メッセージに関連付けられたクライアント証明書を指定します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"   
                binding="netMsmqBinding"   
                bindingConfiguration="messageSecurityBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"  
                behaviorConfiguration="ClientCertificateBehavior" />  
    </client>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate"/>  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 セキュリティ モードが Message に設定されている場合は、ClientCredentialType は Certificate に設定されることに注意してください。  
  
 サービス構成には、サービスの資格情報を指定するサービス動作が含まれます。この資格情報は、クライアントがサービスを認証する際に使用されます。サーバー証明書のサブジェクト名は、[\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)の `findValue` 属性で指定されています。  
  
```  
  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
          behaviorConfiguration="PurchaseOrderServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="messageSecurityBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="PurchaseOrderServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!--   
               The serviceCredentials behavior allows one to define a service certificate.  
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
               This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
  
```  
  
 このサンプルは、構成を使用した認証の制御、およびセキュリティ コンテキストから呼び出し側の ID を取得する方法を示しています。次のサンプル コードを参照してください。  
  
```  
    // Service class which implements the service contract.  
    // Added code to write output to the console window.  
    public class OrderProcessorService : IOrderProcessor  
    {  
        private string GetCallerIdentity()  
        {  
            // The client certificate is not mapped to a Windows identity by default.  
            // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
            // in the certificate that the client used to authenticate itself to the service.  
            return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void SubmitPurchaseOrder(PurchaseOrder po)  
        {  
            Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
  //…  
}  
```  
  
 実行時、サービス コードにはクライアント ID が表示されます。サービス コードからの出力サンプルを次に示します。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C  
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
## 説明  
  
-   クライアント証明書の作成。  
  
     バッチ ファイルの次の行では、クライアント証明書を作成します。指定されたクライアント名が、作成される証明書のサブジェクト名に使用されます。証明書は、`CurrentUser` ストアの場所の `My` ストアに格納されます。  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
  
    ```  
  
-   クライアント証明書のサーバーの信頼された証明書ストアへのインストール。  
  
     バッチ ファイルの次の行では、クライアント証明書をサーバーの TrustedPeople ストアにコピーし、サーバーが信頼\/非信頼を判断できるようにします。TrustedPeople ストアにインストールされた証明書が [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに信頼されるには、クライアント証明書の検証モードの値を `PeerOrChainTrust` または `PeerTrust` に設定する必要があります。前のサービス構成サンプルを参照して、構成ファイルを使用してこれを行う手順を確認してください。  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
  
    ```  
  
-   サーバー証明書の作成。  
  
     Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     %SERVER\_NAME% 変数はサーバー名を指定します。証明書は LocalMachine ストアに保存されます。セットアップ バッチ ファイルの実行にサービスの引数 \(`setup.bat service` など\) が使用された場合、%SERVER\_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。それ以外の場合、既定値は localhost です。  
  
-   サーバー証明書のクライアントの信頼された証明書ストアへのインストール。  
  
     次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないためです。マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  英語 \(米国\) 以外の言語で Microsoft Windows を使用している場合は、Setup.bat ファイルを編集し、"NT AUTHORITY\\NETWORK SERVICE" アカウント名を現在の地域に適した名前に変更してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## 参照