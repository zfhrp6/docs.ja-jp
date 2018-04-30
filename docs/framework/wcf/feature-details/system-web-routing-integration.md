---
title: System.Web.Routing 統合
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72403671fe6700ae26cae4471a1d0ac100005f3a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="6ccb6-102">System.Web.Routing 統合</span><span class="sxs-lookup"><span data-stu-id="6ccb6-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="6ccb6-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをインターネット インフォメーション サービス (IIS) でホストするときは、.svc ファイルを仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="6ccb6-104">この .svc ファイルは、使用するサービス ホスト ファクトリと、サービスを実装するクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="6ccb6-105">たとえば、URI で .svc ファイルを指定するサービスに要求を行うときに:http://contoso.com/EmployeeServce.svcです。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="6ccb6-106">REST サービスを記述するプログラマにとっては、この種類の URI は最適とは言えません。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="6ccb6-107">REST サービス用の URI は、特定のリソースを指定しており、拡張子がないのが普通です。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="6ccb6-108"><xref:System.Web.Routing> 統合機能では、拡張子のない URI に応答する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST サービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="6ccb6-109">ルーティングの参照の詳細については[ASP.NET ルーティング](http://go.microsoft.com/fwlink/?LinkId=184660)と[AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-109">For more information about routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="6ccb6-110">System.Web.Routing 統合の使用</span><span class="sxs-lookup"><span data-stu-id="6ccb6-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="6ccb6-111"><xref:System.Web.Routing> 統合機能を使用するには、<xref:System.ServiceModel.Activation.ServiceRoute> クラスを使用して 1 つ以上のルートを作成し、Global.asax ファイルでそれらを <xref:System.Web.Routing.RouteTable> に追加します。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="6ccb6-112">これらのルートは、サービスが応答する相対 URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="6ccb6-113">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="6ccb6-114">これは、Customers で始まる相対 URI が指定されたすべての要求を `Service` サービスにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="6ccb6-115">Web.config ファイルでは、次の例に示すように、`System.Web.Routing.UrlRoutingModule` モジュールを追加し、`runAllManagedModulesForAllRequests` 属性を `true` に設定し、`UrlRoutingHandler` ハンドラーを `<system.webServer>` 要素に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6ccb6-116">これで、ルーティングに必要なモジュールとハンドラーが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="6ccb6-117">詳細については、[ルーティング](../../../../docs/framework/wcf/feature-details/routing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="6ccb6-118">また、次の例に示すように、`aspNetCompatibilityEnabled` 要素で `true` 属性を `<serviceHostingEnvironment>` に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="6ccb6-119">次の例に示すように、このサービスを実装するクラスでは、ASP.NET 互換要件を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ccb6-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ccb6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ccb6-120">See Also</span></span>  
 [<span data-ttu-id="6ccb6-121">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="6ccb6-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="6ccb6-122">ASP.NET ルーティング</span><span class="sxs-lookup"><span data-stu-id="6ccb6-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
