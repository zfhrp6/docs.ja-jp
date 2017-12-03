---
title: "Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a63f9a4e982e4065f55b15ec28be5afbf2d89fcc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a><span data-ttu-id="5d7c0-102">Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する</span><span class="sxs-lookup"><span data-stu-id="5d7c0-102">Configuring the Windows Process Activation Service for Use with Windows Communication Foundation</span></span>
<span data-ttu-id="5d7c0-103">ここでは、Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) を [!INCLUDE[wv](../../../../includes/wv-md.md)] で構成して、HTTP ネットワーク プロトコルでは通信しない [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストするために必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) in [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="5d7c0-104">以降の各セクションで、この構成に関する手順について概説します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="5d7c0-105">必要な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティベーション コンポーネントをインストール (またはそのインストールを確認) します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components required.</span></span>  
  
-   <span data-ttu-id="5d7c0-106">使用するネットワーク プロトコル バインドを含む WAS サイトを作成するか、新しいプロトコル バインドを既存のサイトに追加します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-106">Create a WAS site with the network protocol bindings you wish to use, or add a new protocol binding to an existing site.</span></span>  
  
-   <span data-ttu-id="5d7c0-107">サービスをホストするアプリケーションを作成し、必要なネットワーク プロトコルを使用するようにそのアプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-107">Create an application to host your services and enable that application to use the required network protocols.</span></span>  
  
-   <span data-ttu-id="5d7c0-108">非 HTTP エンドポイントを公開する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構築します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-108">Build a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes a non-HTTP endpoint.</span></span>  
  
## <a name="configuring-a-site-with-non-http-bindings"></a><span data-ttu-id="5d7c0-109">非 HTTP バインドを使用したサイトの構成</span><span class="sxs-lookup"><span data-stu-id="5d7c0-109">Configuring a Site with Non-HTTP bindings</span></span>  
 <span data-ttu-id="5d7c0-110">WAS で非 HTTP バインドを使用するには、サイト バインドを WAS 構成に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-110">To use a non-HTTP binding with WAS, the site binding must be added to the WAS configuration.</span></span> <span data-ttu-id="5d7c0-111">WAS の構成ストアは、%windir%\system32\inetsrv\config ディレクトリにある applicationHost.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-111">The configuration store for WAS is the applicationHost.config file, located in the %windir%\system32\inetsrv\config directory.</span></span> <span data-ttu-id="5d7c0-112">この構成ストアは、WAS と IIS 7.0 の両方で共有されます。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-112">This configuration store is shared by both WAS and IIS 7.0.</span></span>  
  
 <span data-ttu-id="5d7c0-113">applicationHost.config は、任意の標準テキスト エディター (メモ帳など) で開くことが可能な XML テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-113">applicationHost.config is an XML text file that can be opened with any standard text editor (such as Notepad).</span></span> <span data-ttu-id="5d7c0-114">ただし、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] コマンド ライン構成ツール (appcmd.exe) の方が、非 HTTP サイトのバインディングの追加には適しています。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-114">However, the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] command-line configuration tool (appcmd.exe) is the preferred way to add non-HTTP site bindings.</span></span>  
  
 <span data-ttu-id="5d7c0-115">次のコマンドは、appcmd.exe を使用して、既定の Web サイトに net.tcp サイト バインドを追加します (このコマンドは 1 行で入力します)。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-115">The following command adds a net.tcp site binding to the default Web site using appcmd.exe (this command is entered as a single line).</span></span>  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 <span data-ttu-id="5d7c0-116">このコマンドは、次に示す行を applicationHost.config ファイルに追加することによって、既定の Web サイトに新しい net.tcp バインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-116">This command adds the new net.tcp binding to the default Web site by adding the line indicated below to the applicationHost.config file.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a><span data-ttu-id="5d7c0-117">非 HTTP プロトコルを使用するためのアプリケーションの設定</span><span class="sxs-lookup"><span data-stu-id="5d7c0-117">Enabling an Application to Use Non-HTTP Protocols</span></span>  
 <span data-ttu-id="5d7c0-118">有効にするにまたは個々 のネットワーク protocolsat アプリケーション レベルを無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-118">You can enable or disable individual network protocolsat the application level.</span></span> <span data-ttu-id="5d7c0-119">次のコマンドは、`Default Web Site` で動作するアプリケーションに対して、HTTP プロトコルと net.tcp プロトコルの両方を有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-119">The following command illustrates how to enable both the HTTP and net.tcp protocols for an application that runs in the `Default Web Site`.</span></span>  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 <span data-ttu-id="5d7c0-120">有効なプロトコルの一覧設定することもできます、 \<applicationDefaults > ApplicationHost.config に保存されたサイトの XML 構成の要素。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-120">The list of enabled protocols can also be set in the \<applicationDefaults> element of the site’s XML configuration stored in ApplicationHost.config.</span></span>  
  
 <span data-ttu-id="5d7c0-121">次の applicationHost.config からの XML コードは、HTTP プロトコルと非 HTTP プロトコルの両方にバインドされたサイトを示しています。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-121">The following XML code from applicationHost.config illustrates a site bound to both HTTP and non-HTTP protocols.</span></span> <span data-ttu-id="5d7c0-122">非 HTTP プロトコルのサポートに必要な追加の構成は、コメントで付記されています。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-122">The additional configuration required to support non-HTTP protocols is called out with comments.</span></span>  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
    <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
    </application>  
       <bindings>  
            //The following two lines are added by the command.  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile   
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging   
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults   
      applicationPool="DefaultAppPool"   
      //The following line is inserted by the command.  
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 <span data-ttu-id="5d7c0-123">非 HTTP アクティブ化の WAS を使用するサービスをアクティブ化しようとしたときに、WAS をインストールおよび構成していない場合、次のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-123">If you attempt to activate a service using WAS for Non-HTTP activation and you have not installed and configured WAS you may see the following error:</span></span>  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 <span data-ttu-id="5d7c0-124">このエラーが表示された場合は、非 HTTP アクティブ化の WAS が適切にインストールおよび構成されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-124">If you see this error ensure WAS for Non-HTTP Activation is installed and configured properly.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="5d7c0-125">[する方法: インストールして WCF アクティブ化コンポーネントを構成する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-125"> [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a><span data-ttu-id="5d7c0-126">非 HTTP のアクティブ化で WAS を使用する WCF サービスの構築</span><span class="sxs-lookup"><span data-stu-id="5d7c0-126">Building a WCF Service That Uses WAS for Non-HTTP activation</span></span>  
 <span data-ttu-id="5d7c0-127">一度インストールし、WAS を構成する手順を実行すると (を参照してください[する方法: WCF アクティブ化コンポーネントの構成のインストールと](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md))、ライセンス認証は IIS でホストされているサービスを構成するように WAS を使用するサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-127">Once you perform the steps to install and configure WAS (see [How to: Install and Configure WCF Activation Components](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), configuring a service to use WAS for activation is similar to configuring a service that is hosted in IIS.</span></span>  
  
 <span data-ttu-id="5d7c0-128">WAS アクティブ化の構築に関する詳細な手順について[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サービスを参照してください[する方法: WAS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d7c0-128">For detailed instructions about building a WAS-activated [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7c0-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d7c0-129">See Also</span></span>  
 [<span data-ttu-id="5d7c0-130">Windows プロセス アクティブ化サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="5d7c0-130">Hosting in Windows Process Activation Service</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)  
 [<span data-ttu-id="5d7c0-131">Windows Server App Fabric のホスティング機能</span><span class="sxs-lookup"><span data-stu-id="5d7c0-131">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
