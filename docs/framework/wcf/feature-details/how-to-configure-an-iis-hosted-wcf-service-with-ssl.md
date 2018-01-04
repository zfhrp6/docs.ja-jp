---
title: "IIS でホストされる WCF サービスに SSL を構成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b16ca5b4cfe615eedd9e532b12f61394806829bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>IIS でホストされる WCF サービスに SSL を構成する方法
ここでは、HTTP トランスポート セキュリティを使用するように IIS でホストされる WCF サービスをセットアップする方法について説明します。 HTTP トランスポート セキュリティを使用するには、SSL 証明書が IIS に登録されている必要があります。 SSL 証明書がない場合は、IIS を使用してテスト証明書を生成できます。 次に、Web サイトに SSL バインディングを追加し、Web サイトの認証プロパティを構成する必要があります。 最後に、HTTPS を使用するように WCF サービスを構成する必要があります。  
  
### <a name="creating-a-self-signed-certificate"></a>自己署名証明書の作成  
  
1.  インターネット インフォメーション サービス マネージャー (inetmgr.exe) を開き、左側のツリー ビューでコンピューター名を選択します。 画面の右側で [サーバー証明書] を選択します。  
  
     ![IIS マネージャーのホーム画面](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2.  サーバー証明書 ウィンドウでをクリックして、**自己署名証明書を作成しています.** リンクをクリックします。  
  
     ![IIS で証明書に署名自己 &#45; を作成する](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3.  自己署名証明書のフレンドリ名を入力し、クリックして**OK**です。  
  
     ![Self &#45; を作成します。署名証明書ダイアログ](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")  
  
     新しく作成された自己署名証明書の詳細が示されています、**サーバー証明書**ウィンドウです。  
  
     ![サーバー証明書 ウィンドウ](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     生成された証明書が、信頼されたルート証明機関ストアにインストールされます。  
  
### <a name="add-ssl-binding"></a>SSL バインドの追加  
  
1.  インターネット インフォメーション サービス マネージャーでも、展開、**サイト**フォルダーし、**既定の Web サイト**画面の左側にあるツリー ビューでフォルダーです。  
  
2.  クリックして、**バインドしています.** 内のリンク、**アクション**セクションで、ウィンドウの右上の部分にします。  
  
     ![SSL バインディングの追加](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3.  サイト バインド ウィンドウで、**追加**ボタンをクリックします。  
  
     ![サイトのバインド ダイアログ ボックス](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4.  **サイト バインドの追加**作成ダイアログ ボックスで、型とした自己署名証明書のフレンドリ名 (https) を選択します。  
  
     ![サイト バインディングの例](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>SSL の仮想ディレクトリの構成  
  
1.  インターネット インフォメーション サービス マネージャーで、WCF のセキュリティで保護されたサービスが含まれている仮想ディレクトリを選択します。  
  
2.  ウィンドウの中央のウィンドウで選択**SSL 設定**IIS セクションでします。  
  
     ![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3.  SSL 設定 ウィンドウで、選択、 **SSL が必要** チェック ボックス をクリック、**適用**内のリンク、**アクション**画面の右側にあるセクション。  
  
     ![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>HTTP トランスポート セキュリティのための WCF サービスの構成  
  
1.  WCF サービスの Web.config で、次の XML に示すように、トランスポート セキュリティを使用するよう HTTP バインドを構成します。  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2.  次の XML に示すように、サービスとサービス エンドポイントを指定します。  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a>例  
 次は、HTTP トランスポート セキュリティを使用した WCF サービスの web.config ファイルの詳細な例です。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [インターネット インフォメーション サービスのホスティング手順](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [インライン コードを使用した IIS ホスティング](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
