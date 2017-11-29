---
title: "方法: Windows 認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 676a03678cbdf6fe08e628806df2a1853fb71718
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-windows-authentication"></a><span data-ttu-id="2ce43-102">方法: Windows 認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="2ce43-102">How To: Build Claims-Aware ASP.NET Application Using Windows Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="2ce43-103">対象</span><span class="sxs-lookup"><span data-stu-id="2ce43-103">Applies To</span></span>  
  
-   <span data-ttu-id="2ce43-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="2ce43-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="2ce43-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="2ce43-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="2ce43-106">概要</span><span class="sxs-lookup"><span data-stu-id="2ce43-106">Summary</span></span>  
 <span data-ttu-id="2ce43-107">この操作方法では、Windows 認証を使用する簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Windows authentication.</span></span> <span data-ttu-id="2ce43-108">また、Windows 認証を使用してユーザーがサインインするときにクレームが表示されることを確認するために、アプリケーションをテストする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in using Windows authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="2ce43-109">目次</span><span class="sxs-lookup"><span data-stu-id="2ce43-109">Contents</span></span>  
  
-   <span data-ttu-id="2ce43-110">目的</span><span class="sxs-lookup"><span data-stu-id="2ce43-110">Objectives</span></span>  
  
-   <span data-ttu-id="2ce43-111">概要</span><span class="sxs-lookup"><span data-stu-id="2ce43-111">Overview</span></span>  
  
-   <span data-ttu-id="2ce43-112">手順の要約</span><span class="sxs-lookup"><span data-stu-id="2ce43-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="2ce43-113">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="2ce43-114">手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="2ce43-115">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="2ce43-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="2ce43-116">目的</span><span class="sxs-lookup"><span data-stu-id="2ce43-116">Objectives</span></span>  
  
-   <span data-ttu-id="2ce43-117">Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-117">Configure an ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
-   <span data-ttu-id="2ce43-118">ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する</span><span class="sxs-lookup"><span data-stu-id="2ce43-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="2ce43-119">概要</span><span class="sxs-lookup"><span data-stu-id="2ce43-119">Overview</span></span>  
 <span data-ttu-id="2ce43-120">.NET 4.5 には、WIF とそのクレーム ベースの認証が、Framework の不可欠な部分として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="2ce43-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="2ce43-121">以前は、ASP.NET ユーザーからのクレームが必要な場合に、WIF をインストールしてから、`Thread.CurrentPrincipal` または `HttpContext.Current.User` などのプリンシパル オブジェクトにインターフェイスをキャストする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="2ce43-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="2ce43-122">現在は、これらのプリンシパル オブジェクトで自動的にクレームが処理されます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="2ce43-123">Windows 認証では、.NET 4.5 に組み込まれている WIF による利点が得られます。Windows 資格情報で認証されたすべてのユーザーには自動的にクレームが関連付けられるためです。</span><span class="sxs-lookup"><span data-stu-id="2ce43-123">Windows authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Windows credentials automatically have claims associated with them.</span></span> <span data-ttu-id="2ce43-124">この操作方法で示すように、Windows 認証を使用する ASP.NET アプリケーションでは、これらのクレームの使用をすぐに開始することができます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-124">You can begin using these claims immediately in an ASP.NET application that uses Windows authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="2ce43-125">手順の要約</span><span class="sxs-lookup"><span data-stu-id="2ce43-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="2ce43-126">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="2ce43-127">手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
  
-   <span data-ttu-id="2ce43-128">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="2ce43-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="2ce43-129">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="2ce43-130">この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="2ce43-131">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="2ce43-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="2ce43-132">Visual Studio を起動してから、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce43-132">Start Visual Studio, then click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="2ce43-133">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce43-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="2ce43-134">**[名前]** で、「`TestApp`」と入力して **[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="2ce43-135">**TestApp** プロジェクトが作成されたら、**ソリューション エクスプローラー**でそれをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ce43-135">After the **TestApp** project has been created, click on it in **Solution Explorer**.</span></span> <span data-ttu-id="2ce43-136">プロジェクトのプロパティが、**ソリューション エクスプローラー**の下の **[プロパティ]** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-136">The project’s properties will appear in the **Properties** pane below **Solution Explorer**.</span></span> <span data-ttu-id="2ce43-137">**[Windows 認証]** プロパティを **[有効]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-137">Set the **Windows Authentication** property to **Enabled**.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="2ce43-138">新しい ASP.NET アプリケーションでは Windows 認証が既定で無効になるため、手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ce43-138">Windows authentication is disabled by default in new ASP.NET applications, so you must manually enable it.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="2ce43-139">手順 2 – Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="2ce43-139">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Windows Authentication</span></span>  
 <span data-ttu-id="2ce43-140">この手順では、構成エントリを *Web.config* 構成ファイルに追加し、アカウントのクレーム情報を表示するように *Default.aspx* ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-140">In this step you will add a configuration entry to the *Web.config* configuration file and modify the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-windows-authentication"></a><span data-ttu-id="2ce43-141">Windows 認証を使用してクレーム用の ASP.NET アプリケーションを構成するには</span><span class="sxs-lookup"><span data-stu-id="2ce43-141">To configure ASP.NET application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="2ce43-142">**TestApp** プロジェクトの *Default.aspx* ファイルで、既存のマークアップを次のものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-142">In the **TestApp** project’s *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Windows authenticated user.          
        </p>  
        <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
     <span data-ttu-id="2ce43-143">この手順では GridView コントロールを *Default.aspx* ページに追加します。このページには、Windows 認証から取得されたクレームが取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-143">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Windows authentication.</span></span>  
  
2.  <span data-ttu-id="2ce43-144">*Default.aspx* ファイルを保存し、*Default.aspx.cs* という名前の分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-144">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="2ce43-145">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-145">Replace the existing code with the following:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        public partial class _Default : Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Page.User as ClaimsPrincipal;  
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="2ce43-146">上記のコードでは、認証ユーザーに関するクレームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ce43-146">The above code will display claims about an authenticated user.</span></span>  
  
3.  <span data-ttu-id="2ce43-147">アプリケーションの認証の種類を変更するには、プロジェクトのルート *Web.config* ファイルの **\<system.web>** セクション内の **\<authentication>** ブロックを変更して、以下の構成エントリのみが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="2ce43-147">To change the application’s authentication type, modify the **\<authentication>** block in the **\<system.web>** section of the project’s root *Web.config* file so that it only includes the following configuration entry:</span></span>  
  
    ```xml  
    <authentication mode="Windows" />  
    ```  
  
4.  <span data-ttu-id="2ce43-148">最後に、同じ *Web.config* ファイルの **\<system.web>** セクション内の **\<authorization>** ブロックを変更して、認証を強制します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-148">Finally, modify the **\<authorization>** block in the **\<system.web>** section of the same *Web.config* file to force authentication:</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="2ce43-149">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="2ce43-149">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="2ce43-150">この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーが Windows 認証を使用してサインインするときに、クレームが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-150">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Windows authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-windows-authentication"></a><span data-ttu-id="2ce43-151">Windows 認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="2ce43-151">To test your ASP.NET Web Forms application for claims using Windows authentication</span></span>  
  
1.  <span data-ttu-id="2ce43-152">**F5** キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="2ce43-152">Press **F5** to build and run the application.</span></span> <span data-ttu-id="2ce43-153">*Default.aspx* が表示されます。Windows アカウント名 (ドメイン名を含む) は、ページの右上に認証ユーザーとして既に表示されています。</span><span class="sxs-lookup"><span data-stu-id="2ce43-153">You should be presented with *Default.aspx*, and your Windows account name (including domain name) should already appear as the authenticated user in the top right of the page.</span></span> <span data-ttu-id="2ce43-154">ページの内容には、Windows アカウントから取得されたクレームが入力されたテーブルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ce43-154">The page’s content should include a table filled with claims retrieved from your Windows account.</span></span>
