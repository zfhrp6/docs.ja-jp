---
title: "方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d5b81e20ed1b39c7750329718729905484eb7fa1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-claims-aware-aspnet-web-forms-application-using-wif"></a><span data-ttu-id="4ee17-102">方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="4ee17-102">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>
## <a name="applies-to"></a><span data-ttu-id="4ee17-103">対象</span><span class="sxs-lookup"><span data-stu-id="4ee17-103">Applies To</span></span>  
  
-   <span data-ttu-id="4ee17-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4ee17-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="4ee17-105">ASP.NET® Web フォーム</span><span class="sxs-lookup"><span data-stu-id="4ee17-105">ASP.NET® Web Forms</span></span>  
  
## <a name="summary"></a><span data-ttu-id="4ee17-106">概要</span><span class="sxs-lookup"><span data-stu-id="4ee17-106">Summary</span></span>  
 <span data-ttu-id="4ee17-107">この操作方法では、簡単なクレーム対応 ASP.NET Web フォーム アプリケーションを作成するための詳細な手順を示します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-107">This How-To provides detailed step-by-step procedures for creating simple claims-aware ASP.NET Web Forms application.</span></span> <span data-ttu-id="4ee17-108">また、フェデレーション認証を正常に実装するために簡単なクレーム対応 ASP.NET Web フォーム アプリケーションをテストする方法も示します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-108">It also provides instructions for how to test the simple claims-aware ASP.NET Web Forms application for successful implementation of federated authentication.</span></span> <span data-ttu-id="4ee17-109">この操作方法には、セキュリティ トークン サービス (STS) の詳細な作成手順は含まれていません。既に STS が構成済みであると想定します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and assumes you have already configured an STS.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="4ee17-110">目次</span><span class="sxs-lookup"><span data-stu-id="4ee17-110">Contents</span></span>  
  
-   <span data-ttu-id="4ee17-111">目的</span><span class="sxs-lookup"><span data-stu-id="4ee17-111">Objectives</span></span>  
  
-   <span data-ttu-id="4ee17-112">手順の要約</span><span class="sxs-lookup"><span data-stu-id="4ee17-112">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4ee17-113">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-113">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="4ee17-114">手順 2 – クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-114">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
  
-   <span data-ttu-id="4ee17-115">手順 3 – ソリューションのテスト</span><span class="sxs-lookup"><span data-stu-id="4ee17-115">Step 3 – Test Your Solution</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="4ee17-116">目的</span><span class="sxs-lookup"><span data-stu-id="4ee17-116">Objectives</span></span>  
  
-   <span data-ttu-id="4ee17-117">クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-117">Configure ASP.NET Web Forms application for claims-based authentication</span></span>  
  
-   <span data-ttu-id="4ee17-118">クレーム対応 ASP.NET Web フォーム アプリケーションが正常であることをテストする</span><span class="sxs-lookup"><span data-stu-id="4ee17-118">Test successful claims-aware ASP.NET Web Forms application</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="4ee17-119">手順の要約</span><span class="sxs-lookup"><span data-stu-id="4ee17-119">Summary of Steps</span></span>  
  
-   <span data-ttu-id="4ee17-120">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-120">Step 1 – Create Simple ASP.NET Web Forms Application</span></span>  
  
-   <span data-ttu-id="4ee17-121">手順 2 – フェデレーション認証用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-121">Step 2 – Configure ASP.NET Web Forms Application for Federated Authentication</span></span>  
  
-   <span data-ttu-id="4ee17-122">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="4ee17-122">Step 3 – Test Your Solution</span></span>  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application"></a><span data-ttu-id="4ee17-123">手順 1 – 簡単な ASP.NET Web フォーム アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-123">Step 1 – Create a Simple ASP.NET Web Forms Application</span></span>  
 <span data-ttu-id="4ee17-124">この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-124">In this step, you will create a new ASP.NET Web Forms application.</span></span>  
  
#### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="4ee17-125">簡単な ASP.NET アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="4ee17-125">To create a simple ASP.NET application</span></span>  
  
1.  <span data-ttu-id="4ee17-126">Visual Studio を起動し、**[ファイル]**、**[新規作成]**、**[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-126">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>  
  
2.  <span data-ttu-id="4ee17-127">**[新しいプロジェクト]** ウィンドウで、**[ASP.NET Web フォーム アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-127">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>  
  
3.  <span data-ttu-id="4ee17-128">**[名前]** で、「`TestApp`」と入力して **[OK]** を押します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-128">In **Name**, enter `TestApp` and press **OK**.</span></span>  
  
## <a name="step-2--configure-aspnet-web-forms-application-for-claims-based-authentication"></a><span data-ttu-id="4ee17-129">手順 2 – クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションを構成する</span><span class="sxs-lookup"><span data-stu-id="4ee17-129">Step 2 – Configure ASP.NET Web Forms Application for Claims-Based Authentication</span></span>  
 <span data-ttu-id="4ee17-130">この手順では、構成エントリを ASP.NET Web フォーム アプリケーションの *Web.config* 構成ファイルに追加して、クレーム対応にします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-130">In this step you will add configuration entries to the *Web.config* configuration file of your ASP.NET Web Forms application to make it claims-aware.</span></span>  
  
#### <a name="to-configure-aspnet-application-for-claims-based-authentication"></a><span data-ttu-id="4ee17-131">クレーム ベースの認証用の ASP.NET アプリケーションを構成するには</span><span class="sxs-lookup"><span data-stu-id="4ee17-131">To configure ASP.NET application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="4ee17-132">**\<configuration>** 開始要素のすぐ後の *Web.config* 構成ファイルに、次の構成セクション エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-132">Add the following configuration section entries to the *Web.config* configuration file immediately after the **\<configuration>** opening element:</span></span>  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  <span data-ttu-id="4ee17-133">次のように、アプリケーションのフェデレーション メタデータへのアクセスを有効にする **\<location>** 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-133">Add a **\<location>** element that enables access to the application’s federation metadata:</span></span>  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  <span data-ttu-id="4ee17-134">**\<system.web>** 要素内で以下の構成エントリを追加して、ユーザーを拒否し、ネイティブ認証を無効にし、認証を管理するために WIF を有効にします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-134">Add the following configuration entries within the **\<system.web>** elements to deny users, disable native authentication, and enable WIF to manage authentication.</span></span>  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  <span data-ttu-id="4ee17-135">フェデレーション認証用のモジュールを定義する **\<system.webServer>** 要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-135">Add a **\<system.webServer>** element that defines the modules for federated authentication.</span></span> <span data-ttu-id="4ee17-136">*PublicKeyToken* 属性は、前の手順で追加した **\<configSections>** エントリの *PublicKeyToken* 属性と同じである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4ee17-136">Note that the *PublicKeyToken* attribute must be the same as the *PublicKeyToken* attribute for the **\<configSections>** entries added earlier:</span></span>  
  
    ```xml  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  <span data-ttu-id="4ee17-137">以下の Windows Identity Foundation 関連の構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が、**\<audienceUris>** エントリ、**\<wsFederation>** 要素の **realm** 属性、および **\<wsFederation>** 要素の **reply** 属性の値と一致することを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-137">Add the following Windows Identity Foundation related configuration entries and ensure that your ASP.NET application’s URL and port number match the values in the **\<audienceUris>** entry, **realm** attribute of the **\<wsFederation>** element, and the **reply** attribute of the **\<wsFederation>** element.</span></span> <span data-ttu-id="4ee17-138">また、**issuer** の値がセキュリティ トークン サービス (STS) URL に適したものであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-138">Also ensure that the **issuer** value fits your Security Token Service (STS) URL.</span></span>  
  
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
  
6.  <span data-ttu-id="4ee17-139"><xref:System.IdentityModel> アセンブリに参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-139">Add reference to the <xref:System.IdentityModel> assembly.</span></span>  
  
7.  <span data-ttu-id="4ee17-140">ソリューションをコンパイルして、エラーがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-140">Compile the solution to make sure there are no errors.</span></span>  
  
## <a name="step-3--test-your-solution"></a><span data-ttu-id="4ee17-141">手順 3 – ソリューションをテストする</span><span class="sxs-lookup"><span data-stu-id="4ee17-141">Step 3 – Test Your Solution</span></span>  
 <span data-ttu-id="4ee17-142">この手順では、クレーム ベースの認証用に構成された ASP.NET Web フォーム アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-142">In this step you will test your ASP.NET Web Forms application configured for claims-based authentication.</span></span> <span data-ttu-id="4ee17-143">基本テストを実行するには、セキュリティ トークン サービス (STS) で発行されたトークンでクレームを表示するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-143">To perform a basic test, you will add code that displays claims in the token issued by the Security Token Service (STS).</span></span>  
  
#### <a name="to-test-your-aspnet-web-form-application-for-claims-based-authentication"></a><span data-ttu-id="4ee17-144">クレーム ベースの認証用の ASP.NET Web フォーム アプリケーションをテストするには</span><span class="sxs-lookup"><span data-stu-id="4ee17-144">To test your ASP.NET Web Form application for claims-based authentication</span></span>  
  
1.  <span data-ttu-id="4ee17-145">**TestApp** プロジェクトの下にある **Default.aspx** ファイルを開き、既存のマークアップを次のマークアップに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4ee17-145">Open the **Default.aspx** file under the **TestApp** project and replace its existing markup with the following markup:</span></span>  
  
    ```  
    %@ Page Language="C#" AutoEventWireup="true" CodeFile="Default.aspx.cs" Inherits="_Default" %>  
  
    <!DOCTYPE html>  
  
    <html>  
    <head id="Head1" runat="server">  
        <title></title>  
    </head>  
    <body>  
        <h1><asp:label ID="signedIn" runat="server" /></h1>  
        <asp:label ID="claimType" runat="server" />  
        <asp:label ID="claimValue" runat="server" />  
        <asp:label ID="claimValueType" runat="server" />  
        <asp:label ID="claimSubjectName" runat="server" />  
        <asp:label ID="claimIssuer" runat="server" />  
    </body>  
    </html>  
    ```  
  
2.  <span data-ttu-id="4ee17-146">**Default.aspx** を保存し、**Default.aspx.cs** という名前の分離コード ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="4ee17-146">Save **Default.aspx**, and then open its code behind file named **Default.aspx.cs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ee17-147">**Default.aspx.cs** は、ソリューション エクスプローラーで **Default.aspx** の下に隠れていることがあります。</span><span class="sxs-lookup"><span data-stu-id="4ee17-147">**Default.aspx.cs** may be hidden beneath **Default.aspx** in Solution Explorer.</span></span> <span data-ttu-id="4ee17-148">**Default.aspx.cs** が表示されない場合は、**Default.aspx** の横の三角形をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-148">If **Default.aspx.cs** is not visible, expand **Default.aspx** by clicking on the triangle next to it.</span></span>  
  
3.  <span data-ttu-id="4ee17-149">**Default.aspx.cs** の **Page_Load** メソッド内の既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4ee17-149">Replace the existing code in the **Page_Load** method of **Default.aspx.cs** with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.IdentityModel;  
    using System.Security.Claims;  
    using System.Threading;  
    using System.Web.UI;  
  
    namespace TestApp  
    {  
        public partial class _Default : System.Web.UI.Page  
        {  
            protected void Page_Load(object sender, EventArgs e)  
            {  
                ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
                if (claimsPrincipal != null)  
                {  
                    signedIn.Text = "You are signed in.";  
  
                    foreach (Claim claim in claimsPrincipal.Claims)  
                    {  
                        claimType.Text = claim.Type;  
                        claimValue.Text = claim.Value;  
                        claimValueType.Text = claim.ValueType;  
                        claimSubjectName.Text = claim.Subject.Name;  
                        claimIssuer.Text = claim.Issuer;  
                    }  
                }  
                else  
                {  
                    signedIn.Text = "You are not signed in.";  
                }  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="4ee17-150">**Default.aspx.cs** を保存して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4ee17-150">Save **Default.aspx.cs**, and build the solution.</span></span>  
  
5.  <span data-ttu-id="4ee17-151">**F5** キーを押して、ソリューションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ee17-151">Run the solution by pressing the **F5** key.</span></span>  
  
6.  <span data-ttu-id="4ee17-152">セキュリティ トークン サービスで発行されたトークンでクレームを表示するページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ee17-152">You should be presented with the page that displays the claims in the token that was issued to you by the Security Token Service.</span></span>
