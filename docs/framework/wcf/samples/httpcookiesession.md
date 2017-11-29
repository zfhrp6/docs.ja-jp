---
title: HttpCookieSession
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ea032f7284884d842916d6019f7df9e66d8b4e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="httpcookiesession"></a>HttpCookieSession
このサンプルでは、カスタム プロトコル チャネルを作成し、セッション管理用の HTTP クッキーを使用する方法を示します。 このチャネルは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスと ASMX クライアント間の通信、または [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと ASMX サービス間の通信を有効にします。  
  
 クライアントがセッション ベースの ASMX Web サービス内で Web メソッドを呼び出すと、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] エンジンは次の処理を行います。  
  
-   一意の ID (セッション ID) を生成します。  
  
-   セッション オブジェクトを生成し、一意の ID に関連付けます。  
  
-   一意の IDを Set-Cookie HTTP 応答ヘッダーに追加し、クライアントに送信します。  
  
-   送信されるセッション ID に基づき、以降の呼び出しでクライアントを識別します。  
  
 クライアントは、サーバーに対する以降の要求にこのセッション ID を含めます。 サーバーはクライアントのセッション ID を使用して、現在の HTTP コンテキストに適切なセッション オブジェクトを読み込みます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>HttpCookieSession チャネルのメッセージ交換パターン  
 このサンプルでは、ASMX などのシナリオのセッションを有効にします。 チャネル スタックの一番下には、<xref:System.ServiceModel.Channels.IRequestChannel> と <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする HTTP トランスポートがあります。 これはチャネルのジョブで、より高いレベルのチャネル スタックにセッションを提供します。 このサンプルでは、セッションをサポートする 2 つのチャネル (<xref:System.ServiceModel.Channels.IRequestSessionChannel> および <xref:System.ServiceModel.Channels.IReplySessionChannel>) を実装します。  
  
## <a name="service-channel"></a>サービス チャネル  
 このサンプルでは、`HttpCookieReplySessionChannelListener` クラスでサービス チャネルを提供します。 このクラスは <xref:System.ServiceModel.Channels.IChannelListener> インターフェイスを実装し、チャネル スタックの低いレベルにある <xref:System.ServiceModel.Channels.IReplyChannel> チャネルを <xref:System.ServiceModel.Channels.IReplySessionChannel> に変換します。 このプロセスは、次の部分に分かれています。  
  
-   チャネル リスナが開かれると、チャネル リスナは内部リスナの内部チャネルを受け入れます。 内部リスナはデータグラム リスナであり、受け入れられたチャネルの有効期間は内部リスナの有効期間から切り離されるため、次のように、内部リスナを閉じて内部チャネルの保持のみを行うことができます。  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   チャネル リスナを開くプロセスが完了したら、次のようにメッセージ ループをセットアップし、内部チャネルからメッセージを受信します。  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   メッセージが到着したら、サービス チャネルはセッション識別子を調べ、非多重化を行って適切なセッション チャネルに変換します。 このチャネル リスナは、セッション識別子をセッション チャネル インスタンスにマップするディクショナリを保持します。  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` クラスは、<xref:System.ServiceModel.Channels.IReplySessionChannel> を実装しています。 より高いレベルのチャネル スタックは <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> メソッドを呼び出し、このセッションの要求を読み込みます。 各セッション チャネルにはプライベート メッセージ キューがあり、サービス チャネルによって設定されます。  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 ユーザーが <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> メソッドを呼び出したときに、このメッセージ キューにメッセージがない場合は、チャネルは指定された時間分待機した後にシャットダウンします。 これにより、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 以外のクライアント用に作成されたセッション チャネルがクリーンアップされます。  
  
 `channelMapping` を使用して `ReplySessionChannels` を追跡します。受け入れられたすべてのチャネルが閉じられた後で、基になる `innerChannel` を閉じます。 この方法により、`HttpCookieReplySessionChannel` は `HttpCookieReplySessionChannelListener` の有効期間を過ぎても存在できます。 また、リスナのガベージ コレクトは気にする必要はありません。受け入れられたチャネルは、`OnClosed` コールバックを介してそのチャネルのリスナへの参照を保持するためです。  
  
## <a name="client-channel"></a>クライアント チャネル  
 対応するクライアント チャネルは、`HttpCookieSessionChannelFactory` クラスにあります。 チャネルの作成中、チャネル ファクトリは内部要求チャネルを `HttpCookieRequestSessionChannel` でラップします。 `HttpCookieRequestSessionChannel` クラスは、基になる要求チャネルへの呼び出しを転送します。 クライアントがプロキシを閉じると、`HttpCookieRequestSessionChannel` はチャネルが閉じられようとしていることを示すメッセージをサービスに送信します。 そのため、サービス チャネル スタックは、使用中のセッション チャネルを正常にシャットダウンできます。  
  
## <a name="binding-and-binding-element"></a>バインディングとバインディング要素  
 サービス チャネルおよびクライアント チャネルを作成した後の次の手順は、それらのチャネルを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムに統合することです。 チャネルは、バインディングとバインディング要素を介して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に公開されます。 バインディングは、1 つまたは複数のバインディング要素で構成されています。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、いくつかのシステム定義バインディングが用意されています。たとえば、BasicHttpBinding や WSHttpBinding などがあります。 `HttpCookieSessionBindingElement` クラスには、バインディング要素の実装が含まれています。 この実装によってチャネル リスナとチャネル ファクトリの作成メソッドがオーバーライドされ、必要なチャネル リスナまたはチャネル ファクトリがインスタンス化されます。  
  
 このサンプルでは、サービスの説明のポリシー アサーションを使用します。 これにより、サンプルのチャネルの要件を、そのサービスを利用できる他のクライアントに公開できます。 たとえば、このバインディング要素はポリシー アサーションを公開し、セッションがサポートされていることを潜在的なクライアントに通知します。 このサンプルでは、バインディング要素の構成で `ExchangeTerminateMessage` プロパティが有効になっています。そのため、サービスで余分なメッセージ交換アクションがサポートされ、セッションでのメッセージ交換が終了されることを示すために必要なアサーションが追加されます。 その後、クライアントはこのアクションを使用できます。 `HttpCookieSessionBindingElement` から作成されたポリシー アサーションを、次の WSDL コードに示します。  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `HttpCookieSessionBinding` クラスは、システム指定のバインディング要素を使用する定義済みバインディングです。  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>構成システムへのチャネルの追加  
 このサンプルでは、構成を使用してサンプル チャネルを公開する 2 つのクラスを提供します。 1 つ目のクラスは、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement> の `HttpCookieSessionBindingElement` です。 実装の大部分は `HttpCookieSessionBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。 `HttpCookieSessionBindingConfigurationElement` には、`HttpCookieSessionBindingElement` のプロパティに対応するプロパティがあります。  
  
### <a name="binding-element-extension-section"></a>要素拡張セクションのバインディング  
 セクション `HttpCookieSessionBindingElementSection` は <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> で、`HttpCookieSessionBindingElement` を構成システムに公開します。 構成セクション名をいくつかオーバーライドして、バインディング要素の種類とバインディング要素の作成方法が定義されます。 その後、次のようにして拡張セクションを構成ファイルに登録できます。  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a>テスト コード  
 このサンプルのトランスポートを使用するテスト コードは、クライアント ディレクトリとサービス ディレクトリで使用できます。 2 つのテストで構成されます — 1 つのテストを使用するバインディングを使用して`allowCookies`'éý'`true`クライアントにします。 2 つ目のテストは、バインディングで明示的なシャットダウン (メッセージ交換の終了) を有効にします。  
  
 このサンプルを実行すると、次の出力が表示されます。  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
3.  指示に従って、ソリューションをビルドする[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
## <a name="see-also"></a>関連項目
