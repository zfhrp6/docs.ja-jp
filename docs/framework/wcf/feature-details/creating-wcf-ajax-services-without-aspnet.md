---
title: ASP.NET を使用せずに WCF AJAX サービスを作成する方法
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 77a850408c3d952dbd4f682ea704d3248ae17c3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490358"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET を使用せずに WCF AJAX サービスを作成する方法
Windows Communication Foundation (WCF) の AJAX サービスは、ASP.NET AJAX を必要とせず、JavaScript 対応の Web ページからアクセスできます。 このトピックでは、このような WCF サービスを作成する方法について説明します。  
  
 ASP.NET AJAX での WCF の使用方法の詳細については、次を参照してください。 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)です。  
  
 WCF AJAX サービスを作成する 3 つの部分があります。  
  
-   ブラウザーからアクセスできる AJAX エンドポイントの作成  
  
-   AJAX 互換サービス コントラクトの作成  
  
-   WCF AJAX サービスへのアクセス  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX エンドポイントの作成  
 WCF サービスでの AJAX サポートを有効にする最も基本的な方法は、使用する、<xref:System.ServiceModel.Activation.WebServiceHostFactory>次の例のように、サービスに関連付けられた .svc ファイルでします。  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 構成を使用して AJAX エンドポイントを追加することもできます。 次のコード スニペットに示すように、サービス エンドポイントで <xref:System.ServiceModel.WebHttpBinding> を使用し、<xref:System.ServiceModel.Description.WebHttpBehavior> を使用してこのエンドポイントを構成します。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 実際の例では、次を参照してください。、 [JSON と XML での AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)です。  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>AJAX 互換サービス コントラクトの作成  
 既定では、AJAX エンドポイントを介して公開されるサービス コントラクトは、XML 形式でデータを返します。 また、次の例に示すように、既定では、エンドポイント アドレスの後に操作名を追加した URL に対する HTTP POST 要求によって、サービス操作にアクセスできます。  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 この操作は、HTTP POST を使用してアクセス`http://serviceaddress/endpointaddress/GetCities`し、XML メッセージを返します。  
  
 Web プログラミング モデルを活用することで、これらの基本的な部分をカスタマイズできます。 たとえば、<xref:System.ServiceModel.Web.WebGetAttribute> 属性または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、操作が応答する HTTP 動詞を制御したり、これらの属性の `UriTemplate` プロパティを使用して、カスタム URI を指定したりできます。 詳細については、次を参照してください。、 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)トピックです。  
  
 AJAX サービスでは、JSON データ形式がよく使用されます。 XML ではなく JSON を返す操作を作成するには、<xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (または <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) プロパティを <xref:System.ServiceModel.Web.WebMessageFormat.Json> に設定します。 [スタンドアロン JSON のシリアル化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)トピックを JSON にどの組み込み .NET 型とデータ コントラクト型のマップを示しています。  
  
 JSON の要求と応答は、通常 1 つの項目のみで構成されます。 前述の `GetCities` 操作の場合、要求は次のようなステートメントになります。  
  
```  
"na"  
```  
  
 この要求に対する応答は、次のようなステートメントになります。  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 操作で追加のパラメーターを受け取る場合は、両方のパラメーターを 1 つの JSON オブジェクトにラップするために、要求スタイルをラップする必要があります。 このスタイルの JSON メッセージの一例を次に示します。  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 次のコントラクトがこのメッセージを受け入れます。  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>AJAX サービスへのアクセス  
 WCF AJAX エンドポイントは、常に、JSON と XML の両方の要求を受け入れます。  
  
 "Application/json"とのコンテンツの種類の HTTP POST 要求は JSON として扱われ、XML (たとえば、"テキストまたは xml") を示しているコンテンツの種類では XML として扱われます。  
  
 HTTP GET 要求では、URL 自体にすべての要求パラメーターが含まれています。  
  
 エンドポイントに対して HTTP 要求を作成する方法は、ユーザーが自由に決定できます。 また、要求の本文を構成する JSON の作成についても、ユーザーが完全に制御できます。 JavaScript からの要求の作成の例は、次を参照してください。、 [JSON と XML での AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)です。
