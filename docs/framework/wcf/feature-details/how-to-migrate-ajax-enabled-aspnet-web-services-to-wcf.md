---
title: "方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# 方法 : AJAX 対応 ASP.NET Web サービスを WCF に移行する
ここでは、基本的な ASP.NET AJAX サービスを同等の AJAX 対応 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスに移行する手順の概要を説明します。  ここでは、ASP.NET AJAX サービスの、機能的に同等の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バージョンを作成する方法を示します。  この 2 つのサービスを並行して使用することも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを ASP.NET AJAX サービスと置き換えて使用することもできます。  
  
 既存の ASP.NET AJAX サービスを [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスに移行すると、次のような利点が得られます。  
  
-   最小限の追加構成で、AJAX サービスを SOAP サービスとして公開できます。  
  
-   トレースなどの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の機能の利点が得られます。  
  
 次の手順では、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] が使用されていることを前提としています。  
  
 手順に続く例で、ここで説明する手順によって作成されるコードを示します。  
  
 AJAX 対応エンドポイントを介した [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの公開[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)」トピックを参照してください。  
  
### ASP.NET Web サービス アプリケーションを作成してテストする  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をクリックし、**\[プロジェクト\]**、**\[Web\]** の順にクリックして、**\[ASP.NET Web サービス アプリケーション\]** をクリックします。  
  
3.  プロジェクトに「`ASPHello`」という名前を付け、**\[OK\]** をクリックます。  
  
4.  Service1.asmx.cs ファイルで、`System.Web.Script.Services.ScriptService]` が含まれた行のコメントを解除し、このサービスに対して AJAX を有効にします。  
  
5.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
6.  **\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックします。  
  
7.  生成された Web ページで、`HelloWorld` 操作を選択します。  
  
8.  テスト ページで、`HelloWorld`**\[起動\]** をクリックします。  次の XML 応答を受信します。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. この応答は、ASP.NET AJAX サービスが現在機能していること、およびこのサービスが現在 Service1.asmx\/HelloWorld でエンドポイントを公開していることを確認するものです。このエンドポイントが HTTP POST 要求に応答し、XML を返します。  
  
     これで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスを使用するために、このサービスを変換する準備ができました。  
  
### 同等の WCF AJAX サービス アプリケーションを作成するには  
  
1.  **ASPHello** プロジェクトを右クリックして、**\[追加\]**、**\[新しい項目\]** の順にクリックして、**\[AJAX 対応 WCF サービス\]** をクリックします。  
  
2.  サービスに「`WCFHello`」という名前を付けて、**\[追加\]** をクリックします。  
  
3.  WCFHello.svc.cs ファイルを開きます。  
  
4.  Service1.asmx.cs から、`HelloWorld` 操作の次の実装をコピーします。  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  コピーした `HelloWorld` 操作の実装を、WCFHello.svc.cs ファイルの次のコードの代わりに貼り付けます。  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  `Namespace` の <xref:System.ServiceModel.ServiceContractAttribute> 属性を `WCFHello` に指定します。  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <xref:System.ServiceModel.Web.WebInvokeAttribute> を `HelloWorld` 操作に追加し、<xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> を返すように <xref:System.ServiceModel.Web.WebMessageFormat> プロパティを設定します。  この設定を行わない場合、既定の戻り値の型は <xref:System.ServiceModel.Web.WebMessageFormat> です。  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
9. WCFHello.svc ファイルを開き、**\[デバッグ\]** メニューの **\[デバッグなしで開始\]** をクリックします。  
  
10. 現在、サービスは、`WCFHello.svc/HelloWorld` でエンドポイントを公開しています。このエンドポイントが HTTP POST 要求に応答します。  HTTP POST 要求をブラウザーからテストすることはできませんが、エンドポイントは次の XML を返します。  
  
    ```  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. これで、`WCFHello.svc/HelloWorld` エンドポイントと `Service1.aspx/HelloWorld` エンドポイントは機能的に同等になりました。  
  
## 使用例  
 このトピックで説明した手順によって作成されるコードを次の例に示します。  
  
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
  
 <xref:System.Xml.XmlDocument> 型は、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によってシリアル化できないため、<xref:System.Xml.Serialization.XmlSerializer> ではサポートされていません。  <xref:System.Xml.Linq.XDocument> 型を使用するか、<xref:System.Xml.XmlDocument.DocumentElement%2A> をシリアル化します。  
  
 ASMX Web サービスが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスと並行してアップグレードおよび移行される場合は、クライアントで 2 つの型を同じ名前に割り当てないようにします。  同じ名前が割り当てられていると、<xref:System.Web.Services.WebMethodAttribute> と <xref:System.ServiceModel.ServiceContractAttribute> で同じ型が使用されている場合に、シリアライザーで次のような例外が発生します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが先に追加された場合は、ASMX Web サービスでメソッドを呼び出すと、<xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> で例外が発生します。これは、プロキシでの順序の定義で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] スタイル定義が優先されるためです。  
  
-   ASMX Web サービスが先に追加された場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスでメソッドを呼び出すと、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> で例外が発生します。これは、プロキシでの順序の定義で Web サービス スタイル定義が優先されるためです。  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> と ASP.NET AJAX <xref:System.Web.Script.Serialization.JavascriptSerializer> の動作には大きな違いがあります。  たとえば、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> はディクショナリをキーと値のペアの配列として表しますが、ASP.NET AJAX <xref:System.Web.Script.Serialization.JavascriptSerializer> はディクショナリを実際の JSON オブジェクトとして表します。  したがって、ASP.NET AJAX では、ディクショナリが次のように表されます。  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add(“one”, 1);  
d.Add(“two”, 2);  
```  
  
 このディクショナリは、JSON オブジェクトでは次のように表されます。  
  
-   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では \[{"Key":"one","Value":1},{"Key":"two","Value":2}\] と表され、  
  
-   ASP.NET AJAX <xref:System.Web.Script.Serialization.JavascriptSerializer> では、{“one”:1,”two”:2} と表されます。  
  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、キーの種類が文字列ではないディクショナリを処理でき、<xref:System.Web.Script.Serialization.JavascriptSerializer> はできません。この点で前者はより強力と言えます。  しかし、後者の方が JSON で使いやすいと言えます。  
  
 これらのシリアライザーの主な違いを次の表に示します。  
  
|相違点のカテゴリ|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|  
|--------------|--------------------------------|---------------------------------------|  
|空きバッファー \(新しい byte\[0\]\) の <xref:System.Object> \(または <xref:System.Uri>、あるいは他の一部のクラス\) への逆シリアル化|SerializationException|null|  
|<xref:System.DBNull.Value> のシリアル化|{} \(or {"\_\_type":"\#System"}\)|Null|  
|\[Serializable\] 型のプライベート メンバーのシリアル化|シリアル化できます|シリアル化できません|  
|<xref:System.Runtime.Serialization.ISerializable> 型のパブリック プロパティのシリアル化|シリアル化できません|シリアル化できます|  
|JSON の「拡張機能」|オブジェクト メンバー名で引用符を必要とする \({"a":"hello"}\) JSON 仕様に準拠しています。|引用符のないオブジェクト メンバー名 \({a:"hello"}\) をサポートします。|  
|<xref:System.DateTime> 協定世界時刻 \(UTC\)|"\\\/Date\(123456789U\)\\\/" 形式または "\\\/Date\\\(\\d\+\(U&#124;\(\\\+\\\-\[\\d{4}\]\)\)?  \\\)\\\\\/\)" 形式をサポートしません。|DateTime 値として、"\\\/Date\(123456789U\)\\\/" 形式と "\\\/Date\\\(\\d\+\(U&#124;\(\\\+\\\-\[\\d{4}\]\)\)?  \\\)\\\\\/\)" 形式をサポートします。|  
|ディクショナリの表現|KeyValuePair\<K,V\> の配列。文字列以外の種類のキーを処理します。|実際の JSON オブジェクトですが、文字列の種類のキーのみ処理します。|  
|エスケープ文字|必ず、エスケープ文字であるスラッシュ \(\/\) を付けます。"\\n" などのエスケープされない無効な JSON 文字は使用できません。|DateTime 値には、エスケープ文字スラッシュ \(\/\) を付けます。|  
  
## 参照  
 [方法 : 構成を使用して ASP.NET AJAX エンドポイントを追加する](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)