---
title: "System.Web.Routing 統合 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.Web.Routing 統合
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをインターネット インフォメーション サービス \(IIS\) でホストするときは、.svc ファイルを仮想ディレクトリに配置します。この .svc ファイルは、使用するサービス ホスト ファクトリと、サービスを実装するクラスを指定します。サービスを要求するときは、http:\/\/contoso.com\/EmployeeServce.svc などの URI で .svc ファイルを指定します。REST サービスを記述するプログラマにとっては、この種類の URI は最適とは言えません。REST サービス用の URI は、特定のリソースを指定しており、拡張子がないのが普通です。<xref:System.Web.Routing> 統合機能では、拡張子のない URI に応答する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST サービスをホストできます。ルーティング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ASP.NET ルーティング](http://go.microsoft.com/fwlink/?LinkId=184660)」および「[AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md)」のサンプルを参照してください。  
  
## System.Web.Routing 統合の使用  
 <xref:System.Web.Routing> 統合機能を使用するには、<xref:System.ServiceModel.Activation.ServiceRoute> クラスを使用して 1 つ以上のルートを作成し、Global.asax ファイルでそれらを <xref:System.Web.Routing.RouteTable> に追加します。これらのルートは、サービスが応答する相対 URI を指定します。その方法を次の例に示します。  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
  
```  
  
 これは、Customers で始まる相対 URI が指定されたすべての要求を `Service` サービスにルーティングします。  
  
 Web.config ファイルでは、次の例に示すように、`System.Web.Routing.UrlRoutingModule` モジュールを追加し、`runAllManagedModulesForAllRequests` 属性を `true` に設定し、`UrlRoutingHandler` ハンドラーを `<system.webServer>` 要素に追加する必要があります。  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 これで、ルーティングに必要なモジュールとハンドラーが読み込まれます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ルーティング](../../../../docs/framework/wcf/feature-details/routing.md).また、次の例に示すように、`<serviceHostingEnvironment>` 要素で `aspNetCompatibilityEnabled` 属性を `true` に設定する必要もあります。  
  
```  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 次の例に示すように、このサービスを実装するクラスでは、ASP.NET 互換要件を有効にする必要があります。  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## 参照  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [ASP.NET ルーティング](http://go.microsoft.com/fwlink/?LinkId=184660)