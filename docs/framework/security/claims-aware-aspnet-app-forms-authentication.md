---
title: "方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 987157bc3663330d9c610c1016787890e9dc6137
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-application-using-forms-based-authentication"></a><span data-ttu-id="3d097-102">方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="3d097-102">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>
## <a name="applies-to"></a><span data-ttu-id="3d097-103">対象</span><span class="sxs-lookup"><span data-stu-id="3d097-103">Applies To</span></span>  
  
-   <span data-ttu-id="3d097-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="3d097-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="3d097-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="3d097-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3d097-106">概要</span><span class="sxs-lookup"><span data-stu-id="3d097-106">Summary</span></span>  
 <span data-ttu-id="3d097-107">この操作方法では、フォーム認証を使用する簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="3d097-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application that uses Forms authentication.</span></span> <span data-ttu-id="3d097-108">また、フォーム認証を使用してユーザーがサインインするときにクレームが表示されることを確認するために、アプリケーションをテストする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="3d097-108">It also provides instructions for how to test the application to verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="3d097-109">目次</span><span class="sxs-lookup"><span data-stu-id="3d097-109">Contents</span></span>  
  
-   <span data-ttu-id="3d097-110">目的</span><span class="sxs-lookup"><span data-stu-id="3d097-110">Objectives</span></span>  
  
-   <span data-ttu-id="3d097-111">概要</span><span class="sxs-lookup"><span data-stu-id="3d097-111">Overview</span></span>  
  
-   <span data-ttu-id="3d097-112">手順の要約</span><span class="sxs-lookup"><span data-stu-id="3d097-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3d097-113">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="3d097-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="3d097-114">手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="3d097-114">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="3d097-115">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="3d097-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="3d097-116">目的</span><span class="sxs-lookup"><span data-stu-id="3d097-116">Objectives</span></span>  
  
-   <span data-ttu-id="3d097-117">フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="3d097-117">Configure an ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
-   <span data-ttu-id="3d097-118">ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する</span><span class="sxs-lookup"><span data-stu-id="3d097-118">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="3d097-119">概要</span><span class="sxs-lookup"><span data-stu-id="3d097-119">Overview</span></span>  
 <span data-ttu-id="3d097-120">.NET 4.5 には、WIF とそのクレーム ベースの認証が、Framework の不可欠な部分として組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="3d097-120">In .NET 4.5, WIF and its claims-based authorization have been included as an integral part of the Framework.</span></span> <span data-ttu-id="3d097-121">以前は、ASP.NET ユーザーからのクレームが必要な場合に、WIF をインストールしてから、`Thread.CurrentPrincipal` または `HttpContext.Current.User` などのプリンシパル オブジェクトにインターフェイスをキャストする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="3d097-121">Previously, if you wanted claims from an ASP.NET user, you were required to install WIF, and then cast interfaces to Principal objects such as `Thread.CurrentPrincipal` or `HttpContext.Current.User`.</span></span> <span data-ttu-id="3d097-122">現在は、これらのプリンシパル オブジェクトで自動的にクレームが処理されます。</span><span class="sxs-lookup"><span data-stu-id="3d097-122">Now, claims are served automatically by these Principal objects.</span></span>  
  
 <span data-ttu-id="3d097-123">フォーム認証では、.NET 4.5 に組み込まれている WIF による利点が得られます。フォームで認証されたすべてのユーザーには自動的にクレームが関連付けられるためです。</span><span class="sxs-lookup"><span data-stu-id="3d097-123">Forms authentication has benefited from WIF’s inclusion in .NET 4.5 because all users authenticated by Forms automatically have claims associated with them.</span></span> <span data-ttu-id="3d097-124">この操作方法で示すように、フォーム認証を使用する ASP.NET アプリケーションでは、これらのクレームの使用をすぐに開始することができます。</span><span class="sxs-lookup"><span data-stu-id="3d097-124">You can begin using these claims immediately in an ASP.NET application that uses Forms authentication, as this How-To demonstrates.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="3d097-125">手順の要約</span><span class="sxs-lookup"><span data-stu-id="3d097-125">Summary of Steps</span></span>  
  
-   <span data-ttu-id="3d097-126">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="3d097-126">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="3d097-127">手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="3d097-127">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
  
-   <span data-ttu-id="3d097-128">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="3d097-128">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="3d097-129">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="3d097-129">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="3d097-130">この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d097-130">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="3d097-131">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="3d097-131">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="3d097-132">Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d097-132">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="3d097-133">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d097-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="3d097-134">**[名前]** で、「`TestApp`」と入力し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d097-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="3d097-135">手順 2 – フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="3d097-135">Step 2 – Configure ASP.NET Web Forms Application for Claims Using Forms Authentication</span></span>  
 <span data-ttu-id="3d097-136">この手順では、構成エントリを *Web.config* 構成ファイルに追加し、アカウントのクレーム情報を表示するように *Default.aspx* ファイルを編集します。</span><span class="sxs-lookup"><span data-stu-id="3d097-136">In this step you will add a configuration entry to the *Web.config* configuration file and edit the *Default.aspx* file to display claims information for an account.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-using-forms-authentication"></a><span data-ttu-id="3d097-137">フォーム認証を使用してクレーム用の ASP.NET アプリケーションを構成するには</span><span class="sxs-lookup"><span data-stu-id="3d097-137">To configure ASP.NET application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="3d097-138">*Default.aspx* ファイルの既存のマークアップを次のように置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3d097-138">In the *Default.aspx* file, replace the existing markup with the following:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
        <p>  
            This page displays the claims associated with a Forms authenticated user.          
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
  
     <span data-ttu-id="3d097-139">この手順では、GridView コントロールを *Default.aspx* ページに追加します。このページには、フォーム認証から取得されたクレームが取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="3d097-139">This step adds a GridView control to your *Default.aspx* page that will be populated with the claims retrieved from Forms authentication.</span></span>  
  
2.  <span data-ttu-id="3d097-140">*Default.aspx* ファイルを保存し、*Default.aspx.cs* という名前の分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3d097-140">Save the *Default.aspx* file, then open its code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="3d097-141">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3d097-141">Replace the existing code with the following:</span></span>  
  
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
  
                if (claimsPrincipal != null)  
                {  
                    this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                    this.ClaimsGridView.DataBind();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="3d097-142">上記のコードでは、認証済みユーザー (フォーム認証で特定されたユーザーを含む) に関する要求が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d097-142">The above code will display claims about an authenticated user, including users identified by Forms authentication.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="3d097-143">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="3d097-143">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="3d097-144">この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用してサインインするときに、クレームが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3d097-144">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="3d097-145">フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="3d097-145">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="3d097-146">**F5** キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="3d097-146">Press **F5** to build and run the application.</span></span> <span data-ttu-id="3d097-147">ページの右上には、**[登録]** と **[ログイン]** のリンクが表示される *Default.aspx* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d097-147">You should be presented with *Default.aspx*, which has **Register** and **Log in** links in the top right of the page.</span></span> <span data-ttu-id="3d097-148">**[登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d097-148">Click **Register**.</span></span>  
  
2.  <span data-ttu-id="3d097-149">**[登録]** ページで、ユーザーアカウントを作成し、**[登録]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3d097-149">On the **Register** page, create a user account, and then click **Register**.</span></span> <span data-ttu-id="3d097-150">フォーム認証を使用してアカウントが作成され、自動的にサインインされます。</span><span class="sxs-lookup"><span data-stu-id="3d097-150">Your account will be created using Forms authentication, and you will be automatically signed in.</span></span>  
  
3.  <span data-ttu-id="3d097-151">ホーム ページにリダイレクトされたら、**Your Claims** 見出しの下の表に、アカウントに関する **Issuer**、**OriginalIssuer**、**Type**、**Value**、および **ValueType** 要求情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d097-151">After you have been redirected to the home page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span>
