---
title: 複合型を使用した AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: c284fbef36ee7f6dda725ba9a3db9b98fb1549ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-complex-types-sample"></a>複合型を使用した AJAX サービスのサンプル
このサンプルでは、Windows Communication Foundation (WCF) を使用して、複合型のインスタンスを作成し、サービスとクライアントの JavaScript Object Notation (JSON) との間で送信する ASP.NET Asynchronous JavaScript and XML (AJAX) サービスを作成する方法を示します。 AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。 このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルです。  
  
 WCF での AJAX サポートがを介して ASP.NET AJAX と共に使用できるように最適化、<xref:System.Web.UI.ScriptManager>コントロール。 WCF を ASP.NET AJAX と共に使用しての例は、次を参照してください。、 [AJAX サンプル](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 次のサンプルのサービスには、AJAX 固有のコードを持たない WCF サービスです。 <xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。 サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。 複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。  

```csharp
[DataContract]  
public class MathResult  
{  
    [DataMember]  
    public double sum;  
    [DataMember]  
    public double difference;  
    [DataMember]  
    public double product;  
    [DataMember]  
    public double quotient;  
}  
```

 基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。  
  
 クライアント Web ページ ComplexTypeClientPage.aspx には、ユーザーがクリックしたときに、サービスを呼び出す ASP.NET および JavaScript のコードが含まれています、**計算を実行する** ページでボタンをクリックします。 サービスを呼び出すコードが JSON 本文を構築し、送信のような HTTP POST を使用して、 [HTTP POST を使用して AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)サンプルです。  
  
 サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションをビルドします ComplexTypeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。  
  
3.  移動http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx(開かないで ComplexTypeClientPage.aspx プロジェクト ディレクトリからブラウザーで)。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>関連項目  
 [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
