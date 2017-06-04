---
title: "WCF トラブルシューティング クイックスタート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF [WCF], トラブルシューティング"
  - "Windows Communication Foundation [WCF], トラブルシューティング"
ms.assetid: a9ea7a53-f31a-46eb-806e-898e465a4992
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# WCF トラブルシューティング クイックスタート
このトピックでは、WCF クライアントと WCF サービスの開発時に生じるさまざまな既知の問題の一覧を示します。 発生している問題がこの一覧にない場合は、サービスに対してトレースを構成することをお勧めします。 これにより、トレース ファイル ビューアーで表示し、サービス内で発生することがある例外に関する詳細情報を取得できるトレース ファイルが生成されます。 トレースの構成の詳細については、「[トレースの構成](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。 トレース ファイル ビューアーの詳細については、「[サービス トレース ビューアー ツール \(SvcTraceViewer.exe\)](../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)」を参照してください。  
  
1.  [Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 \- Not Found" というエラー メッセージが表示されます](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#bkmk_0)  
  
     HTTP エラー 404.3 \- Not Found 拡張構成により、要求しているページは使用できません。 ページがスクリプトの場合は、ハンドラーを追加します。 ファイルをダウンロードする場合は、MIME マップを追加します。 エラーの詳細: InformationModule StaticFileModule。  
  
2.  [最初の要求の後でクライアントがしばらくアイドル状態になった場合、2 番目の要求で MessageSecurityException を受け取ることがあります。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q1)  
  
3.  [サービスと対話しているクライアントの数が約 10 個になると、サービスが新しいクライアントを拒否し始めます。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q2)  
  
4.  [WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q3)  
  
5.  [サービスとクライアントの動作に問題はないのですが、クライアントが別のコンピューター上にあるときにサービスとクライアントがうまく動作しません。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q4)  
  
6.  [型が例外である場合に FaultException\<Exception\> をスローすると、必ずクライアントで、ジェネリック型ではなく一般的な FaultException 型を受け取ります。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q5)  
  
7.  [応答にデータがない場合、一方向操作と要求\/応答操作が戻る速度がほぼ同じになるようです。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q6)  
  
8.  [サービスで X.509 証明書を使用していますが、System.Security.Cryptography.CryptographicException を受け取ります。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q77)  
  
9. [操作の最初のパラメーターを大文字から小文字に変更したら、クライアントが例外をスローするようになりました。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q88)  
  
10. [トレース ツールの 1 つを使用していますが、EndpointNotFoundException を受け取りました。 どうしてでしょうか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q99)  
  
11. [WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BK_MK99)  
  
 [ベース アドレスについて教えてください。 エンドポイント アドレスとどのように関連していますか。](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md#BKMK_q10)  
  
<a name="bkmk_0"></a>   
## Windows 7 と IIS のインストール後に WCF サービスを参照しようとすると、"HTTP エラー 404.3 \- Not Found" というエラー メッセージが表示されます  
 エラー メッセージの全文は次のとおりです。  
  
 HTTP エラー 404.3 \- Not Found 拡張構成により、要求しているページは使用できません。 ページがスクリプトの場合は、ハンドラーを追加します。 ファイルをダウンロードする場合は、MIME マップを追加します。 エラーの詳細: InformationModule StaticFileModule。  
  
 このエラー メッセージは、\[Windows Communication Foundation HTTP Activation\] がコントロール パネルで明示的に設定されていない場合に表示されます。 これを設定するには、コントロール パネルに移動し、ウィンドウの左下にある \[プログラム\] をクリックします。 \[Windows の機能の有効化または無効化\] をクリックします。 \[Microsoft .NET Framework 3.5.1\] を展開し、\[Windows Communication Foundation HTTP Activation\] をクリックします。  
  
<a name="BKMK_q1"></a>   
## 最初の要求の後でクライアントがしばらくアイドル状態になった場合、2 番目の要求で MessageSecurityException を受け取ることがあります。 どうしてでしょうか。  
 2 番目の要求は、主に次の 2 つの理由から失敗する可能性があります。\(1\) セッションがタイムアウトした。\(2\) サービスをホストしている Web サーバーがリサイクルされている。 最初の理由の場合、セッションはサービスがタイムアウトするまで有効です。 サービスは、サービスのバインディング \(<xref:System.ServiceModel.Channels.Binding.ReceiveTimeout%2A>\) で指定された期間内にクライアントから要求を受信しなかった場合、セキュリティ セッションを終了します。 それ以降のクライアント メッセージでは、<xref:System.ServiceModel.Security.MessageSecurityException> が発生します。 クライアントは、セキュリティで保護されたセッションをサービスとの間に再度確立して、後続のメッセージを送信するか、ステートフルなセキュリティ コンテキスト トークンを使用する必要があります。 また、ステートフルなセキュリティ コンテキスト トークンによって、セキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。 セキュリティで保護されたセッションでのステートフルなセキュリティ コンテキスト トークンの使用方法の[!INCLUDE[crabout](../../../includes/crabout-md.md)]については、「[方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)」を参照してください。 また、セキュリティで保護されたセッションは無効にできます。[\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) バインディングを使用する場合は、`establishSecurityContext` プロパティを `false` に設定して、セキュリティで保護されたセッションを無効にできます。 その他のバインディングでセキュリティで保護されたセッションを無効にするには、カスタム バインディングを作成する必要があります。 カスタム バインディングの作成の詳細については、「[方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)」を参照してください。 このオプションを適用する前に、アプリケーションのセキュリティ要件を確認する必要があります。  
  
<a name="BKMK_q2"></a>   
## サービスと対話しているクライアントの数が約 10 個になると、サービスが新しいクライアントを拒否し始めます。 どうしてでしょうか。  
 既定では、サービスは、10 個の同時セッションだけをサポートできます。 したがって、サービス バインディングでセッションを使用する場合、サービスは 10 個に到達するまで新しいクライアント接続を受け入れますが、その数に到達した後は、現在実行中のセッションの 1 つが終了するまで新しいクライアント接続を拒否します。 いくつかの方法で、より多くのクライアントをサポートできます。 サービスにセッションが必要ない場合、セッションの多いバインディングを使用しないでください  \([!INCLUDE[crdefault](../../../includes/crdefault-md.md)][セッションの使用](../../../docs/framework/wcf/using-sessions.md).\) 他には、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> プロパティの値をユーザーの環境に適した数値に変更することによって、セッションの制限値を増やす方法があります。  
  
<a name="BKMK_q3"></a>   
## WCF アプリケーションの構成ファイル以外の場所からサービス構成を読み込むことはできますか。  
 できます。ただし、<xref:System.ServiceModel.ServiceHost> メソッドをオーバーライドするカスタムの <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> クラスを作成する必要があります。 そのメソッドでは、ベースを呼び出して最初に構成を読み込むことができますが \(標準の構成情報も読み込む場合\)、構成読み込みシステム全体を置き換えることもできます。 アプリケーションの構成ファイルとは異なる構成ファイルから構成を読み込む場合は、構成ファイルを自分で解析して構成を読み込む必要があります。  
  
 <xref:System.ServiceModel.ServiceHostBase.ApplyConfiguration%2A> メソッドをオーバーライドし、エンドポイントを直接構成する方法を次のコード例に示します。  
  
```  
public class MyServiceHost : ServiceHost  
{  
  public MyServiceHost(Type serviceType, params Uri[] baseAddresses)    
    : base(serviceType, baseAddresses)  
  { Console.WriteLine("MyServiceHost Constructor"); }  
  
  protected override void ApplyConfiguration()  
  {  
    string straddress = GetAddress();  
    Uri address = new Uri(straddress);  
    Binding binding = GetBinding();  
    base.AddServiceEndpoint(typeof(IData), binding, address);  
  }  
  
  string GetAddress()  
  { return "http://MyMachine:7777/MyEndpointAddress/"; }  
  
  Binding GetBinding()  
  {  
    WSHttpBinding binding = new WSHttpBinding();  
    binding.Security.Mode = SecurityMode.None;  
    return binding;  
  }  
}  
```  
  
<a name="BKMK_q4"></a>   
## サービスとクライアントの動作に問題はないのですが、クライアントが別のコンピューター上にあるときにサービスとクライアントがうまく動作しません。 どうしてでしょうか。  
 例外によっては、次のようないくつかの問題が存在する可能性があります。  
  
-   場合によっては、クライアントのエンドポイント アドレスを "localhost" ではなくホスト名に変更する必要があります。  
  
-   場合によっては、アプリケーションに対してポートを開く必要があります。 詳細については、SDK サンプルから「[ファイアウォール手順](../../../docs/framework/wcf/samples/firewall-instructions.md)」を参照してください。  
  
-   考えられる他の問題については、サンプル トピックの「[Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/ja-jp/a451a525-e7ce-452d-9da9-620221260113)」を参照してください。  
  
-   クライアントが Windows 資格情報を使用し、例外が <xref:System.ServiceModel.Security.SecurityNegotiationException> の場合、次のように Kerberos を設定します。  
  
    1.  クライアントの App.config ファイルのエンドポイント要素に ID 資格情報を追加します。  
  
        ```  
        <endpoint   
          address="http://MyServer:8000/MyService/"   
          binding="wsHttpBinding"   
          bindingConfiguration="WSHttpBinding_IServiceExample"   
          contract="IServiceExample"   
          behaviorConfiguration="ClientCredBehavior"   
          name="WSHttpBinding_IServiceExample">  
          <identity>  
            <userPrincipalName value="name@corp.contoso.com"/>  
          </identity>  
        </endpoint>  
        ```  
  
    2.  System または NetworkService アカウントで自己ホスト型サービスを実行します。 次のコマンドを実行すると、System アカウントでコマンド ウィンドウを作成できます。  
  
        ```  
        at 12:36  /interactive "cmd.exe"  
        ```  
  
    3.  既定でサービス プリンシパル名 \(SPN\) アカウントを使用するインターネット インフォメーション サービス \(IIS\) でのサービスをホストします。  
  
    4.  SetSPN を使用してドメインに新しい SPN を登録します。 この操作を行えるのは、ドメイン管理者のみです。  
  
 Kerberos プロトコルの[!INCLUDE[crabout](../../../includes/crabout-md.md)]については、「[WCF で使用されるセキュリティの概要](../../../docs/framework/wcf/feature-details/security-concepts-used-in-wcf.md)」および以下を参照してください。  
  
-   [Windows 認証エラーのデバッグ](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
  
-   [Http.sys を使用した Kerberos サービス プリンシパル名の登録](http://go.microsoft.com/fwlink/?LinkId=86943)  
  
-   [Kerberos の説明](http://go.microsoft.com/fwlink/?LinkId=86946)  
  
<a name="BKMK_q5"></a>   
## 型が例外である場合に FaultException\<Exception\> をスローすると、必ずクライアントで、ジェネリック型ではなく一般的な FaultException 型を受け取ります。 どうしてでしょうか。  
 独自のカスタム エラー データ型を作成し、エラー コントラクトで詳細な型としてその型を宣言することをお勧めします。 その理由は、システム指定の例外型を使用すると、次のような状況が起こるためです。  
  
-   サービス指向アプリケーションの長所の 1 つを排除する型依存関係が作成されます。  
  
-   標準的な方法でシリアル化している例外に依存できません。<xref:System.Security.SecurityException> のような例外はまったくシリアル化できない可能性があります。  
  
-   クライアントに内部実装の詳細が公開されます。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][コントラクトおよびサービスのエラーの指定と処理](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
 ただし、アプリケーションをデバッグしている場合、<xref:System.ServiceModel.Description.ServiceDebugBehavior> クラスを使用することによって例外情報をシリアル化して、その情報をクライアントに返すことができます。  
  
<a name="BKMK_q6"></a>   
## 応答にデータがない場合、一方向操作と要求\/応答操作が戻る速度がほぼ同じになるようです。 どうしてでしょうか。  
 操作を一方向に指定すると、操作コントラクトは入力メッセージを受け入れるだけで、出力メッセージを返しません。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、送信データがネットワークに書き込まれるか、例外がスローされたとき、すべてのクライアント呼び出しが戻ります。 一方向操作は同様に動作し、この操作では、サービスが見つからない場合は例外をスローし、サービスがネットワークからのデータの受け入れ準備を完了していない場合はブロックできます。 このため、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では通常、一方向呼び出しは要求\/応答よりも速くクライアントに戻りますが、ネットワーク上でデータの送信速度が遅くなると、一方向操作の速度も要求\/応答操作の速度と同様に遅くなります。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][一方向サービス](../../../docs/framework/wcf/feature-details/one-way-services.md) および [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)。  
  
<a name="BKMK_q77"></a>   
## サービスで X.509 証明書を使用していますが、System.Security.Cryptography.CryptographicException を受け取ります。 どうしてでしょうか。  
 この例外は通常、IIS ワーカー プロセスの実行に使用しているユーザー アカウントを変更すると発生します。 たとえば、[!INCLUDE[wxp](../../../includes/wxp-md.md)] で、既定のユーザー アカウントを使用して Aspnet\_wp.exe を実行しているときにそのアカウントを ASPNET からカスタムのユーザー アカウントに変更した場合、このエラーが発生します。 秘密キーを使用している場合、そのキーを使用するプロセスには、そのキーを格納しているファイルにアクセスするためのアクセス許可が必要になります。  
  
 この場合、秘密キーを格納しているファイルについて、プロセスのアカウントに読み取りアクセス権を与える必要があります。 たとえば、IIS ワーカー プロセスを Bob というアカウントで実行している場合、秘密キーを格納しているファイルへの読み取りアクセス権を Bob に与える必要があります。  
  
 特定の X.509 証明書について、秘密キーを格納しているファイルへのアクセス権を適切なユーザー アカウントに与える方法の[!INCLUDE[crabout](../../../includes/crabout-md.md)]については、「[方法 : X.509 証明書を WCF からアクセス可能にする](../../../docs/framework/wcf/feature-details/how-to-make-x-509-certificates-accessible-to-wcf.md)」を参照してください。  
  
<a name="BKMK_q88"></a>   
## 操作の最初のパラメーターを大文字から小文字に変更したら、クライアントが例外をスローするようになりました。 どうしてでしょうか。  
 操作シグネチャのパラメーター名の値はコントラクトに含まれ、大文字と小文字が区別されます。 ローカル パラメーター名と、クライアント アプリケーションの操作を記述するメタデータを区別する必要がある場合は、<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=fullName> 属性を使用します。  
  
<a name="BKMK_q99"></a>   
## トレース ツールの 1 つを使用していますが、EndpointNotFoundException を受け取りました。 どうしてでしょうか。  
 使用しているトレース ツールが、システム指定の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレース機構でなく、アドレス フィルターの不一致があることを示す <xref:System.ServiceModel.EndpointNotFoundException> を受け取った場合は、<xref:System.ServiceModel.Description.ClientViaBehavior> クラスを使用してメッセージをトレース ユーティリティに送信し、そのユーティリティがそのメッセージをサービス アドレスにリダイレクトするようにする必要があります。<xref:System.ServiceModel.Description.ClientViaBehavior> クラスは、 `Via` アドレス指定ヘッダーを変更して、`To` アドレス指定ヘッダーで示されている最終受信者とは別に、次のネットワーク アドレスを指定します。 ただし、このとき、エンドポイント アドレスは `To` 値の設定に使用されるので変更しないでください。  
  
 次のコード例は、クライアント構成ファイルの例を示しています。  
  
```  
<endpoint   
  address=http://localhost:8000/MyServer/  
  binding="wsHttpBinding"  
  bindingConfiguration="WSHttpBinding_IMyContract"  
  behaviorConfiguration="MyClient"   
  contract="IMyContract"   
  name="WSHttpBinding_IMyContract">  
</endpoint>  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="MyClient">  
      <clientVia viaUri="http://localhost:8001/MyServer/"/>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
<a name="BKMK_q10"></a>   
## ベース アドレスについて教えてください。 エンドポイント アドレスとどのように関連していますか。  
 ベース アドレスとは、<xref:System.ServiceModel.ServiceHost> クラスのルート アドレスです。 既定では、<xref:System.ServiceModel.Description.ServiceMetadataBehavior> クラスをサービス構成に追加する場合、ホストが発行するすべてのエンドポイントの Web サービス記述言語 \(WSDL\) は、HTTP ベース アドレスから取得され、それにメタデータ動作に提供される相対アドレスと "?wsdl" が追加されます。[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] と IIS では、ベース アドレスは仮想ディレクトリに相当します。  
  
## NetTcpBinding を使用したサービス エンドポイントと MEX エンドポイント間でのポートの共有  
 サービスのベース アドレスとして net.tcp:\/\/MyServer:8080\/MyService を指定して次のエンドポイントを追加します。  
  
```xml  
<services>  
      <service name="Microsoft.Samples.NetTcp.CalculatorService">  
        <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
        <endpoint address="mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
      </service>  
    </services>  
  
```  
  
 次の構成スニペットに示すように、NetTcpBinding 設定の 1 つを変更するとします。  
  
```xml  
<bindings>  
      <netTcpBinding>  
        <binding closeTimeout="00:01:00" openTimeout="00:01:00" receiveTimeout="00:10:00" sendTimeout="00:01:00" transactionFlow="false" transferMode="Buffered" transactionProtocol="OleTransactions" hostNameComparisonMode="StrongWildcard" listenBacklog="10" maxBufferPoolSize="524288" maxBufferSize="65536" maxConnections="11" maxReceivedMessageSize="65536">  
          <readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384"/>  
          <reliableSession ordered="true" inactivityTimeout="00:10:00" enabled="false"/>  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign"/>  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
  
```  
  
 "ハンドルされない例外: System.ServiceModel.AddressAlreadyInUseException: IP エンドポイント 0.0.0.0:9000 には既にリスナーがあります。" というエラーが表示されます。このエラーは、次の構成スニペットに示すように、ポートが異なる完全修飾 URL を MEX エンドポイントに対して指定することで回避できます。  
  
```  
<services>  
      <service name="Microsoft.Samples.NetTcp.CalculatorService">  
        <endpoint address="calcsvc" binding ="netTcpBinding" contract="Microsoft.Samples.NetTcp.ICalculator"/>  
        <endpoint address="net.tcp://localhost:9001/servicemodelsamples/mex" binding="mexTcpBinding" contract="IMetadataExchange" />  
      </service>  
    </services>  
  
```  
  
<a name="BK_MK99"></a>   
## WCF SOAP アプリケーションから WCF Web HTTP アプリケーションを呼び出すと、サービスから "405 メソッドは許可されていません" というエラーが返されます  
 WCF サービスから WCF Web HTTP アプリケーション \(<xref:System.ServiceModel.WebHttpBinding> および <xref:System.ServiceModel.Description.WebHttpBehavior> を使用するサービス\) を呼び出すと、"`ハンドルされていない例外: System.ServiceModel.FaultException`1[System.ServiceModel.ExceptionDetail]: リモート サーバーから予期しない応答が返されました: (405) メソッドが許可されていません。`" という例外が発生する場合があります。この例外が発生するのは、WCF が送信 <xref:System.ServiceModel.OperationContext> を受信 <xref:System.ServiceModel.OperationContext> で上書きするためです。 この問題を解決するには、WCF Web HTTP サービス操作内で <xref:System.ServiceModel.OperationContextScope> を作成します。 例:  
  
```ecmascript  
public string Echo(string input)  
        {  
            using (new OperationContextScope(this.InnerChannel))  
            {  
                return base.Channel.Echo(input);  
            }  
        }  
  
```  
  
## 参照  
 [Windows 認証エラーのデバッグ](../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)