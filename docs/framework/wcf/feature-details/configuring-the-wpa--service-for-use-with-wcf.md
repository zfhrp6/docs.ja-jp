---
title: "Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Windows Communication Foundation で使用するための Windows プロセス アクティブ化サービスを設定する
ここでは、Windows プロセス アクティブ化サービス \(WAS: Windows Process Activation Service\) を [!INCLUDE[wv](../../../../includes/wv-md.md)] で構成して、HTTP ネットワーク プロトコルでは通信しない [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストするために必要な手順について説明します。以降の各セクションで、この構成に関する手順について概説します。  
  
-   必要な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティベーション コンポーネントをインストール \(またはそのインストールを確認\) します。  
  
-   使用するネットワーク プロトコル バインドを含む WAS サイトを作成するか、新しいプロトコル バインドを既存のサイトに追加します。  
  
-   サービスをホストするアプリケーションを作成し、必要なネットワーク プロトコルを使用するようにそのアプリケーションを設定します。  
  
-   非 HTTP エンドポイントを公開する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを構築します。  
  
## 非 HTTP バインドを使用したサイトの構成  
 WAS で非 HTTP バインドを使用するには、サイト バインドを WAS 構成に追加する必要があります。WAS の構成ストアは、%windir%\\system32\\inetsrv\\config ディレクトリにある applicationHost.config ファイルです。この構成ストアは、WAS と IIS 7.0 の両方で共有されます。  
  
 applicationHost.config は、任意の標準テキスト エディター \(メモ帳など\) で開くことが可能な XML テキスト ファイルです。ただし、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] コマンド ライン構成ツール \(appcmd.exe\) の方が、非 HTTP サイトのバインディングの追加には適しています。  
  
 次のコマンドは、appcmd.exe を使用して、既定の Web サイトに net.tcp サイト バインドを追加します \(このコマンドは 1 行で入力します\)。  
  
```  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 このコマンドは、次に示す行を applicationHost.config ファイルに追加することによって、既定の Web サイトに新しい net.tcp バインドを追加します。  
  
```  
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
  
## 非 HTTP プロトコルを使用するためのアプリケーションの設定  
 個々のネットワーク プロトコルは、アプリケーション レベルで有効\/無効を切り替えることができます。次のコマンドは、`Default Web Site` で動作するアプリケーションに対して、HTTP プロトコルと net.tcp プロトコルの両方を有効にする方法を示しています。  
  
```  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 有効にするプロトコルのリストは、ApplicationHost.config に保存されたサイトの XML 構成の \<applicationDefaults\> 要素に設定することもできます。  
  
 次の applicationHost.config からの XML コードは、HTTP プロトコルと非 HTTP プロトコルの両方にバインドされたサイトを示しています。非 HTTP プロトコルのサポートに必要な追加の構成は、コメントで付記されています。  
  
```  
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
  
 非 HTTP アクティブ化の WAS を使用するサービスをアクティブ化しようとしたときに、WAS をインストールおよび構成していない場合、次のエラーが表示されることがあります。  
  
```Output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 このエラーが表示された場合は、非 HTTP アクティブ化の WAS が適切にインストールおよび構成されていることを確認してください。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : WCF アクティブ化コンポーネントをインストールして設定する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## 非 HTTP のアクティブ化で WAS を使用する WCF サービスの構築  
 WAS をインストールして構成する手順 \(「[方法 : WCF アクティブ化コンポーネントをインストールして設定する](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)」を参照\) を実行した後の、アクティブ化で WAS を使用するためのサービスの構成は、IIS でホストされるサービスの構成に似ています。  
  
 WAS によりアクティブ化される [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの構築の詳細な手順については、「[方法 : WAS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)」を参照してください。  
  
## 参照  
 [Windows プロセス アクティブ化サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)