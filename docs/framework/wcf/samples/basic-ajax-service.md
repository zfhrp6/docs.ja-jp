---
title: 基本的な AJAX サービス
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: a534e4eda1f95cd33d4429fda23b6187caaf58ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="basic-ajax-service"></a>基本的な AJAX サービス
このサンプルでは、Windows Communication Foundation (WCF) を使用して基本的な ASP.NET Asynchronous JavaScript and XML (AJAX) サービス (Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。 このサービスは、<xref:System.ServiceModel.Web.WebGetAttribute> 属性を使用してサービスが HTTP GET 要求に応答し、JSON (JavaScript Object Notation) データ形式を使用して応答するように構成されていることを確認します。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、`ScriptManager` コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。 使用する例については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。、 [AJAX サンプル](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 次のコードでは、サービスが確実に HTTP GET 要求に応答するように <xref:System.ServiceModel.Web.WebGetAttribute> 属性が `Add` 操作に適用されています。 このコードでは、簡単にするために GET を使用します (すべての Web ブラウザーから HTTP GET 要求を構築できます)。 また、GET を使用してキャッシングを有効にすることもできます。 HTTP POST は `WebGetAttribute` 属性を使用しない場合の既定です。  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 サンプルの .svc ファイルでは <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> が使用され、それによって <xref:System.ServiceModel.Description.WebScriptEndpoint> 標準エンドポイントがサービスに追加されます。 エンドポイントは、.svc ファイルに相対する空のアドレス位置に設定されます。 つまり、サービスのアドレスがhttp://localhost/ServiceModelSamples/service.svc、追加のサフィックスのない操作名以外にします。  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <xref:System.ServiceModel.Description.WebScriptEndpoint> は、ASP.NET AJAX クライアント ページからサービスにアクセスできるように事前に構成されています。 Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。 追加の変更が不要な場合は、このセクションを削除できます。  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint> は、サービスの既定のデータ形式を XML ではなく JSON に設定します。 サービスを呼び出すに移動http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200後のセットを完了して、このトピックの後半に示す手順をビルドします。 このテスト機能は、HTTP GET 要求を使用することによって有効になります。  
  
 クライアントの Web ページの SimpleAjaxClientPage.aspx には、ユーザーがページ上のいずれかの操作ボタンをクリックするとサービスを呼び出す ASP.NET コードが含まれています。 `ScriptManager` コントロールは、JavaScript を使用してサービスからプロキシにアクセスできるようにする場合に使用します。  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 次の JavaScript コードを使用してローカル プロキシをインスタンス化し、操作を呼び出します。  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 サービス呼び出しが成功すると、コードは `onSuccess` ハンドラーを呼び出し、操作の結果がテキスト ボックスに表示されます。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>関連項目
