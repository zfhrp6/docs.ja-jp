---
title: "方法: WIF を使用してサインイン状態を表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d1174e4-5397-4962-9a5f-3b1ad7b3fc14
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 494e67b39187a2a38f29f994e17051430d90f708
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-signed-in-status-using-wif"></a><span data-ttu-id="6322b-102">方法: WIF を使用してサインイン状態を表示する</span><span class="sxs-lookup"><span data-stu-id="6322b-102">How To: Display Signed In Status Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="6322b-103">対象</span><span class="sxs-lookup"><span data-stu-id="6322b-103">Applies To</span></span>  
  
-   <span data-ttu-id="6322b-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span><span class="sxs-lookup"><span data-stu-id="6322b-104">Microsoft® Windows® Identity Foundation (WIF) 4.5</span></span>  
  
-   <span data-ttu-id="6322b-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="6322b-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="6322b-106">概要</span><span class="sxs-lookup"><span data-stu-id="6322b-106">Summary</span></span>  
 <span data-ttu-id="6322b-107">このトピックでは、WIF 対応 ASP.NET アプリケーションでサインイン状態を表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-107">This topic describes how to display the sign in status in a WIF-enabled ASP.NET application.</span></span> <span data-ttu-id="6322b-108">WIF には、アプリケーションでクレームが認識されるようにする機能、およびアプリケーション リソースの認証と承認を管理する機能があります。</span><span class="sxs-lookup"><span data-stu-id="6322b-108">WIF provides the mechanism for making your application claims-aware, and managing authentication and authorization for application resources.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="6322b-109">目次</span><span class="sxs-lookup"><span data-stu-id="6322b-109">Contents</span></span>  
  
-   <span data-ttu-id="6322b-110">概要</span><span class="sxs-lookup"><span data-stu-id="6322b-110">Overview</span></span>  
  
-   <span data-ttu-id="6322b-111">手順の要約</span><span class="sxs-lookup"><span data-stu-id="6322b-111">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6322b-112">手順 1 – Identity and Access 拡張機能をインストールする</span><span class="sxs-lookup"><span data-stu-id="6322b-112">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="6322b-113">手順 2 – 証明書利用者の ASP.NET アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="6322b-113">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="6322b-114">手順 3 – ユーザー認証のためのローカル開発用 STS の有効化</span><span class="sxs-lookup"><span data-stu-id="6322b-114">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="6322b-115">手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する</span><span class="sxs-lookup"><span data-stu-id="6322b-115">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="6322b-116">手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト</span><span class="sxs-lookup"><span data-stu-id="6322b-116">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6322b-117">概要</span><span class="sxs-lookup"><span data-stu-id="6322b-117">Overview</span></span>  
 <span data-ttu-id="6322b-118">このトピックでは、WIF を使用して簡単なクレーム対応アプリケーションを作成する方法と、ユーザーがサインインしているかどうかを簡単に表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-118">This topic demonstrates how to create a simple claims-aware application using WIF and how to easily display whether a user is signed in or not.</span></span> <span data-ttu-id="6322b-119">次の手順では、Visual Studio の Identity and Access 拡張機能に含まれるローカル開発用 STS を使用します。</span><span class="sxs-lookup"><span data-stu-id="6322b-119">The following steps use the Local Development STS that is included with the Identity and Access Visual Studio Extension.</span></span> <span data-ttu-id="6322b-120">ローカル開発用 STS は、アプリケーションにクレームを統合する簡単な方法を提供する目的で、テストおよび開発環境向けに用意されたものです。</span><span class="sxs-lookup"><span data-stu-id="6322b-120">The Local Development STS is intended for a testing and development environment to provide a simple method of integrating claims into your application.</span></span> <span data-ttu-id="6322b-121">これは、実際の認証を行わず、資格情報も不要なため、稼動環境で使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6322b-121">It should never be used in a production environment, as it does not perform real authentication and credentials are not required.</span></span> <span data-ttu-id="6322b-122">ただし、次の手順の命令型コードは、実際の認証を使用した運用環境で使用できるアプリケーションの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="6322b-122">However, the imperative code in the following steps is the same for a production-ready application using real authentication.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="6322b-123">手順の要約</span><span class="sxs-lookup"><span data-stu-id="6322b-123">Summary of Steps</span></span>  
  
-   <span data-ttu-id="6322b-124">手順 1 – Identity and Access 拡張機能をインストールする</span><span class="sxs-lookup"><span data-stu-id="6322b-124">Step 1 – Install the Identity and Access Extension</span></span>  
  
-   <span data-ttu-id="6322b-125">手順 2 – 証明書利用者の ASP.NET アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="6322b-125">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
  
-   <span data-ttu-id="6322b-126">手順 3 – ユーザー認証のためのローカル開発用 STS の有効化</span><span class="sxs-lookup"><span data-stu-id="6322b-126">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
  
-   <span data-ttu-id="6322b-127">手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する</span><span class="sxs-lookup"><span data-stu-id="6322b-127">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
  
-   <span data-ttu-id="6322b-128">手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト</span><span class="sxs-lookup"><span data-stu-id="6322b-128">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
  
## <a name="step-1--install-the-identity-and-access-extension"></a><span data-ttu-id="6322b-129">手順 1 – Identity and Access 拡張機能をインストールする</span><span class="sxs-lookup"><span data-stu-id="6322b-129">Step 1 – Install the Identity and Access Extension</span></span>  
 <span data-ttu-id="6322b-130">この手順では、Identity and Access 拡張機能を Visual Studio 2012 用に構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-130">This step describes how to configure the Identity and Access extension to Visual Studio 2012.</span></span> <span data-ttu-id="6322b-131">この拡張機能により、STS エンドポイントと通信するようにアプリケーションを構成するプロセスが自動化されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-131">This extension automates the process of configuring your application to communicate with STS endpoints.</span></span>  
  
#### <a name="to-install-the-identity-and-access-extension"></a><span data-ttu-id="6322b-132">Identity and Access 拡張機能をインストールするには</span><span class="sxs-lookup"><span data-stu-id="6322b-132">To install the Identity and Access extension</span></span>  
  
1.  <span data-ttu-id="6322b-133">システム特権のあるモードで管理者として Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="6322b-133">Start Visual Studio in elevated mode as administrator.</span></span>  
  
2.  <span data-ttu-id="6322b-134">Visual Studio で、**[ツール]**、**[拡張機能マネージャー]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-134">In Visual Studio, click **Tools** and click **Extension Manager**.</span></span> <span data-ttu-id="6322b-135">**[拡張機能マネージャー]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-135">The **Extension Manager** window appears.</span></span>  
  
3.  <span data-ttu-id="6322b-136">**拡張機能マネージャー**の左側のメニューで **[オンラインの拡張機能]** をクリックしてから、**[Visual Studio ギャラリー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6322b-136">In **Extension Manager**, click **Online Extensions** from the left menu, then select **Visual Studio Gallery**.</span></span>  
  
4.  <span data-ttu-id="6322b-137">**拡張機能マネージャー**の右上隅で、*Identity and Access* を検索します。</span><span class="sxs-lookup"><span data-stu-id="6322b-137">In the top right corner of **Extension Manager**, search for *Identity and Access*.</span></span>  
  
5.  <span data-ttu-id="6322b-138">**Identity and Access** の項目が検索結果に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-138">The **Identity and Access** item will appear in the search results.</span></span> <span data-ttu-id="6322b-139">それをクリックしてから、**[ダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-139">Click it, and then click **Download**.</span></span>  
  
6.  <span data-ttu-id="6322b-140">**[ダウンロードとインストール]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-140">The **Download and Install** dialog appears.</span></span> <span data-ttu-id="6322b-141">ライセンス条項に同意する場合は、**[インストール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-141">If you agree with the license terms, click **Install**.</span></span>  
  
7.  <span data-ttu-id="6322b-142">**Identity and Access** の拡張機能のインストールが終了したら、管理者モードで Visual Studio を再起動します。</span><span class="sxs-lookup"><span data-stu-id="6322b-142">When the **Identity and Access** extension has finished installing, restart Visual Studio in administrator mode.</span></span>  
  
## <a name="step-2--create-a-relying-party-aspnet-application"></a><span data-ttu-id="6322b-143">手順 2 – 証明書利用者の ASP.NET アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="6322b-143">Step 2 – Create a Relying Party ASP.NET Application</span></span>  
 <span data-ttu-id="6322b-144">この手順では、WIF と統合する証明書利用者の ASP.NET Web フォーム アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-144">This step describes how to create a relying party ASP.NET Web Forms application that will integrate with WIF.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="6322b-145">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="6322b-145">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="6322b-146">Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-146">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="6322b-147">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-147">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="6322b-148">**[名前]** で、「`TestApp`」と入力し、**[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="6322b-148">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-3--enable-local-development-sts-to-authenticate-users"></a><span data-ttu-id="6322b-149">手順 3 – ユーザー認証のためのローカル開発用 STS の有効化</span><span class="sxs-lookup"><span data-stu-id="6322b-149">Step 3 – Enable Local Development STS to Authenticate Users</span></span>  
 <span data-ttu-id="6322b-150">この手順では、アプリケーションでローカル開発用 STS を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-150">This step describes how to enable Local Development STS in your application.</span></span> <span data-ttu-id="6322b-151">ローカル開発用 STS は、Visual Studio 用の Identity and Access 拡張機能を使用することによって有効になります。</span><span class="sxs-lookup"><span data-stu-id="6322b-151">Local Development STS is enabled by using the Identity and Access extension for Visual Studio.</span></span>  
  
#### <a name="to-enable-local-development-sts-in-your-aspnet-application"></a><span data-ttu-id="6322b-152">ASP.NET アプリケーションでローカル開発用 STS を有効にするには</span><span class="sxs-lookup"><span data-stu-id="6322b-152">To enable Local Development STS in your ASP.NET application</span></span>  
  
1.  <span data-ttu-id="6322b-153">Visual Studio の**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックし、**[Identity and Access]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6322b-153">In Visual Studio, right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>  
  
2.  <span data-ttu-id="6322b-154">**[Identity and Access]** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-154">The **Identity and Access** window appears.</span></span> <span data-ttu-id="6322b-155">**[Providers]** で **[Test your application with the Local Development STS]** を選択し、**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6322b-155">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>  
  
## <a name="step-4--modify-your-aspnet-application-to-display-sign-in-status"></a><span data-ttu-id="6322b-156">手順 4 – ASP.NET アプリケーションを変更してサインイン状態を表示する</span><span class="sxs-lookup"><span data-stu-id="6322b-156">Step 4 – Modify Your ASP.NET Application to Display Sign In Status</span></span>  
 <span data-ttu-id="6322b-157">この手順では、現在のユーザーがサインインしているかどうかを動的に表示するように ASP.NET アプリケーションを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-157">This step describes how to modify your ASP.NET application to dynamically display whether the current user is signed in.</span></span> <span data-ttu-id="6322b-158">STS プロバイダーを構成すると、WIF は受信クレームを処理します。</span><span class="sxs-lookup"><span data-stu-id="6322b-158">Once your STS provider has been configured, WIF handles the incoming claims.</span></span> <span data-ttu-id="6322b-159">次に、認証の結果を表示するために、アプリケーション コードを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6322b-159">Now you need to configure your application’s code to display the result of the authentication.</span></span>  
  
#### <a name="to-display-sign-in-status"></a><span data-ttu-id="6322b-160">サインイン状態を表示するには</span><span class="sxs-lookup"><span data-stu-id="6322b-160">To display sign in status</span></span>  
  
1.  <span data-ttu-id="6322b-161">Visual Studio で、**[TestApp]** プロジェクトの下にある **Default.aspx** ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6322b-161">In Visual Studio, open the **Default.aspx** file under the **TestApp** project.</span></span>  
  
2.  <span data-ttu-id="6322b-162">**Default.aspx** ファイルの既存のマークアップを次のマークアップに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6322b-162">Replace the existing markup in the **Default.aspx** file with the following markup:</span></span>  
  
    ```  
    <%@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head runat="server">  
        <title>Logged In Status</title>  
    </head>  
    <body>  
        <asp:label ID="myLabel" runat="server" />  
    </body>  
    </html>  
    ```  
  
3.  <span data-ttu-id="6322b-163">**Default.aspx** を保存してから、**Default.aspx.cs** という名前の分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="6322b-163">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6322b-164">**Default.aspx.cs** は、ソリューション エクスプローラーで **Default.aspx** の下に隠れていることがあります。</span><span class="sxs-lookup"><span data-stu-id="6322b-164">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="6322b-165">**Default.aspx.cs** が表示されない場合は、**Default.aspx** の横の三角形をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="6322b-165">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
4.  <span data-ttu-id="6322b-166">**Default.aspx.cs** の既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="6322b-166">Replace the existing code in **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Web.UI;  
    using System.Security.Claims;  
  
    namespace TestApp  
    {  
        protected void Page_Load(object sender, EventArgs e)  
        {  
            ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
            if (claimsPrincipal != null)  
            {  
                myLabel.Text = "You are signed in.";  
            }  
            else  
            {  
                myLabel.Text = "You are not signed in.";  
            }  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="6322b-167">**Default.aspx.cs** を保存し、アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="6322b-167">Save **Default.aspx.cs**, and build the application.</span></span>  
  
## <a name="step-5--test-the-integration-between-wif-and-your-aspnet-application"></a><span data-ttu-id="6322b-168">手順 5 – WIF と ASP.NET アプリケーション間の統合のテスト</span><span class="sxs-lookup"><span data-stu-id="6322b-168">Step 5 – Test the Integration Between WIF and Your ASP.NET Application</span></span>  
 <span data-ttu-id="6322b-169">この手順では、WIF と ASP.NET アプリケーション間の統合をテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6322b-169">This step describes how you can test the integration between WIF and your ASP.NET application.</span></span>  
  
#### <a name="to-test-the-integration-between-wif-and-aspnet"></a><span data-ttu-id="6322b-170">WIF と ASP.NET 間の統合をテストするには</span><span class="sxs-lookup"><span data-stu-id="6322b-170">To test the integration between WIF and ASP.NET</span></span>  
  
1.  <span data-ttu-id="6322b-171">Visual Studio で **F5** キーを押して、アプリケーションのデバッグを開始します。</span><span class="sxs-lookup"><span data-stu-id="6322b-171">In Visual Studio, press **F5** to start debugging your application.</span></span> <span data-ttu-id="6322b-172">エラーがなければ、新しいブラウザー ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="6322b-172">If no errors are found, a new browser window will open.</span></span>  
  
2.  <span data-ttu-id="6322b-173">ブラウザーが STS に自動的に要求をリダイレクトし、Default.aspx ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="6322b-173">You may notice that the browser silently redirects your request to the STS, and then opens the Default.aspx page.</span></span> <span data-ttu-id="6322b-174">WIF が正しく構成されている場合は、サイトに **"You are signed in"** というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6322b-174">If WIF is properly configured, you should see the site display the following text: **"You are signed in"**.</span></span>
