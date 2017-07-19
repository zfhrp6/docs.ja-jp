---
title: "カスタムのトークン ハンドラー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# カスタムのトークン ハンドラー
このトピックでは、WIF にトークンの処理にどのように使用するかトークン ハンドラーについて説明します。  WIF トピックでは、既定ではサポートされていないトークンの種類のカスタム トークン ハンドラーを作成する必要のあるものについて説明します。  
  
## WIF トークン ハンドラーの概要  
 WIF は、セキュリティ トークンのハンドラーに、作成するために、書き込み、依存し、証明書利用者の \(RP\) アプリケーションまたはセキュリティ トークン サービス \(STS\) のトークンを検証します。  トークン ハンドラーは WIF パイプラインのカスタム トークン ハンドラーを追加したり、既存のトークン ハンドラーがトークンを管理する方法をカスタマイズする機能拡張ポイントです。  WIF、必要に応じて機能を変更できるように変更するか、完全にオーバーライドできる 9 種類の組み込みセキュリティ トークンのハンドラーを提供します。  
  
## WIF の組み込みセキュリティ トークンのハンドラー  
 WIF 4.5 は、抽象基本クラスから派生 <xref:System.IdentityModel.Tokens.SecurityTokenHandler>9 種類のセキュリティ トークンのハンドラー クラスが含まれています:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## カスタム トークン ハンドラーの追加  
 簡単な Web トークン \(SWT\) と JSON Web トークン \(JWT\) など、トークンの種類に、WIF に用意されている組み込みのトークン ハンドラーはありません。  これらのトークンの種類と組み込みハンドラーがないそのほか、カスタム トークン ハンドラーを作成するには、次の手順を実行する必要があります。  
  
#### カスタム トークン ハンドラーの追加  
  
1.  <xref:System.IdentityModel.Tokens.SecurityTokenHandler>から派生する新しいクラスを作成します。  
  
2.  次のメソッドをオーバーライドして、独自の実装を提供する:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  WIF に適用する **\<system.identityModel\>** のセクション内の *Web.config* または *App.config* の新しいカスタム トークン ハンドラーへの参照を追加します。  たとえば、次の構成のマークアップは **MyCustomTokenHandler** という名前の **CustomToken** の名前空間を設定する新しいトークン ハンドラーを指定します。  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     既に組み込みのトークン ハンドラーを持つ型トークンを処理する独自のトークン ハンドラーを提供する場合は、既定のハンドラーを削除して、カスタム ハンドラーを使用するように **\<remove\>** の要素を追加する必要があることに注意してください。  たとえば、次の構成にカスタム トークン ハンドラーで既定値を置き換えます <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> :  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type=”System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789”>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```