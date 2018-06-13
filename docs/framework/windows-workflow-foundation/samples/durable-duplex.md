---
title: 永続的な二重
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 3df5ba962ef33594df1eaebc20789fa9e2d35244
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809428"
---
# <a name="durable-duplex"></a>永続的な二重
このサンプルを設定して、Windows Workflow Foundation (WF)、メッセージング アクティビティを使用して永続的な双方向メッセージ交換を構成する方法を示します。 永続的な双方向メッセージ交換は、長期間行われる双方向メッセージ交換です。 メッセージ交換の有効期間は、通信チャネルの有効期間およびサービス インスタンスのメモリ内有効期間よりも長い場合があります。  
  
## <a name="sample-details"></a>サンプルの詳細  
 このサンプルでは、Windows Workflow Foundation を使用して実装されている 2 つの Windows Communication Foundation (WCF) サービスは、永続的な双方向メッセージ交換に構成されます。 永続的な双方向メッセージ交換が MSMQ 経由で送信され、関連するを使用して 2 つの一方向のメッセージから構成される[.NET コンテキスト交換](http://go.microsoft.com/fwlink/?LinkID=166059)です。 これらのメッセージは、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティと <xref:System.ServiceModel.Activities.Receive> メッセージング アクティビティを使用して送信されます。 .NET コンテキスト交換は、送信メッセージに対してコールバック アドレスを指定するために使用します。 どちらのサービスも Windows プロセス アクティブ化サービス (WAS) を使用してホストされ、サービス インスタンスの永続化を有効にするように構成されます。  
  
 1 つ目のサービス (Service1.xamlx) は、処理を実行する送信サービス (Service2.xamlx) に要求を送信します。 処理が完了したら、Service2.xamlx は、処理が完了したことを示す通知を Service1.xamlx に送り返します。 ワークフロー コンソール アプリケーションによって、サービスがリッスンするキューが設定され、Service1.xamlx をアクティブ化するために最初の開始メッセージが送信されます。 Service1.xamlx は、要求した処理が完了したことを示す通知を Service2.xamlx から受け取ったら、結果を XML ファイルに保存します。 コールバック メッセージを待機している間、Service1.xamlx は既定の <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> を使用してインスタンスの状態を永続化します。 Service2.xamlx は、Service1.xamlx によって要求された処理を完了する一環としてインスタンスの状態を永続化します。  
  
 MSMQ を介して .NET コンテキスト交換を使用するようにサービスを構成するために、<xref:System.ServiceModel.Channels.ContextBindingElement> と <xref:System.ServiceModel.Channels.MsmqTransportBindingElement> から成るカスタム バインディングを使用するように両方のサービスが構成されます。 <xref:System.ServiceModel.Channels.ContextBindingElement> ではコールバック アドレスが指定され、カスタム バインディングを使用して送信されるすべてのメッセージのコールバック コンテキスト ヘッダーに含まれます。 カスタム バインディングを定義するコード例を次に示します。  
  
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
>  このサンプルで使用するバインディングはセキュリティで保護されていません。 アプリケーションを配置するときに、アプリケーションのセキュリティ要件に基づいてバインディングを構成する必要があります。  
  
> [!NOTE]
>  このサンプルで使用するキューはトランザクション キューではありません。 トランザクション キューを使用して WCF メッセージの交換を設定する方法を示すサンプルについては、次を参照してください。、 [MSMQ アクティブ化](../../../../docs/framework/wcf/samples/msmq-activation.md)サンプルです。  
  
 Service1.xamlx によって Service2.xamlx に送信されるメッセージは、Service2.xamlx のアドレスと前に定義したカスタム バインドを使用して構成されるクライアント エンドポイントを使用して送信されます。 Service2.xamlx から Service1.xamlx へのコールバックは、アドレスが明示的に構成されていないクライアント エンドポイントを使用して送信されます。アドレスは、Service1.xamlx によって送信されるコールバック コンテキストから取得されます。 クライアント エンドポイントを定義するコード例を次に示します。  
  
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
  
```xml  
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
  
## <a name="system-requirements"></a>システム要件  
 このサンプルには、次のコンポーネントが必要です。  
  
1.  インターネット インフォメーション サービス。  
  
2.  [Internet Information Services] -> [IIS 6 と互換性のある管理] -> [IIS メタベースおよび IIS 6 構成との互換性]。  
  
3.  [World Wide Web サービス] -> [アプリケーション開発機能] -> [ASP.NET]。  
  
4.  Microsoft メッセージ キュー (MSMQ) サーバー。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  永続性データベースと結果ディレクトリを設定します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
    2.  このサンプルのフォルダーに移動して Setup.cmd を実行します。  
  
2.  仮想アプリケーションを設定します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] コマンド プロンプトから次のコマンドを実行し、ASP.NET を登録します。  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  実行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を右クリックして、管理者権限を持つ[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]を選択して**管理者として実行**です。  
  
    3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、DurableDuplex.sln ファイルを開きます。  
  
3.  サービス キューを設定します。  
  
    1.  DurableDuplex クライアントを実行するために、F5 キーを押します。  
  
    2.  開く、**コンピューターの管理**コンソールを実行して`Compmgmt.msc`コマンド プロンプトからです。  
  
    3.  展開**サービスとアプリケーション**、**メッセージ キュー**です。 **専用キュー**です。  
  
    4.  Durableduplex/service1.xamlx キューと durableduplex/service2.xamlx キューを右クリックし **プロパティ**です。  
  
    5.  選択、**セキュリティ**でき、タブ**Everyone メッセージの受信**、**メッセージのピーク**と**メッセージの送信**両方のキューのアクセス許可。  
  
    6.  インターネット インフォメーション サービス (IIS) マネージャーを開きます。  
  
    7.  参照**サーバー**、**サイト**、**既定の Web サイト**、**プライベート**、**永続的な二重**を選択**Advanced Options**です。  
  
    8.  変更、**有効なプロトコル**に**http, net.msmq**です。  
  
4.  サンプルを実行します。  
  
    1.  参照http://localhost/private/durableduplex/service1.xamlxとhttp://localhost/private/durableduplex/service2.xamlxを両方のサービスが実行されていることを確認します。  
  
    2.  F5 キーを押して DurableDuplexClient を実行します。  
  
         永続的な双方向メッセージ交換が完了したら、メッセージ交換の結果を示す result.xml ファイルが C:\Inbox フォルダーに保存されます。  
  
#### <a name="to-cleanup-optional"></a>クリーンアップするには (省略可能)  
  
1.  Cleanup.cmd を実行します。  
  
    1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] のコマンド プロンプトを開きます。  
  
    2.  このサンプルのフォルダーに移動して Cleanup.cmd を実行します。  
  
2.  サービスの仮想アプリケーションを削除します。  
  
    1.  実行して、インターネット インフォメーション サービス (IIS) マネージャーを開く`Inetmgr.exe`コマンド プロンプトからです。  
  
    2.  既定の Web サイトを参照し、削除、**プライベート**仮想ディレクトリです。  
  
3.  このサンプルに対して設定されているキューを削除します。  
  
    1.  実行して、コンピューターの管理コンソールを開きます`Compmgmt.msc`コマンド プロンプトからです。  
  
    2.  展開**サービスとアプリケーション**、**メッセージ キュー**、**専用キュー**です。  
  
    3.  durableduplex/service1.xamlx キューと durableduplex/service2.xamlx キューを削除します。  
  
4.  C:\Inbox ディレクトリを削除します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`