---
title: "方法: 入力方向の要求の変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2831d514-d9d8-4200-9192-954bb6da1126
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# 方法: 入力方向の要求の変換
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   Web フォーム ASP.NET®  
  
## 概要  
 ここでは、単純な要求対応の ASP.NET Web フォーム アプリケーションを作成し、着信要求を変換するための詳細な手順を示します。  また、メソッドにアプリケーションの実行時に命令を追加する必要があることを確認するアプリケーションをテストできます。  
  
## 内容  
  
-   対象  
  
-   概要  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- カスタム ClaimsAuthenticationManager を使用して要求の変換を実行します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 対象  
  
-   クレームベース認証用の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   要求管理者ロールに追加することにより、着信要求を変換します。  
  
-   正常に動作しているかどうかを ASP.NET Web フォーム アプリケーションをテストします。  
  
## 概要  
 WIF には、証明書利用者の \(RP\) アプリケーションにという名前の前に <xref:System.Security.Claims.ClaimsAuthenticationManager> という要求を変更することを可能にするクラスを公開します。  <xref:System.Security.Claims.ClaimsAuthenticationManager> は認証と基になるアプリケーション コードの関心の分離に便利です。  次のの例は、RP によって必要とされる <xref:System.Security.Claims.ClaimsPrincipal> 受信した要求にロールを追加する方法を示します。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- カスタム ClaimsAuthenticationManager を使用して要求の変換を実行します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### 単純な ASP.NET アプリケーションを作成するには  
  
1.  管理者としてのあるモードで開始の Visual Studio。  
  
2.  Visual Studio で、をクリック **ファイル**の **新規作成**クリックし、を **プロジェクト**をクリックします。  
  
3.  **新しいプロジェクト** のペインで、**ASP.NET Web フォーム アプリケーション**をクリックします。  
  
4.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
5.  **TestApp** のプロジェクトを **ソリューション エクスプローラー**の下にあるを右クリックして、を **Identity and Access**を選択します。  
  
6.  **Identity and Access** のウィンドウが表示されます。  **プロバイダ**の\[ **ローカルの開発用 STS でアプリケーションをテストします。**は、を **適用**をクリックします。  
  
7.  *Default.aspx ファイル* で、既存のマークアップを次に置き換え、ファイルを保存します:  
  
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
  
8.  *Default.aspx.cs*  という名前の分離コード ファイルを開きます。  既存のコードを次に置き換え、ファイルを保存します:  
  
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
  
## 手順 2 \- カスタム ClaimsAuthenticationManager を使用して要求の変換を実行します。  
 この手順で入力されるプリンシパルに管理者ロールを追加するに <xref:System.Security.Claims.ClaimsAuthenticationManager> クラスの既定の機能をオーバーライドします。  
  
#### 要求の変換をカスタム ClaimsAuthenticationManager を使用して実行するには  
  
1.  Visual Studio で、ソリューションを右クリックし、**追加**をクリックし、を **新しいプロジェクト**をクリックします。  
  
2.  **新しいプロジェクトの追加** のペインで、**Visual C\#** テンプレートから選択 **クラス ライブラリ** には、`ClaimsTransformation`を入力し、を **OK**を押します。  新しいプロジェクトがソリューション フォルダーに作成されます。  
  
3.  **ClaimsTransformation** のプロジェクトの下の **参照** を右クリックし、を **参照の追加**をクリックします。  
  
4.  **参照マネージャー** のペインで、を選択します **System.IdentityModel**は、を **OK**をクリックします。  
  
5.  開いている **Class1.cs**、またはをクリック **クラス\]**するには、右クリックします **ClaimsTransformation**を、**追加**をクリックすると、  
  
6.  コード ファイルには、ディレクティブを使用して次のように追加します:  
  
    ```csharp  
    using System.Security.Claims;  
    using System.Security.Principal;  
    ```  
  
7.  コード ファイルに次のクラスとメソッドを追加します。  
  
    > [!WARNING]
    >  次のコードは、デモンストレーションのためだけに作成されています; 製品コードで、目的のアクセス許可を確認してください。  
  
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
  
8.  ファイルを保存し、**ClaimsTransformation** プロジェクトをビルドします。  
  
9. 参照の **TestApp**、ASP.NET のプロジェクトでは、を右クリックし、を **参照の追加**をクリックします。  
  
10. **参照マネージャー** のウィンドウでは、左のメニューから選択 **ソリューション**、データが設定されたオプションから選択 **ClaimsTransformation** は、を **OK**をクリックします。  
  
11. ルートの **Web.config** ファイルで、**\<system.identityModel\>** のエントリに移動します。  **\<identityConfiguration\>** の要素内に次の行を追加し、ファイルを保存します:  
  
    ```  
    <claimsAuthenticationManager type="ClaimsTransformation.ClaimsTransformationModule, ClaimsTransformation" />  
    ```  
  
## 手順 3 \- ソリューションをテストします。  
 この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用する場合、要求があることを確認します。  
  
#### 要求の ASP.NET Web フォーム アプリケーションのフォーム認証を使用してテストするには  
  
1.  F5 キーを押してアプリケーションをビルドし、実行します。  *Default.aspx*という必要があります。  
  
2.  *Default.aspx ページ* で、**発行者**、**OriginalIssuer**、**種類**、**値**、このアカウントに関する **ValueType** の要求情報含む **アプリケーションで要求** の、見出しの下のテーブルが表示されます。  最後の行には、次の方法で名前を付ける必要があります:  
  
    ||||||  
    |-|-|-|-|-|  
    |地方自治体|地方自治体|http:\/\/schemas.microsoft.com\/ws\/2008\/06\/identity\/claims\/role|Admin|http:\/\/www.w3.org\/2001\/XMLSchema\#string|