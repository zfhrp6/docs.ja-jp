---
title: "方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98a3e029-1a9b-4e0c-b5d0-29d3f23f5b15
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# 方法: フォームベースの認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   Web フォーム ASP.NET®  
  
## 概要  
 ここでは、フォーム認証を使用する単純な要求対応の ASP.NET Web フォーム アプリケーションを作成する詳細な手順を示します。  また、方法にユーザーがフォーム認証を使用するときに命令が必要があることを確認するアプリケーションをテストできます。  
  
## 内容  
  
-   対象  
  
-   概要  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- フォーム認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 対象  
  
-   フォーム認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   正常に動作しているかどうかを ASP.NET Web フォーム アプリケーションをテストします。  
  
## 概要  
 .NET 4.5 では、要求と WIF ベースの承認はフレームワークの重要な部分として含まれていました。  以前は、ASP.NET ユーザーからの要求が必要な場合は、WIF をインストールするように要求し `Thread.CurrentPrincipal` または `HttpContext.Current.User`などの主なオブジェクトにインターフェイスをキャストします。  これで、要求はこれらの主なオブジェクトによって自動的に処理されます。  
  
 フォーム認証は、.NET 4.5 の WIF に含まれないように、フォーム認証されているすべてのユーザーに自動的に関連付けられた要求があるためパフォーマンスが向上しました。  示します。これとしてフォーム認証を使用する ASP.NET アプリケーションでこれらの要求をすぐに、どのように使用できます。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- フォーム認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### 単純な ASP.NET アプリケーションを作成するには  
  
1.  次に、Visual Studio を起動し、**ファイル**、**新規作成**と **プロジェクト**をクリックします。  
  
2.  **新しいプロジェクト** のペインで、**ASP.NET Web フォーム アプリケーション**をクリックします。  
  
3.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
## 手順 2 \- フォーム認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
 この手順では、*Web.config* 構成ファイルに構成エントリを追加し、アカウントの要求情報を表示するに *Default.aspx* を編集します。  
  
#### 要求の ASP.NET アプリケーションをフォーム認証を使用して構成するには  
  
1.  *Default.aspx ファイル* で、既存のマークアップに置き換えます。:  
  
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
  
     この手順は、フォーム認証から取得された要求が設定された *Default.aspx ページ* に GridView コントロールを追加します。  
  
2.  Save the *Default.aspx* ファイルを保存して、*Default.aspx.cs*という名前の分離コード ファイルを開きます。  次に、既存のコードに置き換えます。:  
  
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
  
     上のコードはフォーム認証によって識別されたユーザーを含む認証されたユーザーに関する要求を表示します。  
  
## 手順 3 \- ソリューションをテストします。  
 この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーがフォーム認証を使用する場合、要求があることを確認します。  
  
#### 要求の ASP.NET Web フォーム アプリケーションのフォーム認証を使用してテストするには  
  
1.  F5 キーを押してアプリケーションをビルドし、実行します。  **登録** があり、**ログイン** がページの右上で *Default.aspx*という名前のリンクする必要があります。  **\[登録\]** をクリックします。  
  
2.  **登録** のページで、ユーザー アカウントを作成し、**登録**をクリックします。  このアカウントは、フォーム認証を使用して作成され、自動的に署名されています。  
  
3.  ホーム ページにリダイレクトを変えた後、**発行者**、**OriginalIssuer**、**種類**、**値**、このアカウントに関する **ValueType** の要求情報含む **アプリケーションで要求** の、見出しの下のテーブルが表示されます。