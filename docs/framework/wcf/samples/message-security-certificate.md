---
title: "メッセージ セキュリティ証明書 | Microsoft Docs"
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
  - "WS セキュリティ"
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
caps.latest.revision: 51
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 51
---
# メッセージ セキュリティ証明書
このサンプルでは、クライアントの認証で X.509 v3 証明書による WS\-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509 v3 証明書を使用するサーバー認証が必要です。このサンプルでは、クライアント\/サーバー間のすべてのアプリケーション メッセージが署名されて暗号化される、既定の設定を使用します。このサンプルは、「[WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)」に基づいており、クライアント コンソール プログラムと、インターネット インフォメーション サービス \(IIS\) によってホストされるサービス ライブラリで構成されています。サービスは、要求\/応答通信パターンを定義するコントラクトを実装します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、構成を使用した認証の制御、およびセキュリティ コンテキストから呼び出し側の ID を取得する方法を示しています。次のサンプル コードを参照してください。  
  
```  
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 サービスは、そのサービスとの通信に使用する 1 つのエンドポイントと、WS\-MetadataExchange プロトコルを使用してサービスの WSDL ドキュメントを公開する 1 つのエンドポイントを公開します。これらのエンドポイントは構成ファイル \(Web.config\) で定義します。エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。バインディングは、標準の [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 要素で構成されます。既定では、メッセージ セキュリティが使用されます。このサンプルでは、クライアント認証が必要な証明書に `clientCredentialType` 属性を設定します。  
  
```  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
  
```  
  
 この動作により、クライアントがサービスを認証する際に使用される、サービスの資格情報が指定されます。サーバー証明書のサブジェクト名は、[\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) 要素の `findValue` 属性で指定されます。  
  
```  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
  
```  
  
 クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。クライアント バインディングは、適切なセキュリティ モードおよび認証モードで構成されます。複数コンピューターのシナリオで実行する場合は、サービスのエンドポイント アドレスが適切に変更されていることを確認してください。  
  
```  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
  
```  
  
 クライアントの実装により、構成ファイルまたコードを使用して、使用する証明書が設定されます。次のサンプルでは、使用する証明書を構成ファイルで設定する方法を示します。  
  
```  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
  
```  
  
 次のサンプルでは、プログラムでサービスを呼び出す方法を示します。  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 メッセージ セキュリティ サンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してクライアントとサーバーを構成し、証明書ベースのセキュリティを必要とするホスト アプリケーションを実行できるようになります。バッチ ファイルの実行には 3 つのモードを使用できます。単一コンピューター モードで実行するには、Visual Studio コマンド プロンプトで「**setup.bat**」と入力します。同様に、サービス モードの場合は「**setup.bat service**」と入力し、クライアント モードの場合は「**setup.bat client**」と入力します。このサンプルを複数のコンピューターで実行している場合は、クライアントおよびサーバー モードを使用します。詳細については、このトピック末尾のセットアップ手順を参照してください。次に、バッチ ファイルのセクションのうち、適切な構成で実行するために変更が必要となる部分を示します。  
  
-   クライアント証明書の作成。  
  
     バッチ ファイルの次の行では、クライアント証明書を作成します。指定されたクライアント名が、作成される証明書のサブジェクト名に使用されます。証明書は、`CurrentUser` ストアの場所の `My` ストアに格納されます。  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   サーバーの信頼された証明書ストアへのクライアント証明書のインストール。  
  
     バッチ ファイルの次の行では、クライアント証明書をサーバーの TrustedPeople ストアにコピーし、サーバーが信頼\/非信頼を判断できるようにします。TrustedPeople ストアにインストールされた証明書が [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに信頼されるには、クライアント証明書の検証モードを `PeerOrChainTrust` または `PeerTrust` に設定する必要があります。前のサービス構成サンプルを参照して、構成ファイルを使用してこれを行う手順を確認してください。  
  
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
  
     %SERVER\_NAME% 変数はサーバー名を指定します。証明書は LocalMachine ストアに保存されます。Setup.bat バッチ ファイルの実行にサービスの引数 \(**setup.bat service** など\) が使用された場合、%SERVER\_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。それ以外の場合、既定値は localhost です。  
  
-   クライアントの信頼された証明書ストアへのサーバー証明書のインストール。  
  
     次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないためです。マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   証明書の秘密キーに関する権限の付与。  
  
     Setup.bat ファイルの次の行は、LocalMachine ストアに保存されたサーバー証明書を [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ワーカー プロセス アカウントでアクセスできるようにします。  
  
    ```  
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    >  英語 \(米国\) 以外の言語で Windows を使用している場合は、Setup.bat ファイルを編集し、"NT AUTHORITY\\NETWORK SERVICE" アカウント名を現在の地域に適した名前に変更してください。  
  
> [!NOTE]
>  このバッチ ファイルで使用されるツールは、C:\\Program Files\\Microsoft Visual Studio 8\\Common7\\tools または C:\\Program Files\\Microsoft SDKs\\Windows\\v6.0\\bin にあります。これらのディレクトリのうちいずれか 1 つは、システム パスにする必要があります。Visual Studio がインストールされている場合は、Visual Studio コマンド プロンプトを開いて、このディレクトリを簡単にパスに配置できます。**\[スタート\]**をクリックし、**\[すべてのプログラム\]**、**\[Visual Studio 2012\]**、**\[ツール\]** の順にクリックします。このコマンド プロンプトには、適切なパスが既に設定されています。設定されていない場合は、適切なディレクトリをパスに手動で追加する必要があります。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
### サンプルを同じコンピューターで実行するには  
  
1.  管理特権を使用して Visual Studio コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。これにより、サンプルの実行に必要なすべての証明書がインストールされます。  
  
    > [!NOTE]
    >  Setup.bat バッチ ファイルは、Visual Studio コマンド プロンプトから実行します。path 環境変数が SDK のインストール ディレクトリを指している必要があります。この環境変数は、Visual Studio コマンド プロンプト \(2010\) で自動設定されます。  
  
2.  サービスへのアクセスを検証します。ブラウザーにアドレス「`http://localhost/servicemodelsamples/service.svc`」を入力します。  
  
3.  Client.exe を \\client\\bin で起動します。クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
4.  クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルを複数のコンピューターで実行するには  
  
1.  サービス コンピューターにディレクトリを作成します。インターネット インフォメーション サービス \(IIS\) 管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。  
  
2.  サービス プログラム ファイルを \\inetpub\\wwwroot\\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。ファイルのコピー先が \\bin サブディレクトリであることを確認します。また Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルもサービス コンピューターにコピーします。  
  
3.  クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。  
  
4.  クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。  
  
5.  サーバー上で管理特権を使用して Visual Studio コマンド プロンプトを開き、**setup.bat service** を実行します。**setup.bat** に **service** 引数を指定して実行すると、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、Service.cer というファイルにエクスポートされます。  
  
6.  Web.config を編集して、新しい証明書名 \([\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)の `findValue` 属性\) を反映します。これは、コンピューターの完全修飾ドメイン名と同じです。  
  
7.  Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
8.  クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、**setup.bat client** を実行します。**setup.bat** に **client** 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。  
  
9. クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。  
  
10. Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。  
  
11. クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。これにより、サービス証明書が Service.cer ファイルから CurrentUser \- TrustedPeople ストアにインポートされます。  
  
12. サーバー上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportClientCert.bat を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine \- TrustedPeople ストアにインポートされます。  
  
13. クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルの実行後にクリーンアップするには  
  
-   サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  
  
    > [!NOTE]
    >  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。複数のコンピューターで証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルを実行した場合は、CurrentUser \- TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。  
  
## 参照