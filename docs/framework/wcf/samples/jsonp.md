---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9002597ef662c78b6519ab0c04700cddf7ee3714
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="jsonp"></a>JSONP
このサンプルでは、WCF REST サービスの JSONP (JSON with Padding) をサポートする方法を示します。 JSONP とは、現在のドキュメントでスクリプト タグを生成してドメイン間スクリプトを呼び出す際に使用される変換です。 結果は、指定したコールバック関数で返されます。 JSONP は、`<script src="http://..." >` などのタグで任意のドメインからのスクリプトを評価でき、このようなタグによって取得されたスクリプトを既に他の関数が定義されている範囲で評価するという考えに基づいています。  
  
## <a name="demonstrates"></a>使用例  
 JSONP によるドメイン間スクリプト。  
  
## <a name="discussion"></a>説明  
 このサンプルには、ブラウザーで表示された後にスクリプト ブロックを動的に追加する Web ページが含まれています。 このスクリプト ブロックは、`GetCustomer` 操作を 1 つ持つ WCF REST サービスを呼び出します。 WCF REST サービスは、コールバック関数名でラップされた顧客の名前とアドレスを返します。 WCF REST サービスが応答を返すと、顧客データを使用して Web ページ上のコールバック関数が呼び出され、このコールバック関数によって Web ページ上に顧客データが表示されます。 スクリプト タグの挿入とコールバック関数の実行は、ASP.NET AJAX ScriptManager コントロールによって自動的に処理されます。 次のコードに示すように、使用パターンはすべての ASP.NET AJAX プロキシと同じで、JSONP を有効にするための行が 1 つ追加されます。  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 Web ページでは、WCF REST サービスを呼び出すことができます。これは、WCF REST サービスが、<xref:System.ServiceModel.Description.WebScriptEndpoint> が `crossDomainScriptAccessEnabled` に設定された `true` を使用しているからです。 下にある Web.config ファイルでこれらの構成が終わったら、 \<system.serviceModel > 要素。  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。 ときに`crossDomainScriptAccessEnabled`に設定されている`true`操作の応答形式が JSON と、WCF インフラストラクチャがコールバック クエリ文字列パラメーターの要求の URI を検査し、コールバック クエリ文字列の値と JSON 応答をラップパラメーター。 このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。 ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。  
  
 サンプルを次の 2 つの ASP.NET web アプリケーションの構成: WCF サービスだけを含む 1 つともう 1 つにはサービスを呼び出す .aspx web ページが含まれています。 ソリューションの実行中、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は 2 つの Web サイトを別々のポート上にホストします。これにより、サービスとクライアントが別々のドメインに存在する環境が作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  JSONP サンプルのソリューションを開きます。  
  
2.  起動する f5 キーを押して`http://localhost:26648/JSONPClientPage.aspx`ブラウザーにします。  
  
3.  ページが読み込まれると、"Name"および"Address"のテキスト入力が設定されている値に注意してください。  これらの値は、ブラウザーがページのレンダリングを完了した後に、WCF サービスへの呼び出しから提供されたものです。
