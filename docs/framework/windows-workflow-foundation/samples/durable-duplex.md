---
title: "永続的な二重 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 永続的な二重
このサンプルでは、[!INCLUDE[wf](../../../../includes/wf-md.md)] のメッセージング アクティビティを使用して、永続的な双方向メッセージ交換を設定および構成する方法を示します。永続的な双方向メッセージ交換は、長期間行われる双方向メッセージ交換です。メッセージ交換の有効期間は、通信チャネルの有効期間およびサービス インスタンスのメモリ内有効期間よりも長い場合があります。  
  
## サンプルの詳細  
 このサンプルでは、[!INCLUDE[wf2](../../../../includes/wf2-md.md)] を使用して実装された 2 つの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスで、永続的な双方向メッセージ交換を構成します。永続的な双方向メッセージ交換は、MSMQ を介して送信されて [.NET コンテキスト交換](http://go.microsoft.com/fwlink/?LinkID=166059)を使用して関連付けられる 2 つの一方向メッセージで構成されます。これらのメッセージは、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティと <xref:System.ServiceModel.Activities.Receive> メッセージング アクティビティを使用して送信されます。.NET コンテキスト交換は、送信メッセージに対してコールバック アドレスを指定するために使用します。どちらのサービスも Windows プロセス アクティブ化サービス \(WAS\) を使用してホストされ、サービス インスタンスの永続化を有効にするように構成されます。  
  
 1 つ目のサービス \(Service1.xamlx\) は、処理を実行する送信サービス \(Service2.xamlx\) に要求を送信します。処理が完了したら、Service2.xamlx は、処理が完了したことを示す通知を Service1.xamlx に送り返します。ワークフロー コンソール アプリケーションによって、サービスがリッスンするキューが設定され、Service1.xamlx をアクティブ化するために最初の開始メッセージが送信されます。Service1.xamlx は、要求した処理が完了したことを示す通知を Service2.xamlx から受け取ったら、結果を XML ファイルに保存します。コールバック メッセージを待機している間、Service1.xamlx は既定の <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を使用してインスタンスの状態を永続化します。Service2.xamlx は、Service1.xamlx によって要求された処理を完了する一環としてインスタンスの状態を永続化します。  
  
 MSMQ を介して .NET コンテキスト交換を使用するようにサービスを構成するために、<xref:System.ServiceModel.Channels.ContextBindingElement> と <xref:System.ServiceModel.Channels.MsmqTransportBindingElement> から成るカスタム バインディングを使用するように両方のサービスが構成されます。<xref:System.ServiceModel.Channels.ContextBindingElement> ではコールバック アドレスが指定され、カスタム バインディングを使用して送信されるすべてのメッセージのコールバック コンテキスト ヘッダーに含まれます。カスタム バインディングを定義するコード例を次に示します。  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
> [!NOTE]
>  このサンプルで使用するバインディングはセキュリティで保護されていません。アプリケーションを配置するときに、アプリケーションのセキュリティ要件に基づいてバインディングを構成する必要があります。  
  
> [!NOTE]
>  このサンプルで使用するキューはトランザクション キューではありません。トランザクション キューを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メッセージ交換を設定する方法を示したサンプルについては、「[MSMQ アクティベーション](../../../../docs/framework/wcf/samples/msmq-activation.md)」のサンプルを参照してください。  
  
 Service1.xamlx によって Service2.xamlx に送信されるメッセージは、Service2.xamlx のアドレスと前に定義したカスタム バインディングを使用して構成されるクライアント エンドポイントを使用して送信されます。Service2.xamlx から Service1.xamlx へのコールバックは、アドレスが明示的に構成されていないクライアント エンドポイントを使用して送信されます。アドレスは、Service1.xamlx によって送信されるコールバック コンテキストから取得されます。クライアント エンドポイントを定義するコード例を次に示します。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
 このカスタム バインディングを使用するように net.msmq ベース アドレスの既定のプロトコル マッピングを変更することで、このカスタム バインディングを使用するエンドポイントを公開するコード例を次に示します。  
  
```  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
  
```  
  
 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> の動作を両方のサービスに追加して永続性データベースの接続文字列を指定することで、両方のサービスの永続化を有効にするコード例を次に示します。  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
  
```  
  
## システム要件  
 このサンプルには、次のコンポーネントが必要です。  
  
1.  インターネット インフォメーション サービス。  
  
2.  \[Internet Information Services\] \-\> \[IIS 6 と互換性のある管理\] \-\> \[IIS メタベースおよび IIS 6 構成との互換性\]。  
  
3.  \[World Wide Web サービス\] \-\> \[アプリケーション開発機能\] \-\> \[ASP.NET\]。  
  
4.  Microsoft メッセージ キュー \(MSMQ\) サーバー。  
  
#### このサンプルを使用するには  
  
1.  永続性データベースと結果ディレクトリを設定します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
    2.  このサンプルのフォルダーに移動して Setup.cmd を実行します。  
  
2.  仮想アプリケーションを設定します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトから次のコマンドを実行し、ASP.NET を登録します。  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を右クリックして **\[管理者として実行\]** をクリックし、管理者のアクセス許可で [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を実行します。  
  
    3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DurableDuplex.sln ファイルを開きます。  
  
3.  サービス キューを設定します。  
  
    1.  DurableDuplex クライアントを実行するために、F5 キーを押します。  
  
    2.  コマンド プロンプトから `Compmgmt.msc` を実行して、**\[コンピューターの管理\]** コンソールを開きます。  
  
    3.  **\[サービスとアプリケーション\]**、**\[メッセージ キュー\]**、**\[専用キュー\]** の順に展開します。  
  
    4.  durableduplex\/service1.xamlx キューと durableduplex\/service2.xamlx キューを右クリックし、**\[プロパティ\]** をクリックします。  
  
    5.  **\[セキュリティ\]** タブをクリックし、両方のキューで Everyone グループに対して **\[メッセージの受信\]**、**\[メッセージのピーク\]**、および **\[メッセージの送信\]** アクセス許可を与えます。  
  
    6.  インターネット インフォメーション サービス \(IIS\) マネージャーを開きます。  
  
    7.  **\[サーバー\]**、**\[サイト\]**、**\[既定の Web サイト\]**、**\[private\]**、**\[永続的な二重\]** の順に参照し、**\[詳細オプション\]** をクリックします。  
  
    8.  **\[有効なプロトコル\]** を **http,net.msmq** に変更します。  
  
4.  サンプルを実行します。  
  
    1.  http:\/\/localhost\/private\/durableduplex\/service1.xamlx および http:\/\/localhost\/private\/durableduplex\/service2.xamlx を参照し、両方のサービスが実行されていることを確認します。  
  
    2.  F5 キーを押して DurableDuplexClient を実行します。  
  
         永続的な双方向メッセージ交換が完了したら、メッセージ交換の結果を示す result.xml ファイルが C:\\Inbox フォルダーに保存されます。  
  
#### クリーンアップするには \(省略可能\)  
  
1.  Cleanup.cmd を実行します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトを開きます。  
  
    2.  このサンプルのフォルダーに移動して Cleanup.cmd を実行します。  
  
2.  サービスの仮想アプリケーションを削除します。  
  
    1.  コマンド プロンプトから `Inetmgr.exe` を実行して、インターネット インフォメーション サービス \(IIS\) マネージャーを開きます。  
  
    2.  既定の Web サイトを参照して、**private** 仮想ディレクトリを削除します。  
  
3.  このサンプルに対して設定されているキューを削除します。  
  
    1.  コマンド プロンプトから `Compmgmt.msc` を実行して、\[コンピューターの管理\] コンソールを開きます。  
  
    2.  **\[サービスとアプリケーション\]**、**\[メッセージ キュー\]**、**\[専用キュー\]** の順に展開します。  
  
    3.  durableduplex\/service1.xamlx キューと durableduplex\/service2.xamlx キューを削除します。  
  
4.  C:\\Inbox ディレクトリを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`  
  
## 参照