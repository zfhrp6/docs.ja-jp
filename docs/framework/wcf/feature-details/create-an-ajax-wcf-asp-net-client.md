---
title: "方法 : AJAX 対応 WCF サービスとこのサービスにアクセスする ASP.NET クライアントを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b136565730c1b3175abff8b057a69acc6609a44d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>方法 : AJAX 対応 WCF サービスとこのサービスにアクセスする ASP.NET クライアントを作成する
ここでは、Visual Studio 2008 を使用して AJAX 対応の [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスと、このサービスにアクセスする ASP.NET クライアントを作成する方法について説明します。 これらを作成するための手順を示した後、「使用例」のセクションにサービスおよびクライアント用のコードを示します。  
  
### <a name="to-create-the-aspnet-client-application"></a>ASP.NET クライアント アプリケーションを作成するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。  
  
2.  **ファイル**メニューの **新規**、し**プロジェクト**、し**Web**、し、 **のASP.NETWebアプリケーション**.  
  
3.  プロジェクトに名前を`SandwichServices` をクリック**OK**です。  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>WCF AJAX 対応サービスを作成するには  
  
1.  右クリックし、`SandwichServices`でプロジェクトを**ソリューション エクスプ ローラー**ウィンドウと選択**追加**、し**新しい項目の**、し**AJAX 対応 WCF サービス**.  
  
2.  サービスの名前を付けます`CostService`で、**名前**ボックスし、をクリックして**追加**です。  
  
3.  CostService.svc.cs ファイルを開きます。  
  
4.  指定して、`Namespace`の<xref:System.ServiceModel.ServiceContractAttribute>として`SandwichService`:  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  サービスに操作を実装します。 コントラクトの一部であることを示すために、各操作に <xref:System.ServiceModel.OperationContractAttribute> を追加します。 次の例では、指定したサンドイッチの数に対して価格を返すメソッドを実装します。  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a>サービスにアクセスするようにクライアントを構成するには  
  
1.  Default.aspx ページを開き、選択、**デザイン**ビュー。  
  
2.  **ビュー**メニューの **ツールボックス**です。  
  
3.  展開して、 **AJAX Extensions**ノードやドラッグ アンド ドロップ、 **ScriptManager** Default.aspx ページ。  
  
4.  右クリックし、 **ScriptManager**選択**プロパティ**です。  
  
5.  展開、 **Services**内のコレクション、**プロパティ**ウィンドウを開きます、 **ServiceReference コレクション エディター**ウィンドウです。  
  
6.  をクリックして**追加**、指定`CostService.svc`として、**パス** をクリックし、参照**OK**です。  
  
7.  展開、 **HTML**内のノード、**ツールボックス**ドラッグ アンド ドロップし、**入力 (ボタン)** Default.aspx ページ。  
  
8.  右クリックし、**ボタン**選択**プロパティ**です。  
  
9. 変更、**値**フィールドを`Price for 3 Sandwiches`です。  
  
10. ダブルクリックして、**ボタン**JavaScript コードにアクセスします。  
  
11. 内で次の JavaScript コードに渡す、<`script`> 要素。  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>クライアントからサービスにアクセスするには  
  
1.  Ctrl キーを押しながら F5 キーを押して、サービスと Web クライアントを起動します。 クリックして、 **Price for 3 Sandwiches** 「3.75」の予想される出力を生成するボタンをクリックします。  
  
## <a name="example"></a>例  
 この例には、WCFService.svc.cs ファイルに含まれるサービスのコードと Default.aspx ファイルに含まれるクライアントのコードが含まれています。  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     
