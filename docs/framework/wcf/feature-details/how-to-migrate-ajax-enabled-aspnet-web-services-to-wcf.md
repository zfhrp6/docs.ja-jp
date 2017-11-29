---
title: "方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91b611af6c8de5c2bc0119838eb12950d3207177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="8b9d6-102">方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="8b9d6-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="8b9d6-103">ここでは、基本的な ASP.NET AJAX サービスを同等の AJAX 対応 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに移行する手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="8b9d6-104">ここでは、ASP.NET AJAX サービスの、機能的に同等の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-104">It shows how to create a functionally equivalent [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="8b9d6-105">この 2 つのサービスを並行して使用することも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを ASP.NET AJAX サービスと置き換えて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-105">The two services can then be used side by side, or the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be used to replace the ASP.NET AJAX service.</span></span>  
  
 <span data-ttu-id="8b9d6-106">既存の ASP.NET AJAX サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスに移行すると、次のような利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-106">Migrating an existing ASP.NET AJAX service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="8b9d6-107">最小限の追加構成で、AJAX サービスを SOAP サービスとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>  
  
-   <span data-ttu-id="8b9d6-108">トレースなどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の機能の利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-108">You can benefit from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features such as tracing, and so on.</span></span>  
  
 <span data-ttu-id="8b9d6-109">次の手順では、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] が使用されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-109">The following procedures assume that you are using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
 <span data-ttu-id="8b9d6-110">手順に続く例で、ここで説明する手順によって作成されるコードを示します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8b9d6-111">公開する、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX 対応エンドポイントを介してサービスを参照してください、[する方法: ASP.NET AJAX エンドポイントを追加する構成を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-111"> exposing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="8b9d6-112">ASP.NET Web サービス アプリケーションを作成してテストする</span><span class="sxs-lookup"><span data-stu-id="8b9d6-112">To create and test the ASP.NET Web service application</span></span>  
  
1.  <span data-ttu-id="8b9d6-113">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-113">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="8b9d6-114">**ファイル**メニューの **新規**、し**プロジェクト**、し**Web**、し、 **ASP.NET Web サービス アプリケーション**.</span><span class="sxs-lookup"><span data-stu-id="8b9d6-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>  
  
3.  <span data-ttu-id="8b9d6-115">プロジェクトに名前を`ASPHello` をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-115">Name the project `ASPHello` and click **OK**.</span></span>  
  
4.  <span data-ttu-id="8b9d6-116">Service1.asmx.cs ファイルで、`System.Web.Script.Services.ScriptService]` が含まれた行のコメントを解除し、このサービスに対して AJAX を有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>  
  
5.  <span data-ttu-id="8b9d6-117">**ビルド**メニューの **ソリューションのビルド**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-117">From the **Build** menu, select **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="8b9d6-118">**デバッグ**メニューの **デバッグなしで開始**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
7.  <span data-ttu-id="8b9d6-119">生成された Web ページで、`HelloWorld` 操作を選択します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-119">On the Web page generated, select the `HelloWorld` operation.</span></span>  
  
8.  <span data-ttu-id="8b9d6-120">クリックして、 **Invoke**のボタンでは、`HelloWorld`テスト ページ。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="8b9d6-121">次の XML 応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-121">You should receive the following XML response.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. <span data-ttu-id="8b9d6-122">この応答は、ASP.NET AJAX サービスが現在機能していること、およびこのサービスが現在 Service1.asmx/HelloWorld でエンドポイントを公開していることを確認するものです。このエンドポイントが HTTP POST 要求に応答し、XML を返します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>  
  
     <span data-ttu-id="8b9d6-123">これで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスを使用するために、このサービスを変換する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-123">Now you are ready to convert this service to use a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service.</span></span>  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="8b9d6-124">同等の WCF AJAX サービス アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="8b9d6-124">To create an equivalent WCF AJAX service application</span></span>  
  
1.  <span data-ttu-id="8b9d6-125">右クリックし、 **ASPHello**プロジェクトし、選択**追加**、し**新しい項目の**、し**AJAX 対応 WCF サービス**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="8b9d6-126">サービスの名前を付けます`WCFHello` をクリック**追加**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-126">Name the service `WCFHello` and click **Add**.</span></span>  
  
3.  <span data-ttu-id="8b9d6-127">WCFHello.svc.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-127">Open the WCFHello.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="8b9d6-128">Service1.asmx.cs からの次の実装をコピー、`HelloWorld`操作します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  <span data-ttu-id="8b9d6-129">コピーの実装に貼り付け、`HelloWorld`次のコードの代わりに、WCFHello.svc.cs ファイルに操作します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  <span data-ttu-id="8b9d6-130">指定して、`Namespace`属性<xref:System.ServiceModel.ServiceContractAttribute>として`WCFHello`です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <span data-ttu-id="8b9d6-131">追加、<xref:System.ServiceModel.Web.WebInvokeAttribute>を`HelloWorld`操作とセット、<xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>を返すプロパティ<xref:System.ServiceModel.Web.WebMessageFormat.Xml>です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="8b9d6-132">この設定を行わない場合、既定の戻り値の型は <xref:System.ServiceModel.Web.WebMessageFormat.Json> です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  <span data-ttu-id="8b9d6-133">**ビルド**メニューの **ソリューションのビルド**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-133">From the **Build** menu, select **Build Solution**.</span></span>  
  
9. <span data-ttu-id="8b9d6-134">WCFHello.svc ファイルを開くとの間、**デバッグ**メニューの **デバッグなしで開始**です。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
10. <span data-ttu-id="8b9d6-135">サービス エンドポイントを公開今すぐ`WCFHello.svc/HelloWorld`、HTTP POST 要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="8b9d6-136">HTTP POST 要求をブラウザーからテストすることはできませんが、エンドポイントは次の XML を返します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. <span data-ttu-id="8b9d6-137">`WCFHello.svc/HelloWorld`と`Service1.aspx/HelloWorld`エンドポイントは機能的に等価ようになりました。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b9d6-138">例</span><span class="sxs-lookup"><span data-stu-id="8b9d6-138">Example</span></span>  
 <span data-ttu-id="8b9d6-139">このトピックで説明した手順によって作成されるコードを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>  
  
```  
//This is the ASP.NET code in the Service1.asmx.cs file.  
  
using System;  
using System.Collections;  
using System.ComponentModel;  
using System.Data;  
using System.Linq;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Linq;  
using System.Web.Script.Services;  
  
namespace ASPHello  
{  
    /// <summary>  
    /// Summary description for Service1.  
    /// </summary>  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    [ToolboxItem(false)]  
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.   
    [System.Web.Script.Services.ScriptService]  
    public class Service1 : System.Web.Services.WebService  
    {  
  
        [WebMethod]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
    }  
}   
  
//This is the WCF code in the WCFHello.svc.cs file.  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace ASPHello  
{  
    [ServiceContract(Namespace = "WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class WCFHello  
    {  
        // Add [WebInvoke] attribute to use HTTP GET.  
        [OperationContract]  
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
        public string HelloWorld()  
        {  
            return "Hello World";  
        }  
  
        // Add more operations here and mark them with [OperationContract].  
    }  
}  
```  
  
 <span data-ttu-id="8b9d6-140"><xref:System.Xml.XmlDocument> 型は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によってシリアル化できないため、<xref:System.Xml.Serialization.XmlSerializer> ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8b9d6-141"><xref:System.Xml.Linq.XDocument> 型を使用するか、<xref:System.Xml.XmlDocument.DocumentElement%2A> をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>  
  
 <span data-ttu-id="8b9d6-142">ASMX Web サービスが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと並行してアップグレードおよび移行される場合は、クライアントで 2 つの型を同じ名前に割り当てないようにします。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-142">If ASMX Web services are being upgraded and migrated side-by-side to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="8b9d6-143">同じ名前が割り当てられていると、<xref:System.Web.Services.WebMethodAttribute> と <xref:System.ServiceModel.ServiceContractAttribute> で同じ型が使用されている場合に、シリアライザーで次のような例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>  
  
-   <span data-ttu-id="8b9d6-144">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが先に追加された場合は、ASMX Web サービスでメソッドを呼び出すと、<xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> で例外が発生します。これは、プロキシでの順序の定義で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタイル定義が優先されるためです。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-144">If [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] style definition of the order in the proxy takes precedence.</span></span>  
  
-   <span data-ttu-id="8b9d6-145">ASMX Web サービスが先に追加された場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでメソッドを呼び出すと、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> で例外が発生します。これは、プロキシでの順序の定義で Web サービス スタイル定義が優先されるためです。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-145">If ASMX Web Service is added first, invoking method on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>  
  
 <span data-ttu-id="8b9d6-146"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> の動作には大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="8b9d6-147">たとえば、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> はディクショナリをキーと値のペアの配列として表しますが、ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> はディクショナリを実際の JSON オブジェクトとして表します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="8b9d6-148">したがって、ASP.NET AJAX では、ディクショナリが次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 <span data-ttu-id="8b9d6-149">このディクショナリは、JSON オブジェクトでは次のように表されます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>  
  
-   <span data-ttu-id="8b9d6-150"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では [{"Key":"one","Value":1},{"Key":"two","Value":2}] と表され、</span><span class="sxs-lookup"><span data-stu-id="8b9d6-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>  
  
-   <span data-ttu-id="8b9d6-151">{"one": 1,"two": 2} ASP.NET ajax<xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="8b9d6-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>  
  
 <span data-ttu-id="8b9d6-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、キーの種類が文字列ではないディクショナリを処理でき、<xref:System.Web.Script.Serialization.JavaScriptSerializer> はできません。この点で前者はより強力と言えます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="8b9d6-153">しかし、後者の方が JSON で使いやすいと言えます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-153">But the latter is more JSON-friendly.</span></span>  
  
 <span data-ttu-id="8b9d6-154">これらのシリアライザーの主な違いを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-154">The significant differences between these serializers are summarized in the following table.</span></span>  
  
|<span data-ttu-id="8b9d6-155">相違点のカテゴリ</span><span class="sxs-lookup"><span data-stu-id="8b9d6-155">Category of Differences</span></span>|<span data-ttu-id="8b9d6-156">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="8b9d6-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="8b9d6-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="8b9d6-157">ASP.NET AJAX JavaScriptSerializer</span></span>|  
|-----------------------------|--------------------------------|---------------------------------------|  
|<span data-ttu-id="8b9d6-158">空きバッファー (新しい byte[0]) の <xref:System.Object> (または <xref:System.Uri>、あるいは他の一部のクラス) への逆シリアル化</span><span class="sxs-lookup"><span data-stu-id="8b9d6-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="8b9d6-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="8b9d6-159">SerializationException</span></span>|<span data-ttu-id="8b9d6-160">null</span><span class="sxs-lookup"><span data-stu-id="8b9d6-160">null</span></span>|  
|<span data-ttu-id="8b9d6-161"><xref:System.DBNull.Value> のシリアル化</span><span class="sxs-lookup"><span data-stu-id="8b9d6-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="8b9d6-162">{} (or {"__type":"#System"})</span><span class="sxs-lookup"><span data-stu-id="8b9d6-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="8b9d6-163">Null</span><span class="sxs-lookup"><span data-stu-id="8b9d6-163">Null</span></span>|  
|<span data-ttu-id="8b9d6-164">[Serializable] 型のプライベート メンバーのシリアル化</span><span class="sxs-lookup"><span data-stu-id="8b9d6-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="8b9d6-165">シリアル化できます</span><span class="sxs-lookup"><span data-stu-id="8b9d6-165">serialized</span></span>|<span data-ttu-id="8b9d6-166">シリアル化できません</span><span class="sxs-lookup"><span data-stu-id="8b9d6-166">not serialized</span></span>|  
|<span data-ttu-id="8b9d6-167"><xref:System.Runtime.Serialization.ISerializable> 型のパブリック プロパティのシリアル化</span><span class="sxs-lookup"><span data-stu-id="8b9d6-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="8b9d6-168">シリアル化できません</span><span class="sxs-lookup"><span data-stu-id="8b9d6-168">not serialized</span></span>|<span data-ttu-id="8b9d6-169">シリアル化できます</span><span class="sxs-lookup"><span data-stu-id="8b9d6-169">serialized</span></span>|  
|<span data-ttu-id="8b9d6-170">JSON の「拡張機能」</span><span class="sxs-lookup"><span data-stu-id="8b9d6-170">"Extensions" of JSON</span></span>|<span data-ttu-id="8b9d6-171">オブジェクト メンバー名で引用符を必要とする ({"a":"hello"}) JSON 仕様に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="8b9d6-172">引用符のないオブジェクト メンバー名 ({a:"hello"}) をサポートします。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|  
|<span data-ttu-id="8b9d6-173"><xref:System.DateTime> 協定世界時刻 (UTC)</span><span class="sxs-lookup"><span data-stu-id="8b9d6-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="8b9d6-174">形式をサポートしていません"\\/Date(123456789U)\\/"または"\\日付/\\(\d+ (U &#124; (\\+\\-[\d{4}]))?\\)\\\\/)".</span><span class="sxs-lookup"><span data-stu-id="8b9d6-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="8b9d6-175">形式"\\/Date(123456789U)\\/"および"\\日付/\\(\d+ (U &#124; (\\+\\-[\d{4}]))?\\)\\ \\/)"としての DateTime 値。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|  
|<span data-ttu-id="8b9d6-176">ディクショナリの表現</span><span class="sxs-lookup"><span data-stu-id="8b9d6-176">Representation of dictionaries</span></span>|<span data-ttu-id="8b9d6-177">KeyValuePair の配列\<K, V >、文字列以外の種類のキーを処理します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="8b9d6-178">実際の JSON オブジェクトですが、文字列の種類のキーのみ処理します。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-178">As actual JSON objects - but only handles key types that are strings.</span></span>|  
|<span data-ttu-id="8b9d6-179">エスケープ文字</span><span class="sxs-lookup"><span data-stu-id="8b9d6-179">Escaped characters</span></span>|<span data-ttu-id="8b9d6-180">必ず、エスケープ文字であるスラッシュ (/) を付けます。"\n" などのエスケープされない無効な JSON 文字は使用できません。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="8b9d6-181">DateTime 値には、エスケープ文字スラッシュ (/) を付けます。</span><span class="sxs-lookup"><span data-stu-id="8b9d6-181">With an escape forward slash (/) for DateTime values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b9d6-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b9d6-182">See Also</span></span>  
 [<span data-ttu-id="8b9d6-183">方法: 構成を使用して ASP.NET AJAX エンドポイントを追加するには</span><span class="sxs-lookup"><span data-stu-id="8b9d6-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
