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
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="e7123-102">方法 : AJAX 対応 WCF サービスとこのサービスにアクセスする ASP.NET クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="e7123-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="e7123-103">ここでは、Visual Studio 2008 を使用して AJAX 対応の [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスと、このサービスにアクセスする ASP.NET クライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7123-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="e7123-104">これらを作成するための手順を示した後、「使用例」のセクションにサービスおよびクライアント用のコードを示します。</span><span class="sxs-lookup"><span data-stu-id="e7123-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="e7123-105">ASP.NET クライアント アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="e7123-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="e7123-106">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="e7123-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e7123-107">**ファイル**メニューの **新規**、し**プロジェクト**、し**Web**、し、 **のASP.NETWebアプリケーション**.</span><span class="sxs-lookup"><span data-stu-id="e7123-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="e7123-108">プロジェクトに名前を`SandwichServices` をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="e7123-109">WCF AJAX 対応サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="e7123-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="e7123-110">右クリックし、`SandwichServices`でプロジェクトを**ソリューション エクスプ ローラー**ウィンドウと選択**追加**、し**新しい項目の**、し**AJAX 対応 WCF サービス**.</span><span class="sxs-lookup"><span data-stu-id="e7123-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="e7123-111">サービスの名前を付けます`CostService`で、**名前**ボックスし、をクリックして**追加**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="e7123-112">CostService.svc.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="e7123-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="e7123-113">指定して、`Namespace`の<xref:System.ServiceModel.ServiceContractAttribute>として`SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="e7123-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
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
  
5.  <span data-ttu-id="e7123-114">サービスに操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="e7123-114">Implement the operations in the service.</span></span> <span data-ttu-id="e7123-115">コントラクトの一部であることを示すために、各操作に <xref:System.ServiceModel.OperationContractAttribute> を追加します。</span><span class="sxs-lookup"><span data-stu-id="e7123-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="e7123-116">次の例では、指定したサンドイッチの数に対して価格を返すメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7123-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="e7123-117">サービスにアクセスするようにクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="e7123-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="e7123-118">Default.aspx ページを開き、選択、**デザイン**ビュー。</span><span class="sxs-lookup"><span data-stu-id="e7123-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="e7123-119">**ビュー**メニューの **ツールボックス**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="e7123-120">展開して、 **AJAX Extensions**ノードやドラッグ アンド ドロップ、 **ScriptManager** Default.aspx ページ。</span><span class="sxs-lookup"><span data-stu-id="e7123-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="e7123-121">右クリックし、 **ScriptManager**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="e7123-122">展開、 **Services**内のコレクション、**プロパティ**ウィンドウを開きます、 **ServiceReference コレクション エディター**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="e7123-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="e7123-123">をクリックして**追加**、指定`CostService.svc`として、**パス** をクリックし、参照**OK**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="e7123-124">展開、 **HTML**内のノード、**ツールボックス**ドラッグ アンド ドロップし、**入力 (ボタン)** Default.aspx ページ。</span><span class="sxs-lookup"><span data-stu-id="e7123-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="e7123-125">右クリックし、**ボタン**選択**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="e7123-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="e7123-126">変更、**値**フィールドを`Price for 3 Sandwiches`です。</span><span class="sxs-lookup"><span data-stu-id="e7123-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="e7123-127">ダブルクリックして、**ボタン**JavaScript コードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e7123-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="e7123-128">内で次の JavaScript コードに渡す、<`script`> 要素。</span><span class="sxs-lookup"><span data-stu-id="e7123-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="e7123-129">クライアントからサービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="e7123-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="e7123-130">Ctrl キーを押しながら F5 キーを押して、サービスと Web クライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="e7123-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="e7123-131">クリックして、 **Price for 3 Sandwiches** 「3.75」の予想される出力を生成するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e7123-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7123-132">例</span><span class="sxs-lookup"><span data-stu-id="e7123-132">Example</span></span>  
 <span data-ttu-id="e7123-133">この例には、WCFService.svc.cs ファイルに含まれるサービスのコードと Default.aspx ファイルに含まれるクライアントのコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e7123-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
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
