---
title: "メッセージ セキュリティ ユーザー名"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
caps.latest.revision: "57"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4df9b3d5c1f073b1b2348220ac1a77efbe797311
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-user-name"></a>メッセージ セキュリティ ユーザー名
このサンプルでは、クライアントのユーザー名認証による WS-Security を使用するアプリケーションを実装する方法を示します。このアプリケーションでは、サーバーの X.509v3 証明書を使用するサーバー認証が必要です。 クライアント/サーバー間のすべてのアプリケーション メッセージは署名され、暗号化されます。 既定では、クライアントによって提供されるユーザー名とパスワードが、有効な Windows アカウントへのログオンに使用されます。 このサンプルがに基づいて、 [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md)です。 このサンプルは、クライアント コンソール プログラム (Client.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (Service.dll) で構成されています。 サービスは、要求/応答通信パターンを定義するコントラクトを実装します。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、さらに次の方法も示します。  
  
-   追加の承認を実行できるようにするための、Windows アカウントへの既定のマッピング。  
  
-   サービス コードから呼び出し元の ID 情報にアクセスする方法。  
  
 サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは構成ファイル Web.config で定義します。エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。 標準バインディングの構成は[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティを使用して既定値です。 このサンプルでは、標準設定[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)クライアント ユーザー名認証を使用します。 この動作により、サービス認証でユーザーの資格情報が使用されることが指定されます。 サーバー証明書のサブジェクト名と同じ値を含める必要があります、`findValue`属性、 [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)です。  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 クライアント エンドポイント構成は、サービス エンドポイントの絶対アドレス、バインディング、およびコントラクトで構成されます。 クライアント バインディングは、適切な `securityMode` と `authenticationMode` で構成されます。 複数コンピューターのシナリオで実行する場合は、サービスのエンドポイント アドレスを適切に変更する必要があります。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 クライアント実装では、使用するユーザー名とパスワードが設定されます。  
  
```  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 MessageSecurity サンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、証明書ベースのセキュリティを必要とするホスト アプリケーションを実行できるようになります。 バッチ ファイルの実行には 2 つのモードを使用できます。 バッチ ファイルを単一コンピューター モードで実行するには、コマンド ラインに「`setup.bat`」と入力します。 サービス モードで実行するには、「`setup.bat service`」と入力します。 このサンプルを複数のコンピューターで実行している場合は、このモードを使用します。 詳細については、このトピック末尾のセットアップ手順を参照してください。  
  
 次に、バッチ ファイルの各セクションの概要を簡単に説明します。  
  
-   サーバー証明書の作成  
  
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
  
     %SERVER_NAME% 変数はサーバー名を指定します。 証明書は LocalMachine ストアに保存されます。 Setup.bat バッチ ファイルの実行にサービスの引数 (`setup.bat service` など) が使用された場合、%SERVER_NAME% にはコンピューターの完全修飾ドメイン名が含まれます。  それ以外の場合、既定値は localhost です。  
  
-   クライアントの信頼された証明書ストアへのサーバー証明書のインストール  
  
     次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。 この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。 マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   証明書の秘密キーに関する権限の付与  
  
     Setup.bat バッチ ファイルの次の行は、LocalMachine ストアに保存されたサーバー証明書を [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ワーカー プロセス アカウントでアクセスできるようにします。  
  
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
    >  英語 (米国) 以外の言語で Windows を使用している場合は、Setup.bat ファイルを編集し、`NT AUTHORITY\NETWORK SERVICE` アカウント名を現在の地域に適した名前に変更してください。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>サンプルを同じコンピューターで実行するには  
  
1.  Makecert.exe と FindPrivateKey.exe が含まれているフォルダーがパスに含まれていることを確認します。  
  
2.  管理特権を使用して Visual Studio コマンド プロンプトを開き、サンプルのインストール フォルダーから Setup.bat を実行します。 これにより、サンプルの実行に必要なすべての証明書がインストールされます。  
  
    > [!NOTE]
    >  Setup.bat バッチ ファイルは、Visual Studio コマンド プロンプトから実行します。 path 環境変数が SDK のインストール ディレクトリを指している必要があります。 この環境変数は、Visual Studio コマンド プロンプトで自動設定されます。  
  
3.  サービスへのアクセスを検証します。ブラウザーにアドレス「http://localhost/servicemodelsamples/service.svc」を入力します。  
  
4.  Client.exe を \client\bin で起動します。 クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
5.  クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### <a name="to-run-the-sample-across-computers"></a>サンプルを複数のコンピューターで実行するには  
  
1.  サービス コンピューターにディレクトリを作成します。 インターネット インフォメーション サービス管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。  
  
2.  サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。 ファイルのコピー先が \bin サブディレクトリであることを確認します。 Setup.bat ファイルと Cleanup.bat ファイルもサービス コンピューターにコピーします。  
  
3.  クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。  
  
4.  クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。 Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。  
  
5.  サーバー上で管理特権を使用して Visual Studio コマンド プロンプトを開き、`setup.bat service` を実行します。 実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。  
  
6.  Web.config を編集して、新しい証明書名 (serviceCertificate 要素の findValue 属性) を反映します。これは、コンピューターの完全修飾ドメイン名と同じです。`.`  
  
7.  Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
8.  クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。  
  
9. クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。 これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。  
  
10. クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。 クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### <a name="to-clean-up-after-the-sample"></a>サンプルの実行後にクリーンアップするには  
  
-   サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  
  
    > [!NOTE]
    >  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。 複数のコンピューターで証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルを実行した場合は、CurrentUser - TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。 削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。  
  
## <a name="see-also"></a>参照
