---
title: IIS でホストされる WCF サービスに SSL を構成する方法
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: e739eb47611e5b73e7f1d62191a5aa61ad77abe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493498"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="1ec8e-102">IIS でホストされる WCF サービスに SSL を構成する方法</span><span class="sxs-lookup"><span data-stu-id="1ec8e-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="1ec8e-103">ここでは、HTTP トランスポート セキュリティを使用するように IIS でホストされる WCF サービスをセットアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="1ec8e-104">HTTP トランスポート セキュリティを使用するには、SSL 証明書が IIS に登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="1ec8e-105">SSL 証明書がない場合は、IIS を使用してテスト証明書を生成できます。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="1ec8e-106">次に、Web サイトに SSL バインディングを追加し、Web サイトの認証プロパティを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="1ec8e-107">最後に、HTTPS を使用するように WCF サービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="1ec8e-108">自己署名証明書の作成</span><span class="sxs-lookup"><span data-stu-id="1ec8e-108">Creating a Self-Signed Certificate</span></span>  
  
1.  <span data-ttu-id="1ec8e-109">インターネット インフォメーション サービス マネージャー (inetmgr.exe) を開き、左側のツリー ビューでコンピューター名を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="1ec8e-110">画面の右側で [サーバー証明書] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="1ec8e-111">![IIS マネージャーのホーム画面](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-111">![IIS Manager Home Screen](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2.  <span data-ttu-id="1ec8e-112">サーバー証明書 ウィンドウでをクリックして、**自己署名証明書を作成しています.**</span><span class="sxs-lookup"><span data-stu-id="1ec8e-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="1ec8e-113">リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-113">Link.</span></span>  
  
     <span data-ttu-id="1ec8e-114">![自己を作成する&#45;署名入り証明書を IIS に](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-114">![Creating a self&#45;signed certificate with IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3.  <span data-ttu-id="1ec8e-115">自己署名証明書のフレンドリ名を入力し、クリックして**OK**です。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="1ec8e-116">![自動作成&#45;署名証明書ダイアログ](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-116">![Create Self&#45;Signed Certificate Dialog](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="1ec8e-117">新しく作成された自己署名証明書の詳細が示されています、**サーバー証明書**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="1ec8e-118">![サーバー証明書 ウィンドウ](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-118">![Server Certificate Window](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="1ec8e-119">生成された証明書が、信頼されたルート証明機関ストアにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="1ec8e-120">SSL バインドの追加</span><span class="sxs-lookup"><span data-stu-id="1ec8e-120">Add SSL Binding</span></span>  
  
1.  <span data-ttu-id="1ec8e-121">インターネット インフォメーション サービス マネージャーでも、展開、**サイト**フォルダーし、**既定の Web サイト**画面の左側にあるツリー ビューでフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2.  <span data-ttu-id="1ec8e-122">クリックして、**バインドしています.**</span><span class="sxs-lookup"><span data-stu-id="1ec8e-122">Click the **Bindings….**</span></span> <span data-ttu-id="1ec8e-123">内のリンク、**アクション**セクションで、ウィンドウの右上の部分にします。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="1ec8e-124">![SSL バインディングの追加](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-124">![Adding an SSL binding](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3.  <span data-ttu-id="1ec8e-125">サイト バインド ウィンドウで、**追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="1ec8e-126">![サイトのバインド ダイアログ ボックス](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-126">![Site Bindings Dialog](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4.  <span data-ttu-id="1ec8e-127">**サイト バインドの追加**作成ダイアログ ボックスで、型とした自己署名証明書のフレンドリ名 (https) を選択します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="1ec8e-128">![サイト バインディングの例](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-128">![Site binding example](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="1ec8e-129">SSL の仮想ディレクトリの構成</span><span class="sxs-lookup"><span data-stu-id="1ec8e-129">Configure Virtual Directory for SSL</span></span>  
  
1.  <span data-ttu-id="1ec8e-130">インターネット インフォメーション サービス マネージャーで、WCF のセキュリティで保護されたサービスが含まれている仮想ディレクトリを選択します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2.  <span data-ttu-id="1ec8e-131">ウィンドウの中央のウィンドウで選択**SSL 設定**IIS セクションでします。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="1ec8e-132">![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-132">![SSL Settings for virtual directory](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3.  <span data-ttu-id="1ec8e-133">SSL 設定 ウィンドウで、選択、 **SSL が必要** チェック ボックス をクリック、**適用**内のリンク、**アクション**画面の右側にあるセクション。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="1ec8e-134">![仮想ディレクトリの SSL 設定](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="1ec8e-134">![Virtual directory SSL settings](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="1ec8e-135">HTTP トランスポート セキュリティのための WCF サービスの構成</span><span class="sxs-lookup"><span data-stu-id="1ec8e-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1.  <span data-ttu-id="1ec8e-136">WCF サービスの Web.config で、次の XML に示すように、トランスポート セキュリティを使用するよう HTTP バインドを構成します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2.  <span data-ttu-id="1ec8e-137">次の XML に示すように、サービスとサービス エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1ec8e-138">例</span><span class="sxs-lookup"><span data-stu-id="1ec8e-138">Example</span></span>  
 <span data-ttu-id="1ec8e-139">次は、HTTP トランスポート セキュリティを使用した WCF サービスの web.config ファイルの詳細な例です。</span><span class="sxs-lookup"><span data-stu-id="1ec8e-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1ec8e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ec8e-140">See Also</span></span>  
 [<span data-ttu-id="1ec8e-141">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="1ec8e-141">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 [<span data-ttu-id="1ec8e-142">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="1ec8e-142">Internet Information Service Hosting Instructions</span></span>](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)  
 [<span data-ttu-id="1ec8e-143">インターネット インフォメーション サービス ホスティングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="1ec8e-143">Internet Information Services Hosting Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [<span data-ttu-id="1ec8e-144">インライン コードを使用した IIS ホスティング</span><span class="sxs-lookup"><span data-stu-id="1ec8e-144">IIS Hosting Using Inline Code</span></span>](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
