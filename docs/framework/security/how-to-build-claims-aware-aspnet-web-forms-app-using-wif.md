---
title: "方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: efb264dd-f47b-49a9-85ee-9f45d4425765
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# 方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   Web フォーム ASP.NET®  
  
## 概要  
 ここでは、単純な要求対応の ASP.NET Web フォーム アプリケーションを作成する詳細な手順を示します。  また、方法についてフェデレーションな認証の正常な実装の単純な要求対応の ASP.NET Web フォーム アプリケーションをテストできます。  ここでは、セキュリティ トークン Services \(STS\) を作成するための詳細な手順がなく、既に STS を構成していることを前提としています。  
  
## 内容  
  
-   対象  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- クレームベース認証用の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 対象  
  
-   クレームベース認証用の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   正常な要求対応の ASP.NET Web フォーム アプリケーションをテストします。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- フェデレーションな認証用の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### 単純な ASP.NET アプリケーションを作成するには  
  
1.  次に、Visual Studio を起動し、**ファイル**、**新規作成**と **プロジェクト**をクリックします。  
  
2.  **新しいプロジェクト** のペインで、**ASP.NET Web フォーム アプリケーション**をクリックします。  
  
3.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
## 手順 2 \- クレームベース認証用の ASP.NET Web フォーム アプリケーションを構成します。  
 この手順で必要な認識するように ASP.NET Web フォーム アプリケーションの *Web.config 構成ファイル* に構成エントリを追加します。  
  
#### クレームベース認証を使用するように ASP.NET アプリケーションを構成するには  
  
1.  **\<configuration\>** の開始要素の直後の *Web.config 構成ファイル* に次の構成セクションのエントリを追加します:  
  
    ```xml  
    <configSections>  
      <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
      <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2.  アプリケーションのフェデレーションのメタデータへのアクセスを可能にする **\<location\>** の要素を追加します:  
  
    ```xml  
    <location path="FederationMetadata">  
      <system.web>  
        <authorization>  
          <allow users="*" />  
        </authorization>  
      </system.web>  
    </location>  
    ```  
  
3.  ユーザーを拒否するに **\<system.web\>** の要素内に次の構成エントリを追加してネイティブの認証を無効にし、認証を管理できます。は WIF ができます。  
  
    ```xml  
    <authorization>  
      <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4.  フェデレーションな認証のモジュールを定義する **\<system.webServer\>** の要素を追加します。  *PublicKeyToken の* 属性が **\<configSections\>** のエントリの *PublicKeyToken の* 属性が、前に追加した同じであることに注意してください:  
  
    ```  
    <system.webServer>  
      <modules>  
        <add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
        <add name="SessionAuthenticationModule" type="System.IdentityModel.Services.SessionAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" preCondition="managedHandler" />  
      </modules>  
    </system.webServer>  
    ```  
  
5.  次の Windows ID の基本関連構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が **\<wsFederation\>** の要素の **\<audienceUris\>** エントリ、**領域** の属性、および **\<wsFederation\>** の要素の **応答** の属性の値が一致することを確認します。  また **発行者** の値がセキュリティ トークン サービスの \(STS\) の URL を満たしていることを確認します。  
  
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
  
6.  [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) のアセンブリへの参照を追加します。  
  
7.  エラーを得るためにソリューションをコンパイルします。  
  
## 手順 3 \- ソリューションをテストします。  
 この手順で構成されたクレームベース認証の ASP.NET Web フォーム アプリケーションをテストします。  基本的なテストを実行するには、コードをそのセキュリティ トークン Services \(STS\) によって発行されたトークンの表示の要求追加します。  
  
#### ASP.NET Web をテストするにはクレームベース認証を使用するようにアプリケーションを設定します  
  
1.  **Default.aspx** ファイルを **TestApp** のプロジェクトで開き、既存のマークアップに置き換えます。:  
  
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
  
2.  **Default.aspx**を保存し、ファイルによって指定 **Default.aspx.cs**の後ろにコードを開きます。  
  
    > [!NOTE]
    >  **Default.aspx.cs** は、ソリューション エクスプローラーの **Default.aspx** の下に非表示になる場合があります。  **Default.aspx.cs** が表示されない場合は、その横の三角形をクリックして **Default.aspx** を展開します。  
  
3.  次のコードで **Default.aspx.cs** の **Page\_Load** のメソッドの既存のコードに置き換えます。:  
  
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
  
4.  **Default.aspx.cs**を保存し、ソリューションをビルドします。  
  
5.  **F5** キーを押してソリューションを実行します。  
  
6.  セキュリティ トークン サービスにより、に発行されたトークンの要求を表示するページという名前を付ける必要があります。