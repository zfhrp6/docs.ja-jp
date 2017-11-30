---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 56e287543f2510823beff4cb84f6d9cab245cdac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="jsonp"></a>JSONP
このサンプルでは、WCF REST サービスの JSONP (JSON with Padding) をサポートする方法を示します。 JSONP とは、現在のドキュメントでスクリプト タグを生成してドメイン間スクリプトを呼び出す際に使用される変換です。 結果は、指定したコールバック関数で返されます。 JSONP はなどのタグするという考えに基づいて\<スクリプトの src =「http://...」> の任意のドメインからのスクリプトを評価することができ、ようなタグによって取得されたスクリプトが、その他の関数が既に定義されて範囲で評価します。  
  
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
  
 ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。 `crossDomainScriptAccessEnabled` が `true` に設定されていて、操作の応答形式が JSON である場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャは要求の URI からコールバック クエリ文字列パラメーターを検出し、そのコールバック クエリ文字列パラメーターの値で JSON 応答をラップします。 このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。 ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。  
  
 このサンプルは 2 つの ASP.NET Web アプリケーションで構成されます。1 つは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみを含み、もう 1 つはサービスを呼び出す .aspx Web ページを含みます。 ソリューションの実行中、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は 2 つの Web サイトを別々のポート上にホストします。これにより、サービスとクライアントが別々のドメインに存在する環境が作成されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>サンプルを実行するには  
  
1.  JSONP サンプルのソリューションを開きます。  
  
2.  F5 キーを押して、http://localhost:26648/jsonpclientpage.aspx ハイパーリンク""http://localhost:26648/JSONPClientPage.aspx をブラウザーにします。  
  
3.  ページが読み込まれると、"Name"および"Address"のテキスト入力が設定されている値に注意してください。  これらの値は、ブラウザーがページを表示した後に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの呼び出しから提供されたものです。
