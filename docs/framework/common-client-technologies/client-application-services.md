---
title: クライアント アプリケーション サービス
ms.date: 03/30/2017
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
ms.openlocfilehash: d67b7467bdacdfca054d0ecd11a81c7d25b158f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743226"
---
# <a name="client-application-services"></a>クライアント アプリケーション サービス
クライアント アプリケーション サービスにより、Microsoft ASP.NET 2.0 AJAX Extensions に含まれる [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] のログイン、ロール、およびプロファイル アプリケーション サービスを使用する Windows ベースのアプリケーションを簡単に作成できます。 これらのサービスにより、複数の Web ベースおよび Windows ベースのアプリケーションで、単一のサーバーから提供されるユーザー情報とユーザー管理機能を共有できます。 たとえば、これらのサービスを使用して、次のタスクを実行できます。  
  
-   ユーザーを認証します。 認証サービスを使用して、ユーザー ID を検証することができます。  
  
-   認証されたユーザーのロールを確認します。 ロール サービスを使用して、ユーザーのロールに応じてアプリケーションのユーザー インターフェイスを変更できます。 たとえば、管理者ロールのユーザーには機能を追加して提供することができます。  
  
-   サーバー上に存在する、ユーザーごとのアプリケーションの設定を保存してアクセスします。 Web 設定サービス (プロファイル サービスとも呼ばれます) を使用して、複数のアプリケーションや場所で設定を共有することができます。  
  
 クライアント アプリケーション サービスは、アプリケーション構成ファイルで指定できるクライアントのサービス プロバイダーの Web サービス拡張モデルを活用します。 これらのサービス プロバイダーには、ネットワーク接続が利用できない場合、認証、ロール、および設定のデータのローカル キャッシュを使用するオフライン機能が含まれます。  
  
 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスの詳細については、「[ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 クライアント アプリケーション サービス プロバイダーを介して使用できる機能について説明します。  
  
 [方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 このトピックでは、Visual Studio プロジェクト デザイナーを使用して、アプリケーション サービスを有効にし、構成する方法について説明します。 対応する App.config ファイルへの変更についても説明します。  
  
 [方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 アプリケーションがクライアントの認証サービス プロバイダーを使用するよう構成される場合のユーザー検証方法について説明します。  
  
 [チュートリアル : クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 すべてのクライアント アプリケーション サービスの機能を1 つのアプリケーションに結合する方法について説明します。 このチュートリアルでは、エンド ツー エンドのガイダンスを示します。 たとえば、クライアント アプリケーション サービスのテストに使用できる ASP.NET Web サービス アプリケーションを作成する方法の手順が含まれます。  
  
## <a name="reference"></a>参照  
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
  
## <a name="see-also"></a>参照  
 [ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [ASP.NET AJAX でのフォーム認証の使用](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [ASP.NET AJAX でのロール情報の使用](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [ASP.NET AJAX でのプロファイル情報の使用](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET の認証](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [ロールを使用した承認の管理](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [アプリケーション設定の概要](../../../docs/framework/winforms/advanced/application-settings-overview.md)
