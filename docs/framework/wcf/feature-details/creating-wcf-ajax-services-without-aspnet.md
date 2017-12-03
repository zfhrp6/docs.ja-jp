---
title: "ASP.NET を使用せずに WCF AJAX サービスを作成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4ff3e41608c9b879bd64e004fcae5e87599e0b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>ASP.NET を使用せずに WCF AJAX サービスを作成する方法
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] AJAX サービスには、JavaScript 対応の Web ページからアクセスできます。ASP.NET AJAX は必要ありません。 ここでは、このような [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成する方法について説明します。  
  
 使用法について[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。 [ASP.NET AJAX 用の WCF サービスの作成](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)です。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスを作成する手順は、次の 3 つに分けられます。  
  
-   ブラウザーからアクセスできる AJAX エンドポイントの作成  
  
-   AJAX 互換サービス コントラクトの作成  
  
-   WCF AJAX サービスへのアクセス  
  
## <a name="creating-an-ajax-endpoint"></a>AJAX エンドポイントの作成  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスで AJAX のサポートを有効にする最も基本的な方法は、次の例に示すように、サービスに関連付けられた .svc ファイルの <xref:System.ServiceModel.Activation.WebServiceHostFactory> を使用することです。  
  
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
  
 Web プログラミング モデルを活用することで、これらの基本的な部分をカスタマイズできます。 たとえば、<xref:System.ServiceModel.Web.WebGetAttribute> 属性または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性を使用して、操作が応答する HTTP 動詞を制御したり、これらの属性の `UriTemplate` プロパティを使用して、カスタム URI を指定したりできます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)トピックです。  
  
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
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX エンドポイントでは、常に JSON と XML の両方の要求を受け入れます。  
  
 "Application/json"とのコンテンツの種類の HTTP POST 要求は JSON として扱われ、XML (たとえば、"テキストまたは xml") を示しているコンテンツの種類では XML として扱われます。  
  
 HTTP GET 要求では、URL 自体にすべての要求パラメーターが含まれています。  
  
 エンドポイントに対して HTTP 要求を作成する方法は、ユーザーが自由に決定できます。 また、要求の本文を構成する JSON の作成についても、ユーザーが完全に制御できます。 JavaScript からの要求の作成の例は、次を参照してください。、 [JSON と XML での AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)です。
