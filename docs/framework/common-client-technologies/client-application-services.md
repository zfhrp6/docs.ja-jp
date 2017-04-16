---
title: "クライアント アプリケーション サービス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション設定, クライアント アプリケーション サービス"
  - "ASP.NET サービス, クライアント アプリケーション サービス"
  - "認証 [ASP.NET], クライアント アプリケーション サービス"
  - "クライアント アプリケーション サービス"
  - "クライアント アプリケーション サービス, クライアント アプリケーション サービスの概要"
  - "クライアント アプリケーション, ASP.NET サービス"
  - "資格情報 [.NET Framework]"
  - "ログイン [クライアント アプリケーション サービス]"
  - "プロファイル [ASP.NET], クライアント アプリケーション サービス"
  - "ロール ベースのセキュリティ [.NET Framework], クライアント アプリケーション サービス"
  - "ロール [.NET Framework], クライアント アプリケーション サービス"
  - "共有 (情報と機能を) [クライアント アプリケーション サービス]"
  - "Web 設定 [クライアント アプリケーション サービス]"
  - "Windows ベースのアプリケーション, クライアント アプリケーション サービス"
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# クライアント アプリケーション サービス
クライアント アプリケーション サービスにより、Microsoft ASP.NET 2.0 AJAX Extensions に含まれる [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] のログイン、ロール、およびアプリケーション サービスを使用する Windows ベースのアプリケーションを簡単に作成できます。  これらのサービスにより、複数の Web アプリケーションおよび Windows ベースのアプリケーションで、単一のサーバーから提供されるユーザー情報とユーザー管理機能を共有できます。  たとえば、これらのサービスを使用して、次のタスクを実行できます。  
  
-   ユーザーを認証します。  認証サービスを使用して、ユーザー ID を検証することができます。  
  
-   認証されたユーザーのロールを確認します。  ロール サービスを使用して、ユーザーのロールに応じてアプリケーションのユーザー インターフェイスを変更できます。  たとえば、管理者ロールのユーザーには機能を追加して提供することができます。  
  
-   サーバー上に存在する、ユーザーごとのアプリケーションの設定を保存してアクセスします。  Web 設定サービス \(プロファイル サービスとも呼ばれます\) を使用して、複数のアプリケーションや場所で設定を共有することができます。  
  
 クライアント アプリケーション サービスは、アプリケーション構成ファイルで指定できるクライアントのサービス プロバイダーの Web サービス拡張モデルを活用します。  これらのサービス プロバイダーには、ネットワーク接続が利用できない場合、認証、ロール、および設定のデータのローカル キャッシュを使用するオフライン機能が含まれます。  
  
 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスの詳細については、「[ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md)」を参照してください。  
  
## このセクションの内容  
 [クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 クライアント アプリケーション サービス プロバイダーを介して使用できる機能について説明します。  
  
 [方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 このトピックでは、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] プロジェクト デザイナーを使用して、アプリケーション サービスを有効にし、構成する方法について説明します。  対応する App.config ファイルへの変更についても説明します。  
  
 [方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 アプリケーションがクライアントの認証サービス プロバイダーを使用するよう構成される場合のユーザー検証方法について説明します。  
  
 [チュートリアル : クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 すべてのクライアント アプリケーション サービスの機能を1 つのアプリケーションに結合する方法について説明します。  このチュートリアルでは、エンド ツー エンドのガイダンスを示します。  たとえば、クライアント アプリケーション サービスのテストに使用できる ASP.NET Web サービス アプリケーションを作成する方法の手順が含まれます。  
  
## 関連項目  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## 参照  
 [ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md)   
 [Using Forms Authentication with Microsoft Ajax](../Topic/Using%20Forms%20Authentication%20with%20Microsoft%20Ajax.md)   
 [Using Roles Information with Microsoft Ajax](../Topic/Using%20Roles%20Information%20with%20Microsoft%20Ajax.md)   
 [Using Profile Information with Microsoft Ajax](../Topic/Using%20Profile%20Information%20with%20Microsoft%20Ajax.md)   
 [ASP.NET Authentication](../Topic/ASP.NET%20Authentication.md)   
 [Managing Authorization Using Roles](../Topic/Managing%20Authorization%20Using%20Roles.md)   
 [OLD NIB: Managing Application Settings](http://msdn.microsoft.com/ja-jp/7de3c3bd-e0dc-4e75-a1aa-7b0ecfaac4fc)   
 [アプリケーション設定の概要](../../../docs/framework/winforms/advanced/application-settings-overview.md)