---
title: "方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 7065455e3459ad37a8e296107ca8c6991334b328
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a><span data-ttu-id="11702-102">方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="11702-102">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="11702-103">対象</span><span class="sxs-lookup"><span data-stu-id="11702-103">Applies To</span></span>  
  
-   <span data-ttu-id="11702-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="11702-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="11702-105">ASP.NET® MVC</span><span class="sxs-lookup"><span data-stu-id="11702-105">ASP.NET® MVC</span></span>  
  
## <a name="summary"></a><span data-ttu-id="11702-106">概要</span><span class="sxs-lookup"><span data-stu-id="11702-106">Summary</span></span>  
 <span data-ttu-id="11702-107">この操作方法では、簡単なクレーム対応 ASP.NET MVC Web アプリケーションを作成するための詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="11702-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET MVC web application.</span></span> <span data-ttu-id="11702-108">また、クレーム ベースの認証を正常に実装するために簡単なクレーム対応 ASP.NET MVC Web アプリケーションをテストする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="11702-108">It also provides instructions how to test the simple claims-aware ASP.NET MVC web application for successful implementation of claims-based authentication.</span></span> <span data-ttu-id="11702-109">この操作方法には、セキュリティ トークン サービス (STS) の詳細な作成手順は含まれていません。既に STS が構成済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="11702-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="11702-110">目次</span><span class="sxs-lookup"><span data-stu-id="11702-110">Contents</span></span>  
  
-   <span data-ttu-id="11702-111">目的</span><span class="sxs-lookup"><span data-stu-id="11702-111">Objectives</span></span>  
  
-   <span data-ttu-id="11702-112">手順の要約</span><span class="sxs-lookup"><span data-stu-id="11702-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="11702-113">手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="11702-113">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="11702-114">手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="11702-114">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="11702-115">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="11702-115">Step 3 – Test Your Solution</span></span>  
  
-   <span data-ttu-id="11702-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="11702-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="11702-117">目的</span><span class="sxs-lookup"><span data-stu-id="11702-117">Objectives</span></span>  
  
-   <span data-ttu-id="11702-118">クレーム ベースの認証用の ASP.NET MVC Web アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="11702-118">Configure ASP.NET MVC web application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="11702-119">クレーム対応 ASP.NET MVC Web アプリケーションが正常であることをテストする</span><span class="sxs-lookup"><span data-stu-id="11702-119">Test successful claims-aware ASP.NET MVC web application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="11702-120">手順の要約</span><span class="sxs-lookup"><span data-stu-id="11702-120">Summary of Steps</span></span>  
  
-   <span data-ttu-id="11702-121">手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="11702-121">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
  
-   <span data-ttu-id="11702-122">手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="11702-122">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="11702-123">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="11702-123">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a><span data-ttu-id="11702-124">手順 1 – 簡単な ASP.NET MVC アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="11702-124">Step 1 – Create Simple ASP.NET MVC Application</span></span>  
 <span data-ttu-id="11702-125">この手順では、新しい ASP.NET MVC アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="11702-125">In this step, you will create a new ASP.NET MVC application.</span></span>  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a><span data-ttu-id="11702-126">簡単な ASP.NET MVC アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="11702-126">To create simple ASP.NET MVC application</span></span>  
  
1.  <span data-ttu-id="11702-127">Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="11702-127">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="11702-128">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET MVC 3 Web アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11702-128">In the **New Project** window, click **ASP.NET MVC 3 Web Application**.</span></span>  
  
3.  <span data-ttu-id="11702-129">**[名前]** で、「`TestApp`」と入力して **[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="11702-129">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
4.  <span data-ttu-id="11702-130">**[新しい ASP.NET MVC 3 プロジェクト]** ダイアログで、使用可能なテンプレートから **[インターネット アプリケーション]** を選択し、**[ビュー エンジン]** が **[Razor]** に設定されていることを確認して **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11702-130">In the **New ASP.NET MVC 3 Project** dialog, select **Internet Application** from the available templates, ensure **View Engine** is set to **Razor**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="11702-131">新しいプロジェクトが開いたら、**ソリューション エクスプローラー**で **[TestApp]** プロジェクトを右クリックして **[プロパティ]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="11702-131">When the new project opens, right-click the **TestApp** project in **Solution Explorer** and select the **Properties** option.</span></span>  
  
6.  <span data-ttu-id="11702-132">プロジェクトのプロパティ ページで、左側の **[Web]** タブをクリックし、**[ローカル IIS Web サーバーを使用する]** オプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11702-132">On the project’s properties page, click on the **Web** tab on the left and ensure that the **Use Local IIS Web Server** option is selected.</span></span>  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="11702-133">手順 2 – クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="11702-133">Step 2 – Configure ASP.NET MVC Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="11702-134">この手順では、構成エントリを ASP.NET MVC Web アプリケーションの *Web.config* 構成ファイルに追加して、クレーム対応にします。</span><span class="sxs-lookup"><span data-stu-id="11702-134">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET MVC web application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="11702-135">クレーム ベースの認証用の ASP.NET MVC アプリケーションを構成するには</span><span class="sxs-lookup"><span data-stu-id="11702-135">To configure ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="11702-136">次の構成セクションの定義を *Web.config* 構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-136">Add the following configuration section definitions to the *Web.config* configuration file.</span></span> <span data-ttu-id="11702-137">これで、Windows Identity Foundation に必要な構成セクションが定義されます。</span><span class="sxs-lookup"><span data-stu-id="11702-137">These define configuration sections required by Windows Identity Foundation.</span></span> <span data-ttu-id="11702-138">**\<configuration>** 開始要素のすぐ後に定義を追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-138">Add the definitions immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="11702-139">次のように、アプリケーションのフェデレーション メタデータへのアクセスを有効にする **\<location>** 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-139">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="11702-140">**\<system.web>** 要素内で以下の構成エントリを追加して、ユーザーを拒否し、ネイティブ認証を無効にし、認証を管理するために WIF を有効にします。</span><span class="sxs-lookup"><span data-stu-id="11702-140">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="11702-141">以下の Windows Identity Foundation 関連の構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が、**\<audienceUris>** エントリ、**\<wsFederation>** 要素の **realm** 属性、および **\<wsFederation>** 要素の **reply** 属性の値と一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="11702-141">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="11702-142">また、**issuer** の値がセキュリティ トークン サービス (STS) URL に適したものであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11702-142">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5.  <span data-ttu-id="11702-143"><xref:System.IdentityModel> アセンブリに参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-143">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
6.  <span data-ttu-id="11702-144">ソリューションをコンパイルして、エラーがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="11702-144">Compile the solution to make sure there are errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="11702-145">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="11702-145">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="11702-146">この手順では、クレーム ベースの認証用に構成された ASP.NET MVC Web アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="11702-146">In this step you will test your ASP.NET MVC web application configured for claims-based authentication.</span></span> <span data-ttu-id="11702-147">基本テストを実行するには、セキュリティ トークン サービス (STS) で発行されたトークンでクレームを表示する簡単なコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-147">To perform basic test you will add simple code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a><span data-ttu-id="11702-148">クレーム ベースの認証用の ASP.NET MVC アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="11702-148">To test your ASP.NET MVC application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="11702-149">**ソリューション エクスプローラー**で、**Controllers** フォルダーを展開し、エディターで *HomeController.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="11702-149">In the **Solution Explorer**, expand the **Controllers** folder and open *HomeController.cs* file in the editor.</span></span> <span data-ttu-id="11702-150">**Index** メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-150">Add the following code to the **Index** method:</span></span>  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2.  <span data-ttu-id="11702-151">**ソリューション エクスプローラー**で、**Views** フォルダーを展開してから **Home** フォルダーを展開し、エディターで *Index.cshtml* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="11702-151">In the **Solution Explorer** expand **Views** and then **Home** folders and open *Index.cshtml* file in the editor.</span></span> <span data-ttu-id="11702-152">その内容を削除し、次のマークアップを追加します。</span><span class="sxs-lookup"><span data-stu-id="11702-152">Delete its contents and add the following markup:</span></span>  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3.  <span data-ttu-id="11702-153">**F5** キーを押して、ソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="11702-153">Run the solution by pressing the **F5** key.</span></span>  
  
4.  <span data-ttu-id="11702-154">セキュリティ トークン サービスで発行されたトークンでクレームを表示するページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="11702-154">You should be presented with the page that displays the claims in the token that was issued to you by Security Token Service.</span></span>  
  
## <a name="related-items"></a><span data-ttu-id="11702-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="11702-155">Related Items</span></span>  
  
-   [<span data-ttu-id="11702-156">方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="11702-156">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
