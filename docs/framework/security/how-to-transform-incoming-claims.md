---
title: "方法: 入力方向の要求の変換"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bcf0e640e6b6b45ddb87070c7d6df2fa6dadc834
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-incoming-claims"></a><span data-ttu-id="d004e-102">方法: 入力方向の要求の変換</span><span class="sxs-lookup"><span data-stu-id="d004e-102">How To: Transform Incoming Claims</span></span>
## <a name="applies-to"></a><span data-ttu-id="d004e-103">対象</span><span class="sxs-lookup"><span data-stu-id="d004e-103">Applies To</span></span>  
  
-   <span data-ttu-id="d004e-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="d004e-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="d004e-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="d004e-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="d004e-106">概要</span><span class="sxs-lookup"><span data-stu-id="d004e-106">Summary</span></span>  
 <span data-ttu-id="d004e-107">この操作方法では、単純なクレーム対応 ASP.NET Web フォーム アプリケーションを作成、受信した要求を変換する詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="d004e-107">This How-To provides detailed step-by-step procedures for creating a simple claims-aware ASP.NET Web Forms application and transforming incoming claims.</span></span> <span data-ttu-id="d004e-108">また、アプリケーションの実行中に変換されたクレームが表示されることを確認するためにアプリケーションをテストする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d004e-108">It also provides instructions for how to test the application to verify that transformed claims are presented when the application is run.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="d004e-109">目次</span><span class="sxs-lookup"><span data-stu-id="d004e-109">Contents</span></span>  
  
-   <span data-ttu-id="d004e-110">目的</span><span class="sxs-lookup"><span data-stu-id="d004e-110">Objectives</span></span>  
  
-   <span data-ttu-id="d004e-111">概要</span><span class="sxs-lookup"><span data-stu-id="d004e-111">Overview</span></span>  
  
-   <span data-ttu-id="d004e-112">手順の要約</span><span class="sxs-lookup"><span data-stu-id="d004e-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d004e-113">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d004e-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="d004e-114">手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する</span><span class="sxs-lookup"><span data-stu-id="d004e-114">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="d004e-115">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="d004e-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="d004e-116">目的</span><span class="sxs-lookup"><span data-stu-id="d004e-116">Objectives</span></span>  
  
-   <span data-ttu-id="d004e-117">クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="d004e-117">Configure an ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="d004e-118">管理者ロールのクレームを追加することによって、受信したクレームを変換します。</span><span class="sxs-lookup"><span data-stu-id="d004e-118">Transform incoming claims by adding an Administrator role claim</span></span>  
  
-   <span data-ttu-id="d004e-119">ASP.NET Web フォーム アプリケーションをテストして正しく機能することを確認する</span><span class="sxs-lookup"><span data-stu-id="d004e-119">Test the ASP.NET Web Forms application to see if it is working properly</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d004e-120">概要</span><span class="sxs-lookup"><span data-stu-id="d004e-120">Overview</span></span>  
 <span data-ttu-id="d004e-121">WIF が <xref:System.Security.Claims.ClaimsAuthenticationManager> という名前のクラスを公開し、これを使用してユーザーは、クレームが利用者 (RP) アプリケーションに表示される前に、クレームを変更できます。</span><span class="sxs-lookup"><span data-stu-id="d004e-121">WIF exposes a class named <xref:System.Security.Claims.ClaimsAuthenticationManager> that enables users to modify claims before they are presented to a relying party (RP) application.</span></span> <span data-ttu-id="d004e-122"><xref:System.Security.Claims.ClaimsAuthenticationManager> は、認証と基になるアプリケーション コードの間での問題の分離に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d004e-122">The <xref:System.Security.Claims.ClaimsAuthenticationManager> is useful for separation of concerns between authentication and the underlying application code.</span></span> <span data-ttu-id="d004e-123">次の例は、RP で必要になる場合がある着信 <xref:System.Security.Claims.ClaimsPrincipal> 内のクレームにロールを追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d004e-123">The example below demonstrates how to add a role to the claims in the incoming <xref:System.Security.Claims.ClaimsPrincipal> that may be required by the RP.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="d004e-124">手順の要約</span><span class="sxs-lookup"><span data-stu-id="d004e-124">Summary of Steps</span></span>  
  
-   <span data-ttu-id="d004e-125">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d004e-125">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="d004e-126">手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する</span><span class="sxs-lookup"><span data-stu-id="d004e-126">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
  
-   <span data-ttu-id="d004e-127">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="d004e-127">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="d004e-128">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="d004e-128">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="d004e-129">この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d004e-129">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="d004e-130">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="d004e-130">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="d004e-131">システム特権のあるモードで管理者として Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="d004e-131">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="d004e-132">Visual Studio で、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-132">In Visual Studio, click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="d004e-133">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-133">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
4.  <span data-ttu-id="d004e-134">**[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="d004e-134">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
5.  <span data-ttu-id="d004e-135">**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d004e-135">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
6.  <span data-ttu-id="d004e-136">**[Identity and Access]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d004e-136">The **Identity and Access** window appears.</span></span> <span data-ttu-id="d004e-137">**[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-137">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
7.  <span data-ttu-id="d004e-138">*Default.aspx* ファイルの既存のマークアップを次のものに置き換え、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d004e-138">In the *Default.aspx* file, replace the existing markup with the following, then save the file:</span></span>  
  
    ```  
    <%@ Page Title="Home Page" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true"  
        CodeBehind="Default.aspx.cs" Inherits="TestApp._Default" %>  
  
    <asp:Content runat="server" ID="BodyContent" ContentPlaceHolderID="MainContent">  
          <h3>Your Claims</h3>  
        <p>  
            <asp:GridView ID="ClaimsGridView" runat="server" CellPadding="3">  
                <AlternatingRowStyle BackColor="White" />  
                <HeaderStyle BackColor="#7AC0DA" ForeColor="White" />  
            </asp:GridView>  
        </p>  
    </asp:Content>  
    ```  
  
8.  <span data-ttu-id="d004e-139">*Default.aspx.cs* という名前の分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d004e-139">Open the code-behind file named *Default.aspx.cs*.</span></span> <span data-ttu-id="d004e-140">既存のコードを次のコードに置き換え、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d004e-140">Replace the existing code with the following, then save the file:</span></span>  
  
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
  
## <a name="step-2--implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="d004e-141">手順 2 – カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装する</span><span class="sxs-lookup"><span data-stu-id="d004e-141">Step 2 – Implement Claims Transformation Using a Custom ClaimsAuthenticationManager</span></span>  
 <span data-ttu-id="d004e-142">この手順では、<xref:System.Security.Claims.ClaimsAuthenticationManager> クラスの既定の機能を上書きし、受信プリンシパルに管理者ロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="d004e-142">In this step you will override default functionality in the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to add an Administrator role to the incoming Principal.</span></span>  
  
#### <a name="to-implement-claims-transformation-using-a-custom-claimsauthenticationmanager"></a><span data-ttu-id="d004e-143">カスタム ClaimsAuthenticationManager を使用してクレーム変換を実装するには</span><span class="sxs-lookup"><span data-stu-id="d004e-143">To implement claims transformation using a custom ClaimsAuthenticationManager</span></span>  
  
1.  <span data-ttu-id="d004e-144">Visual Studio でソリューションを右クリックし、**[追加]** をクリックして **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-144">In Visual Studio, right-click the on the solution, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="d004e-145">**[新しいプロジェクトの追加]** ウィンドウで、**[Visual C#]** テンプレート一覧から **[クラス ライブラリ]** を選択し、「`ClaimsTransformation`」と入力して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-145">In the **Add New Project** window, select **Class Library** from the **Visual C#** templates list, enter `ClaimsTransformation`, and then press **OK**.</span></span> <span data-ttu-id="d004e-146">新しいプロジェクトがソリューション フォルダーに作成されます。</span><span class="sxs-lookup"><span data-stu-id="d004e-146">The new project will be created in your solution folder.</span></span>  
  
3.  <span data-ttu-id="d004e-147">**[ClaimsTransformation]** プロジェクトの下の **[参照]** を右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-147">Right-click on **References** under the **ClaimsTransformation** project, and then click **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="d004e-148">**参照マネージャー** ウィンドウで、**System.IdentityModel** を選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-148">In the **Reference Manager** window, select **System.IdentityModel**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="d004e-149">**Class1.cs** を開くか、存在しない場合は **ClaimsTransformation** を右クリックして、**[追加]** をクリックし、**[クラス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-149">Open **Class1.cs**, or if it doesn’t exist, right-click **ClaimsTransformation**, click **Add**, then click **Class…**</span></span>  
  
6.  <span data-ttu-id="d004e-150">ディレクティブを使用して以下をコード ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d004e-150">Add the following using directives to the code file:</span></span>  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  <span data-ttu-id="d004e-151">次のクラスとメソッドをコード ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d004e-151">Add the following class and method in the code file.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="d004e-152">次のコードは、デモの目的でのみ使用します。実稼働コードで、目的のアクセス許可を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d004e-152">The following code is for demonstration purposes only; make sure that you verify your intended permissions in production code.</span></span>  
  
    ```csharp  
    public class ClaimsTransformationModule : ClaimsAuthenticationManager  
    {  
        public override ClaimsPrincipal Authenticate(string resourceName, ClaimsPrincipal incomingPrincipal)  
        {  
            if (incomingPrincipal != null && incomingPrincipal.Identity.IsAuthenticated == true)  
            {  
               ((ClaimsIdentity)incomingPrincipal.Identity).AddClaim(new Claim(ClaimTypes.Role, "Admin"));  
            }  
  
            return incomingPrincipal;  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="d004e-153">ファイルを保存し、**ClaimsTransformation** プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d004e-153">Save the file and build the **ClaimsTransformation** project.</span></span>  
  
9. <span data-ttu-id="d004e-154">**TestApp** ASP.NET プロジェクトで、[参照] を右クリックし、**[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-154">In your **TestApp** ASP.NET project, right-click on References, and then click **Add Reference**.</span></span>  
  
10. <span data-ttu-id="d004e-155">**参照マネージャー** ウィンドウで、左側のメニューから **[ソリューション]** を選択し、設定されたオプションから **ClaimsTransformation** を選択し、**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d004e-155">In the **Reference Manager** window, select **Solution** from the left menu, select **ClaimsTransformation** from the populated options, and then click **OK**.</span></span>  
  
11. <span data-ttu-id="d004e-156">ルートの **Web.config**ファイルで、**\<system.identityMode >** エントリに移動します。</span><span class="sxs-lookup"><span data-stu-id="d004e-156">In the root **Web.config** file, navigate to the **\<system.identityModel>** entry.</span></span> <span data-ttu-id="d004e-157">**\<identityConfiguration >** 要素内で、次の行を追加し、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="d004e-157">Within the **\<identityConfiguration>** elements, add the following line and save the file:</span></span>  
  
    ```xml  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="d004e-158">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="d004e-158">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="d004e-159">この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用してサインインするときに、クレームが表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d004e-159">In this step you will test your ASP.NET Web Forms application, and verify that claims are presented when a user signs in with Forms authentication.</span></span>  
  
#### <a name="to-test-your-aspnet-web-forms-application-for-claims-using-forms-authentication"></a><span data-ttu-id="d004e-160">フォーム認証を使用してクレーム用の ASP.NET Web フォーム アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="d004e-160">To test your ASP.NET Web Forms application for claims using Forms authentication</span></span>  
  
1.  <span data-ttu-id="d004e-161">**F5** キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="d004e-161">Press **F5** to build and run the application.</span></span> <span data-ttu-id="d004e-162">*Default.aspx* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d004e-162">You should be presented with *Default.aspx*.</span></span>  
  
2.  <span data-ttu-id="d004e-163">*Default.aspx* ページで、**Your Claims** 見出しの下の表に、アカウントに関する **Issuer**、**OriginalIssuer**、**Type**、**Value**、および**ValueType** クレーム情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d004e-163">On the *Default.aspx* page, you should see a table beneath the **Your Claims** heading that includes the **Issuer**, **OriginalIssuer**, **Type**, **Value**, and **ValueType** claims information about your account.</span></span> <span data-ttu-id="d004e-164">最後の行は、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="d004e-164">The last row should be presented in the following way:</span></span>  
  
    ||||||  
    |-|-|-|-|-|  
    |<span data-ttu-id="d004e-165">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="d004e-165">LOCAL AUTHORITY</span></span>|<span data-ttu-id="d004e-166">LOCAL AUTHORITY</span><span class="sxs-lookup"><span data-stu-id="d004e-166">LOCAL AUTHORITY</span></span>|<span data-ttu-id="d004e-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span><span class="sxs-lookup"><span data-stu-id="d004e-167">http://schemas.microsoft.com/ws/2008/06/identity/claims/role</span></span>|<span data-ttu-id="d004e-168">管理</span><span class="sxs-lookup"><span data-stu-id="d004e-168">Admin</span></span>|<span data-ttu-id="d004e-169">http://www.w3.org/2001/XMLSchema#string</span><span class="sxs-lookup"><span data-stu-id="d004e-169">http://www.w3.org/2001/XMLSchema#string</span></span>|
