---
title: "メンバーシップとロール プロバイダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2107c5ae03330eb82567ab483dcd7003a35e189
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="membership-and-role-provider"></a>メンバーシップとロール プロバイダー
メンバーシップとロール プロバイダーのサンプルでは、サービスが [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップとロール プロバイダーを使用してクライアントを認証および承認するための方法を示します。  
  
 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、次の方法を示します。  
  
-   クライアントがユーザー名とパスワードの組み合わせを使用して認証する。  
  
-   サーバーがクライアント資格情報を [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーと照合する。  
  
-   サーバーがそのサーバーの X.509 証明書を使用して認証される。  
  
-   サーバーが [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーを使用して、認証されたクライアントをロールにマップする。  
  
-   サーバーが `PrincipalPermissionAttribute` を使用して、サービスによって公開される特定メソッドへのアクセスを制御する。  
  
 メンバーシップとロール プロバイダーは、SQL Server によってサポートされるストアを使用するように構成されます。 接続文字列と各種オプションは、サービス構成ファイルで指定されます。 メンバーシップ プロバイダーの名前は `SqlMembershipProvider` と指定され、ロール プロバイダーの名前は `SqlRoleProvider` と指定されます。  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"   
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add   
        name="SqlMembershipProvider"   
        type="System.Web.Security.SqlMembershipProvider"   
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"   
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 サービスは、そのサービスとの通信に使用する単一エンドポイントを公開します。エンドポイントは Web.config 構成ファイルで定義します。 エンドポイントは、アドレス、バインディング、およびコントラクトがそれぞれ 1 つずつで構成されます。 バインディングの構成には、標準の `wsHttpBinding` が使用されます。既定では、Windows 認証が使用されます。 このサンプルは、標準の `wsHttpBinding` を設定してユーザー名認証を使用します。 この動作により、サービス認証でサーバー証明書が使用されることが指定されます。 サーバー証明書が同じ値を含める必要があります、`SubjectName`として、`findValue`属性、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)構成要素。 さらに、メンバーシップとロール プロバイダーで定義されている名前を指定することにより、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] メンバーシップ プロバイダーによってユーザー名とパスワードの組み合わせによる認証が実行され、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ロール プロバイダーによってロール マップが実行されることが、この動作によって指定されます。  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"   
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"   
                              storeName ="My"   
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 このサンプルを実行すると、クライアントは、Alice、Bob、および Charlie の 3 人のユーザー アカウントによる各種サービス操作を呼び出します。 操作要求と応答は、クライアントのコンソール ウィンドウに表示されます。 ユーザー "Alice" として行われた 4 つの呼び出しはすべて正常に終了します。 ユーザー "Bob" には、Divide メソッドの呼び出しを試行したときにアクセス拒否エラーが通知されます。 ユーザー "Charlie" には、Multiply メソッドの呼び出しを試行したときにアクセス拒否エラーが通知されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  C# または Visual Basic .NET のバージョンのソリューションをビルドするの指示に従って、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
2.  構成していることを確認してください、 [ASP.NET アプリケーション サービス データベース](http://go.microsoft.com/fwlink/?LinkId=94997)です。  
  
    > [!NOTE]
    >  SQL Server Express Edition を実行している場合、サーバー名は .\SQLEXPRESS になります。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] アプリケーション サービス データベースの構成および Web.config ファイルの接続文字列では、このサーバーを使用する必要があります。  
  
    > [!NOTE]
    >  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ワーカー プロセス アカウントには、この手順で作成されるデータベースに対するアクセス許可が必要です。 これを実行するには、sqlcmd ユーティリティまたは SQL Server Management Studio を使用します。  
  
3.  サンプルを単一コンピューター構成で実行するか、複数コンピューター構成で実行するかに応じて、次の手順に従います。  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>サンプルを同じコンピューターで実行するには  
  
1.  Makecert.exe が存在するフォルダーがパスに含まれていることを確認します。  
  
2.  管理特権で実行した Visual Studio コマンド プロンプトで、サンプルのインストール フォルダーから Setup.bat を実行します。 これにより、サンプルの実行に必要なサービス証明書がインストールされます。  
  
3.  Client.exe を \client\bin で起動します。 クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。  
  
4.  クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### <a name="to-run-the-sample-across-computers"></a>サンプルを複数のコンピューターで実行するには  
  
1.  サービス コンピューターにディレクトリを作成します。 インターネット インフォメーション サービス (IIS) 管理ツールを使用して、このディレクトリ用に servicemodelsamples という仮想アプリケーションを作成します。  
  
2.  サービス プログラム ファイルを \inetpub\wwwroot\servicemodelsamples からサービス コンピューターの仮想ディレクトリにコピーします。 ファイルのコピー先が \bin サブディレクトリであることを確認します。 Setup.bat、GetComputerName.vbs、Cleanup.bat の各ファイルもサービス コンピューターにコピーします。  
  
3.  クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。  
  
4.  クライアント プログラム ファイルを、クライアント コンピューターに作成したクライアント ディレクトリにコピーします。 Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。  
  
5.  サーバー上で管理特権を使用して Visual Studio コマンド プロンプトを開き、`setup.bat service` を実行します。 実行している`setup.bat`で、`service`引数が、コンピューターの完全修飾ドメイン名でサービス証明書を作成し、サービス証明書が Service.cer というファイルにエクスポートします。  
  
6.  新しい証明書名を反映するように Web.config を編集 (で、`findValue`属性、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md))、これは、コンピューターの完全修飾ドメイン名と同じです。  
  
7.  Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。  
  
8.  クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。  
  
9. クライアント上で、管理特権を使用して Visual Studio コマンド プロンプトを開き、ImportServiceCert.bat を実行します。 これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。  
  
10. クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。 クライアントとサービス間で通信できない場合は、「 [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### <a name="to-clean-up-after-the-sample"></a>サンプルの実行後にクリーンアップするには  
  
-   サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。  
  
> [!NOTE]
>  このサンプルを複数のコンピューターで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。 複数のコンピューターで証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルを実行した場合は、CurrentUser - TrustedPeople ストアにインストールされたサービス証明書を忘れずに削除してください。 削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。  
  
## <a name="the-setup-batch-file"></a>セットアップ バッチ ファイル  
 このサンプルに用意されている Setup.bat バッチ ファイルを使用すると、適切な証明書を使用してサーバーを構成し、サーバー証明書ベースのセキュリティを必要とする自己ホスト型アプリケーションを実行できるようになります。 このバッチ ファイルは、複数のコンピューターを使用する場合またはホストなしの場合に応じて変更する必要があります。  
  
 次に、バッチ ファイルのセクションのうち、該当する構成で実行するために変更が必要となる部分を示します。  
  
-   サーバー証明書の作成。  
  
     Setup.bat バッチ ファイルの次の行は、使用するサーバー証明書を作成します。 %SERVER_NAME% 変数はサーバー名を指定します。 この変数を変更して、使用するサーバー名を指定します。 このバッチ ファイルでの既定は localhost です。  
  
     証明書は、LocalMachine ストアの場所の My (Personal) ストアに保存されます。  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   クライアントの信頼された証明書ストアへのサーバー証明書のインストール。  
  
     Setup.bat バッチ ファイルの次の行は、サーバー証明書をクライアントの信頼されたユーザーのストアにコピーします。 この手順が必要なのは、Makecert.exe によって生成される証明書がクライアント システムにより暗黙には信頼されないからです。 マイクロソフト発行の証明書など、クライアントの信頼されたルート証明書に基づいた証明書が既にある場合は、クライアント証明書ストアにサーバー証明書を配置するこの手順は不要です。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
## <a name="see-also"></a>関連項目
