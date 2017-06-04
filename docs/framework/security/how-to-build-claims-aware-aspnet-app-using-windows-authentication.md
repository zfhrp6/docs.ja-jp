---
title: "方法: Windows 認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 11c53d9d-d34a-44b4-8b5e-22e3eaeaee93
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# 方法: Windows 認証を使用するクレーム対応 ASP.NET アプリケーションをビルドする
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   Web フォーム ASP.NET®  
  
## 概要  
 ここでは、Windows 認証を使用する単純な要求対応の ASP.NET Web フォーム アプリケーションを作成する詳細な手順を示します。  また、方法にユーザーが Windows 認証を使用して署名を行う場合は、命令が必要であることを確認するアプリケーションをテストできます。  
  
## 内容  
  
-   対象  
  
-   概要  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- Windows 認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 対象  
  
-   Windows 認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   正常に動作しているかどうかを ASP.NET Web フォーム アプリケーションをテストします。  
  
## 概要  
 .NET 4.5 では、要求と WIF ベースの承認はフレームワークの重要な部分として含まれていました。  以前は、ASP.NET ユーザーからの要求が必要な場合は、WIF をインストールするように要求し `Thread.CurrentPrincipal` または `HttpContext.Current.User`などの主なオブジェクトにインターフェイスをキャストします。  これで、要求はこれらの主なオブジェクトによって自動的に処理されます。  
  
 Windows 認証は、.NET 4.5 の WIF に含まれないよう Windows の資格情報に、認証されているすべてのユーザーに自動的に関連付けられた要求があるためパフォーマンスが向上しました。  示します。これとして Windows 認証を使用する ASP.NET アプリケーションでこれらの要求をすぐに、どのように使用できます。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
  
-   手順 2 \- Windows 認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET Web フォーム アプリケーションを作成します。  
 この手順では、新しい ASP.NET Web フォーム アプリケーションを作成します。  
  
#### 単純な ASP.NET アプリケーションを作成するには  
  
1.  次に、Visual Studio を起動し、**ファイル**、**新規作成**と **プロジェクト**をクリックします。  
  
2.  **新しいプロジェクト** のペインで、**ASP.NET Web フォーム アプリケーション**をクリックします。  
  
3.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
4.  **TestApp** のプロジェクトを作成したら、その **ソリューション エクスプローラー**のをクリックします。  プロジェクトのプロパティは **ソリューション エクスプローラー**の下に **プロパティ** のペインに表示されます。  **有効**に **Windows 認証** のプロパティを設定します。  
  
    > [!WARNING]
    >  Windows 認証は、新しい ASP.NET アプリケーションで既定で無効になっているため、手動で有効にする必要があります。  
  
## 手順 2 \- Windows 認証を使用する要求の ASP.NET Web フォーム アプリケーションを構成します。  
 この手順では、*Web.config* 構成ファイルに構成エントリを追加し、アカウントの要求情報を表示するに *Default.aspx* を変更します。  
  
#### 要求の ASP.NET アプリケーションが Windows 認証を使用して構成するには  
  
1.  **TestApp** のプロジェクトで *Default.aspx ファイル* では、既存のマークアップに置き換えます。:  
  
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
  
     この手順は、Windows 認証から取得された要求が設定された *Default.aspx ページ* に GridView コントロールを追加します。  
  
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
                this.ClaimsGridView.DataSource = claimsPrincipal.Claims;  
                this.ClaimsGridView.DataBind();  
            }  
        }  
    }  
    ```  
  
     上のコードは認証されたユーザーに関する要求が表示されます。  
  
3.  次の構成エントリだけを含むように、アプリケーションの認証タイプを変更するには、プロジェクトのルートの *Web.config ファイル* の **\<system.web\>** のセクションの **\<authentication\>** ブロックを変更する:  
  
    ```  
    <authentication mode="Windows" />  
    ```  
  
4.  最後に、認証を強制的に同じ *Web.config ファイル* の **\<system.web\>** のセクションの **\<authorization\>** ブロックを変更する:  
  
    ```  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    ```  
  
## 手順 3 \- ソリューションをテストします。  
 この手順では、ASP.NET Web フォーム アプリケーションをテストし、ユーザーが Windows 認証を使用する場合、要求があることを確認します。  
  
#### 要求の ASP.NET Web フォーム アプリケーションを Windows 認証を使用してテストするには  
  
1.  F5 キーを押してアプリケーションをビルドし、実行します。  *Default.aspx*、という名前の Windows アカウント名は、ページの右上の認証済みユーザーとしてドメイン名 \(など\) が表示されます。  ページの内容は、Windows のアカウントから取得された要求が設定されているテーブルを含める必要があります。