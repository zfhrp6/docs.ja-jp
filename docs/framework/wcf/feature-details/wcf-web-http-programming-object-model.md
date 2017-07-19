---
title: "WCF Web HTTP プログラミング オブジェクト モデル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# WCF Web HTTP プログラミング オブジェクト モデル
WCF Web HTTP プログラミング モデルを使用すると、開発者は基本 HTTP 要求を使用して [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web サービスを公開できるようになり、SOAP は必要ありません。  WCF WEB HTTP プログラミング モデルは、既存の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張モデルに基づいて構築されます。  Web HTTP プログラミング モデルでは、次のクラスが定義されます。  
  
 **プログラミング モデル**  
  
-   <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
-   <xref:System.ServiceModel.Web.WebGetAttribute>  
  
-   <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
-   <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **チャネルおよびディスパッチャー インフラストラクチャ**  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
-   <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **ユーティリティ クラスと機能拡張ポイント**  
  
-   <xref:System.UriTemplate>  
  
-   <xref:System.UriTemplateTable>  
  
-   <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
-   <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用された場合に、構成ファイル内の ASP.NET 出力キャッシュ プロファイルを示します。この構成ファイルを使用して ASP .NET 出力キャッシュに操作の応答がキャッシュされます。  このプロパティが受け取るパラメーターは 1 つ \(構成ファイルでキャッシュ設定を指定するキャッシュ プロファイル名\) だけです。  
  
## WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> 属性は、サービス操作を HTTP GET 要求に応答する操作としてマークするために使用されます。  メタデータを操作の説明に追加する受信操作の動作です \(<xref:System.ServiceModel.Description.IOperationBehavior> メソッドは何の処理も行いません\)。  このメタデータを操作の説明で検索する動作 \(特に <xref:System.ServiceModel.Description.WebHttpBehavior>\) がサービスの動作コレクションに追加されていない場合は、<xref:System.ServiceModel.Web.WebGetAttribute> を適用しても機能しません。  <xref:System.ServiceModel.Web.WebGetAttribute> 属性には、次の表に示すパラメーターをオプションで指定できます。  
  
|パラメーター|説明|  
|------------|--------|  
|`BodyStyle`|属性が適用されているサービス操作との間で送受信される要求と応答をラップするかどうかを制御します。|  
|`RequestFormat`|要求メッセージの書式設定方法を制御します。|  
|`ResponseFormat`|応答メッセージの書式設定方法を制御します。|  
|`UriTemplate`|属性が適用されているサービス操作にマップされた HTTP 要求を制御する URI テンプレートを指定します。|  
  
## WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> クラスは、<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> を使用して、XML、JSON、および生のバイナリ データのサポートを組み込みます。  これは、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、および <xref:System.ServiceModel.WebHttpSecurity> オブジェクトから構成されています。  <xref:System.ServiceModel.WebHttpBinding> は、<xref:System.ServiceModel.Description.WebHttpBehavior> と組み合わせて使用するようにデザインされています。  
  
## WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性は <xref:System.ServiceModel.Web.WebGetAttribute> 属性によく似ていますが、サービス操作を GET 以外の HTTP 要求に応答する操作としてマークするために使用されます。  メタデータを操作の説明に追加する受信操作の動作です \(<xref:System.ServiceModel.Description.IOperationBehavior> メソッドは何の処理も行いません\)。  このメタデータを操作の説明で検索する動作 \(特に <xref:System.ServiceModel.Description.WebHttpBehavior>\) がサービスの動作コレクションに追加されていない場合は、<xref:System.ServiceModel.Web.WebInvokeAttribute> を適用しても機能しません。  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性には、次の表に示すパラメーターをオプションで指定できます。  
  
|パラメーター|説明|  
|------------|--------|  
|`BodyStyle`|属性が適用されているサービス操作との間で送受信される要求と応答をラップするかどうかを制御します。|  
|`Method`|サービス操作がマップされる HTTP メソッドを指定します。|  
|`RequestFormat`|要求メッセージの書式設定方法を制御します。|  
|`ResponseFormat`|応答メッセージの書式設定方法を制御します。|  
|`UriTemplate`|属性が適用されているサービス操作にマップされた GET 要求を制御する URI テンプレートを指定します。|  
  
## UriTemplate  
 <xref:System.UriTemplate> クラスでは、構造が似ている URI のセットを定義できます。  テンプレートは、パスとクエリの 2 つの部分から構成されています。  パスは、スラッシュ \(\/\) で区切られた一連のセグメントから構成されています。  各セグメントには、リテラル値、変数値 \(中かっこ \[{ }\] 内に記述。必ず 1 つのセグメントと一致するよう制約\)、またはワイルドカード \(アスタリスク \[\*\] で記述。"残りのパス" に一致する\) を指定することができます。ワイルドカードは、パスの最後に指定する必要があります。  クエリ式は、すべて省略することができます。  存在する場合、クエリ式は順序なしの一連の名前\/値ペアを指定します。  クエリ式の要素には、リテラル ペア \(?x\=2\) または変数ペア \(?x\={*value*}\) を指定できます。  対になっていない値は使用できません。  <xref:System.UriTemplate> は、特定の URI や URI のグループをサービス操作にマップするために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP プログラミング モデルによって内部的に使用されます。  
  
## UriTemplateTable  
 <xref:System.UriTemplateTable> クラスは、開発者が選択したオブジェクトにバインドされた <xref:System.UriTemplate> オブジェクトの結合セットを表します。  これにより、セット内のテンプレートと候補 URI \(Uniform Resource Identifier\) を照合し、一致したテンプレートに関連付けられているデータを取得することができます。  <xref:System.UriTemplateTable> は、特定の URI や URI のグループをサービス操作にマップするために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP プログラミング モデルによって内部的に使用されます。  
  
## WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> は <xref:System.ServiceModel.ServiceHost> を拡張するため、SOAP 以外の Web スタイル サービスを容易にホストできます。  <xref:System.ServiceModel.Web.WebServiceHost> では、サービスの説明にエンドポイントが見つからない場合、サービスのベース アドレスに既定のエンドポイントを自動的に作成します。  既定の HTTP エンドポイントを作成するときに、<xref:System.ServiceModel.Web.WebServiceHost> は、HTTP ヘルプ ページと Web サービス記述言語 \(WSDL\) GET 機能を無効にして、メタデータ エンドポイントが既定の HTTP エンドポイントに干渉しないようにします。  また、<xref:System.ServiceModel.Web.WebServiceHost> は、<xref:System.ServiceModel.WebHttpBinding> を使用するすべてのエンドポイントに必要な <xref:System.ServiceModel.Description.WebHttpBehavior> がアタッチされるようにもします。  最後に、<xref:System.ServiceModel.Web.WebServiceHost> は、エンドポイントのバインディングを、安全な仮想ディレクトリで使用するときに、関連付けられたインターネット インフォメーション サービス \(IIS\) のセキュリティ設定と連携して動作するよう自動的に構成します。  
  
## WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> クラスは、サービスがインターネット インフォメーション サービス \(IIS\) または Windows プロセス アクティブ化サービス \(WAS\) でホストされている場合に、<xref:System.ServiceModel.Web.WebServiceHost> を動的に作成するために使用されます。  ホスト アプリケーションが <xref:System.ServiceModel.Web.WebServiceHost> をインスタンス化する自己ホスト型サービスとは異なり、IIS または WAS でホストされているサービスは、このクラスを使用してサービスの <xref:System.ServiceModel.Web.WebServiceHost> を作成します。  [CreateServiceHost\(Type, Uri\<xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> メソッドは、サービスの受信要求の受信時に呼び出されます。  
  
## WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> クラスは、必要なフォーマッタ、操作セレクターなど、サービス モデル レイヤーで Web スタイル サービスをサポートするために必要な内容を提供します。  このパラメーターは \(<xref:System.ServiceModel.WebHttpBinding> と共に使用される\) エンドポイントの動作として実装され、これにより、フォーマッタと操作セレクターを各エンドポイントに指定できるようになり、さらに、同じサービス実装で SOAP エンドポイントと POX エンドポイントの両方を公開できるようになります。  
  
### WebHttpBehavior の拡張  
 <xref:System.ServiceModel.Description.WebHttpBehavior> は、仮想メソッド <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、および <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29> を使用して拡張できます。  開発者は、<xref:System.ServiceModel.Description.WebHttpBehavior> から派生クラスを作成し、そのメソッドをオーバーライドして既定の動作をカスタマイズすることができます。  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> は、<xref:System.ServiceModel.Description.WebHttpBehavior> 拡張の一例です。  <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> によって、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] エンドポイントでブラウザー ベースの ASP.NET AJAX クライアントから HTTP 要求を受信できるようになります。  「[HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)」はこの機能拡張ポイントの使用例です。  
  
> [!WARNING]
>  <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> を使用する場合、<xref:System.UriTemplate> は、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性内でサポートされません。  
  
## WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> クラスは、<xref:System.UriTemplate> クラスおよび <xref:System.UriTemplateTable> クラスを使用して、サービス操作に対して呼び出しをディスパッチします。  
  
## 互換性  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP プログラミング モデルでは、SOAP ベースのメッセージを使用しないため、WS\-\* プロトコルをサポートしていません。  ただし、SOAP を使用するエンドポイントと SOAP を使用しないその他のエンドポイントの 2 つの異なるエンドポイントを使用して、同じコントラクトを公開できます。  例については、「[方法 : コントラクトを SOAP クライアントおよび Web クライアントに公開する](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)」を参照してください。  
  
## セキュリティ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP プログラミング モデルでは WS\-\* プロトコルがサポートされないため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP プログラミング モデルで構築された Web サービスを保護するには、SSL を使用してサービスを公開するしかありません。  [!INCLUDE[iisver](../../../../includes/iisver-md.md)] を使用した SSL の設定の[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 「[IIS で SSL を実装する方法](http://go.microsoft.com/fwlink/?LinkId=131613)」を参照してください。  
  
## 参照  
 <xref:System.ServiceModel.WebHttpBinding>   
 <xref:System.ServiceModel.Web.WebGetAttribute>   
 <xref:System.ServiceModel.Web.WebInvokeAttribute>   
 <xref:System.ServiceModel.Description.WebHttpBehavior>   
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>   
 [WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)