---
title: "方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# 方法: WIF を使用してクレーム対応 ASP.NET MVC Web アプリケーションをビルドする
## 対象  
  
-   Microsoft® Windows® の ID Foundation \(WIF\)  
  
-   MVC ASP.NET®  
  
## 概要  
 ここでは、単純な要求に対応した ASP.NET MVC Web アプリケーションを作成する詳細な手順を示します。  また、命令をクレームベース認証の正常な実装の単純な要求に対応した ASP.NET MVC Web アプリケーションをテストする方法を提供します。  ここでは、セキュリティ トークン Services \(STS\) を作成するための詳細な手順がなく、既に STS を構成していることを前提としています。  
  
## 内容  
  
-   対象  
  
-   手順の概要  
  
-   手順 1 \- 単純な ASP.NET MVC アプリケーションを作成します。  
  
-   手順 2 \- クレームベース認証用の ASP.NET MVC アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
-   関連項目  
  
## 対象  
  
-   クレームベース認証用の ASP.NET MVC Web アプリケーションを構成します。  
  
-   正常な要求に対応した ASP.NET MVC Web アプリケーションをテストします。  
  
## 手順の概要  
  
-   手順 1 \- 単純な ASP.NET MVC アプリケーションを作成します。  
  
-   手順 2 \- クレームベース認証用の ASP.NET MVC アプリケーションを構成します。  
  
-   手順 3 \- ソリューションをテストします。  
  
## 手順 1 \- 単純な ASP.NET MVC アプリケーションを作成します。  
 この手順では、新しい ASP.NET MVC アプリケーションを作成します。  
  
#### 単純な ASP.NET MVC アプリケーションを作成するには  
  
1.  次に、Visual Studio を起動し、**ファイル**、**新規作成**と **プロジェクト**をクリックします。  
  
2.  **新しいプロジェクト** のペインで、**ASP.NET MVC 3 Web アプリケーション**をクリックします。  
  
3.  **名前**では、`TestApp` を入力し、**OK**を押します。  
  
4.  **新しい ASP.NET MVC 3 プロジェクト** ダイアログ ボックスで、**エンジンの表示** が **Razor**に設定され、次にをクリック **OK**するために使用できるテンプレートから **インターネット アプリケーション** になります選択します。  
  
5.  新しいプロジェクトが開かれると、**ソリューション エクスプローラー** の **TestApp** プロジェクトを右クリックし、**プロパティ** のオプションを選択します。  
  
6.  プロジェクトのプロパティ ページで、左側の **Web** のタブをクリックし、**ローカル IIS Web サーバーを使用する** のが選択されていることを確認します。  
  
## 手順 2 \- クレームベース認証用の ASP.NET MVC アプリケーションを構成します。  
 この手順で必要な認識する、ASP.NET MVC Web アプリケーションの *Web.config 構成ファイル* に構成エントリを追加します。  
  
#### クレームベース認証用の ASP.NET MVC アプリケーションを構成するには  
  
1.  *Web.config 構成ファイル* に次の構成セクションの定義を追加します。  これらは Windows ID の基本に必要な構成セクションを定義します。  **\<configuration\>** の開始要素の直後の定義を追加します:  
  
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
  
4.  次の Windows ID の基本関連構成エントリを追加し、ASP.NET アプリケーションの URL とポート番号が **\<wsFederation\>** の要素の **\<audienceUris\>** エントリ、**領域** の属性、および **\<wsFederation\>** の要素の **応答** の属性の値が一致することを確認します。  また **発行者** の値がセキュリティ トークン サービスの \(STS\) の URL を満たしていることを確認します。  
  
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
  
5.  [System.IdentityModel](assetId:///System.IdentityModel?qualifyHint=False&amp;autoUpgrade=True) のアセンブリへの参照を追加します。  
  
6.  エラーを得るためにソリューションをコンパイルします。  
  
## 手順 3 \- ソリューションをテストします。  
 この手順で構成されたクレームベース認証用の ASP.NET MVC Web アプリケーションをテストします。  基本的なテストを実行するには、単純なコードは、セキュリティ トークン Services \(STS\) によって発行されたトークンの表示の要求追加します。  
  
#### クレームベース認証用の ASP.NET、MVC アプリケーションをテストできます。  
  
1.  **ソリューション エクスプローラー**に、エディターの **コントローラ** のフォルダーを開きます *HomeController.cs ファイルを* 展開します。  **インデックス** のメソッドに次のコードを追加します:  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
  
    ```  
  
2.  次に **ソリューション エクスプローラー** エディターでの **ビュー** と **ホーム** フォルダーを開きます *Index.cshtml ファイルを* 配置します。  コンテンツを削除し、次のマークアップを追加します:  
  
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
  
3.  **F5** キーを押してソリューションを実行します。  
  
4.  セキュリティ トークン サービスにより、に発行されたトークンの要求を表示するページという名前を付ける必要があります。  
  
## 関連項目  
  
-   [方法: WIF を使用してクレーム対応 ASP.NET Web フォーム アプリケーションをビルドする](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)