---
title: "複合型を使用した AJAX サービスのサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 複合型を使用した AJAX サービスのサンプル
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、複合型のインスタンスを作成し、そのインスタンスをサービスとクライアント間で JSON \(JavaScript Object Notation\) として送信する ASP.NET AJAX \(Asynchronous JavaScript and XML\) サービスを作成する方法を示します。AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。このサンプルは、「[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)」のサンプルに基づいています。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、<xref:System.Web.UI.ScriptManager> コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。ASP.NET AJAX と共に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用する例については、「[AJAX Samples](http://msdn.microsoft.com/ja-jp/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)」を参照してください。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 次に示すサンプルのサービスは、AJAX 固有のコードを持たない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。<xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 \("POST"\) が使用されます。サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。  
  
```  
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
  
 クライアント Web ページ ComplexTypeClientPage.aspx には、ユーザーがページの **\[Perform calculation\]** ボタンをクリックしたときにサービスを呼び出す ASP.NET および JavaScript コードが含まれています。サービスを呼び出すコードは、JSON 本文を作成し、HTTP POST を使用して送信します。これは、[HTTP POST を使用する AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) サンプルと同様です。  
  
 サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー \(`sum`、`difference`、`product`、および `quotient`\) にアクセスできます。  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」で説明されているように、ソリューション ComplexTypeAjaxService.sln をビルドします。  
  
3.  http:\/\/localhost\/ServiceModelSamples\/ComplexTypeClientPage.aspx に移動します \(プロジェクト ディレクトリからブラウザーで ComplexTypeClientPage.aspx を開かないでください\)。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## 参照  
 [基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)