---
title: "クライアント アプリケーション サービスの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client application services, classes
- client application services, about client application services
ms.assetid: f0a2da13-e282-4fd7-88a1-f9102c9aeab1
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5719cf7cfb5ec99f1bfbf952048e98c9465e1fa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services-overview"></a>クライアント アプリケーション サービスの概要
クライアント アプリケーション サービスにより、Windows フォーム アプリケーションおよび Windows Presentation Foundation (WPF) アプリケーションから [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] ログイン サービス、ロール サービス、プロファイル サービスに簡単にアクセスできます。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスは、[!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)] と [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] に付属している Microsoft ASP.NET 2.0 AJAX Extensions に含まれています。 これらのサービスにより、複数の Web ベースおよび Windows ベースのアプリケーションで、単一のサーバーから提供されるユーザー情報とユーザー管理機能を共有できます。  
  
 クライアント アプリケーション サービスには、Web サービス機能拡張モデルに組み込まれるクライアント サービス プロバイダーが含まれており、これにより、Windows ベースのアプリケーションで次のことが可能になります。  
  
-   シンプルなクライアント構成。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] プロジェクト デザイナーを使用するか、プロジェクトの App.config ファイルでクライアント サービス プロバイダーを指定することにより、ログイン サービス、ロール サービス、およびプロファイル サービスを有効化して構成することができます。 詳細については、「[方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。  
  
-   簡明なプログラミング。 クライアント アプリケーション サービスを有効にして構成すると、既存の [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] のメンバーシップ クラス、ロール クラス、およびアプリケーション設定クラスから間接的にサービス プロバイダーにアクセスできるようになります。 クライアント アプリケーション サービスを実装する [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] クラスに直接アクセスすることもできます。 しかし、ほとんどの場合、直接アクセスは不要です。 クライアント アプリケーション サービスのクラスの詳細については、このトピックの「クライアント アプリケーション サービスのクラス」を参照してください。  
  
-   オフラインのサポート。 Windows ベースのアプリケーションは、多くの場合、接続頻度の低い環境下に置かれます。 アプリケーションがオンラインのときに、クライアント サービス プロバイダーは、サーバーから取得された値をオフライン時にも使用できるようにキャッシュします。  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] アプリケーション設定デザイナーとの統合。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でプロジェクトに設定を追加するときに、クライアント設定サービス プロバイダーを介してアクセスされる設定を指定できます。  
  
 以下のセクションでは、これらの機能について詳しく説明します。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスの詳細については、「[ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)」を参照してください。  
  
## <a name="authentication"></a>認証  
 クライアント アプリケーション サービスを使用して、既存の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 認証サービスを介してユーザーを検証できます。 Windows 認証またはフォーム認証を使用してユーザーを認証できます。 Windows 認証では、ユーザーがコンピューターまたはドメインにログオンしたときにオペレーティング システムによって付与されたユーザー ID が使用されます。 通常、社内イントラネット上に配置されているアプリケーションにはWindows 認証を使用します。 フォーム認証では、アプリケーションにログイン コントロールを組み込み、取得した資格情報を認証プロバイダーに渡します。 通常、インターネット上に配置されたアプリケーションにはフォーム認証を使用します。  
  
 ユーザーを検証するには、`static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> メソッドを呼び出します。 このメソッドは、アプリケーションで構成されているクライアント サービス プロバイダーにアクセスし、ユーザーが有効であるかどうかを示す <xref:System.Boolean> 値を返します。 詳細については、「[方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)」を参照してください。  
  
 Windows 認証を使用している場合は、<xref:System.Web.Security.Membership.ValidateUser%2A> メソッドのパラメーターとして空の文字列または `null` を渡す必要があります。 Windows 認証を使用している場合、このメソッドを呼び出すと常に `true` が返されます。  
  
 フォーム認証では、<xref:System.Web.Security.Membership.ValidateUser%2A> メソッドは、リモート サービスがユーザーを認証したかどうかを示す値を返します。 検証が成功すると、認証クッキーがローカル ハード ディスクに格納されます。 ロール サービスおよび設定サービスにアクセスする際、このクッキーが検証の確認に使用されます。  
  
 フォーム認証を使用している場合は、ユーザー名とパスワードを <xref:System.Web.Security.Membership.ValidateUser%2A> メソッドに渡すことができます。 また、パラメーターとして空の文字列または `null` を渡して、資格情報プロバイダーを使用することもできます。 資格情報プロバイダーは、アプリケーション構成で指定するクラスです。 資格情報プロバイダー クラスは、<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装する必要があります。このインターフェイスには、<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> という単一のメソッドがあります。 資格情報プロバイダーを使用することにより、複数のアプリケーション間で同じログイン ダイアログ ボックスを共有できます。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。  
  
 フォーム認証で資格情報プロバイダーを使用するようにアプリケーションを構成する際には、<xref:System.Web.Security.Membership.ValidateUser%2A> メソッドのパラメーターとして空の文字列または `null` を渡す必要があります。 サービス プロバイダーは <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> メソッド実装を呼び出します。 通常、このメソッドを実装してダイアログ ボックスを表示し、データが設定された <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> オブジェクトを返します。  
  
 認証の詳細については、「[ASP.NET の認証](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)」を参照してください。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] 認証サービスの設定方法の詳細については、「[ASP.NET AJAX でのフォーム認証の使用](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)」を参照してください。  
  
## <a name="roles"></a>役割  
 クライアント アプリケーション サービスを使用して、既存の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] ロール サービスからロール情報を取得できます。 現在の認証済みユーザーが特定のロールに属すかどうかを判断するには、`static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティから取得された <xref:System.Security.Principal.IPrincipal> 参照の <xref:System.Security.Principal.IPrincipal.IsInRole%2A> メソッドを呼び出します。 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> メソッドは、パラメーターとしてロール名を受け取り、現在のユーザーが特定のロールにあるかどうかを示す <xref:System.Boolean> 値を返します。 ユーザーが認証されない場合、または指定されたロールに属していない場合、このメソッドは `false` を返します。  
  
 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] ロール サービスの設定方法の詳細については、「[ASP.NET AJAX でのロール情報の使用](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)」を参照してください。  
  
## <a name="settings"></a>設定  
 クライアント アプリケーション サービスを使用して、既存の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] プロファイル サービスからユーザー アプリケーション設定を取得できます。 クライアント アプリケーション サービスの Web 設定機能は、[!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] のアプリケーション設定機能と統合されています。 Web 設定を取得するには、まず、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] プロジェクト デザイナーの **[設定]** タブを使用して、プロジェクトの `Settings` クラス (C# では `Properties.Settings.Default`、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `My.Settings` としてアクセスされる) を生成します。 **[設定]** タブの **[Web 設定の読み込み]** ボタンをクリックして Web 設定を読み込み、これを生成された `Settings` クラスに追加することができます。 すべての認証済みユーザーまたはすべての匿名ユーザーによって使用されるように構成された Web 設定を使用できます。  
  
 アプリケーション設定の詳細については、「[アプリケーション設定の概要](../../../docs/framework/winforms/advanced/application-settings-overview.md)」を参照してください。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で設定クラスを生成するのではなく独自の設定クラスを実装する方法の詳細については、「[方法: アプリケーション設定を作成する](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)」を参照してください。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] プロファイル サービスの設定方法の詳細については、「[ASP.NET AJAX でのプロファイル情報の使用](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)」を参照してください。  
  
## <a name="client-application-services-classes"></a>クライアント アプリケーション サービスのクラス  
 次の表は、クライアント アプリケーション サービス機能を実装するクラスの説明です。  
  
 認証、ロール、および設定の主要な機能のみを使用するアプリケーションであれば、これらのクラスに直接アクセスする必要はありません。 このようなアプリケーションは、前のセクションで説明したアプリケーション構成や API を使用して間接的にクライアント アプリケーション サービス プロバイダーにアクセスします。 ユーザーのログアウト機能やオフライン機能などの追加機能を実装する場合は、これらのクラスに直接アクセスする必要があります。  
  
> [!NOTE]
>  すべてのクライアント アプリケーション サービスの API は同期的です。 クライアント アプリケーション サービスは、非同期動作を直接にはサポートしていません。  
  
 クライアント アプリケーション サービス プロバイダーは、標準 [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] 型を実装または拡張しますが、これらの型で定義されるメンバーと機能をすべて実装するわけではありません。 たとえば、クライアント アプリケーション サービス プロバイダーを使用して、新しいユーザーの作成や、ロール メンバーシップを管理するユーザー管理アプリケーションを実装することはできません。 この機能を実装するには、現在のところ Web アプリケーションとサーバー側のコードを使用する必要があります。 実装されてないメンバーを確認するには、この表に示されているリンクから、リファレンス ドキュメントを参照してください。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Web.ClientServices.ClientFormsIdentity>|このクラスは、フォーム認証のユーザー ID と認証クッキーを管理します。<br /><br /> このクラスに直接アクセスする主な理由は、ユーザーを自動的に再検証する <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> メソッドを呼び出すためです。たとえば、オフライン モードからオンライン モードに切り替える場合などが該当します。<br /><br /> フォーム認証を使用してユーザーが認証された後、`static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティを介して取得される <xref:System.Security.Principal.IPrincipal> 参照の <xref:System.Security.Principal.IPrincipal.Identity%2A> プロパティを使用してこのクラスのインスタンスを取得できます。|  
|<xref:System.Web.ClientServices.ClientRolePrincipal>|このクラスは、ユーザー ロールを管理します。<br /><br /> このクラスには、間接的にアクセスできないメンバーはありません。 ただし、ユーザーが認証された後は、`static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティを使用してこのクラスのインスタンスにアクセスできます。|  
|<xref:System.Web.ClientServices.ConnectivityStatus>|このクラスは、アプリケーションをオフライン モードに切り替える際に使用する `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> プロパティを提供します。|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>|このクラスはユーザー資格情報を表します。<br /><br /> このクラスは、<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装する際、<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> メソッドの戻り値の型としてのみ使用します。|  
|<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>|このクラスは、フォーム認証のリモート認証サービスへのアクセスを管理します。<br /><br /> このクラスに直接アクセスする主な理由は、<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> メンバーと <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> メンバーを使用するためです。これらのメンバーは、基本 <xref:System.Web.Security.MembershipProvider> クラスでは実装されません。 また、<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.ServiceUri%2A> プロパティを使用して、サービスの場所をプログラムによって設定することもできます。<br /><br /> このクラスのインスタンスは、`static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> プロパティを使用して取得できます。|  
|<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>|このクラスは Windows 認証を管理します。<br /><br /> このクラスに直接アクセスする主な理由は、<xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider.Logout%2A> メソッドを呼び出すためです。 ログアウト後、ユーザーは Windows に対しては認証されていますが、リモート アプリケーション サービスにはアクセスできなくなります。<br /><br /> このクラスのインスタンスは、`static` <xref:System.Web.Security.Membership.Provider%2A?displayProperty=nameWithType> プロパティを使用して取得できます。|  
|<xref:System.Web.ClientServices.Providers.ClientRoleProvider>|このクラスは、リモート ロール サービスへのアクセスを管理します。<br /><br /> このクラスにアクセスする主な理由は、<xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> メソッドを呼び出すためです。 これは、アプリケーションがゼロ以外のロール サービス キャッシュのタイムアウト値を使用するように構成されている場合に便利です。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。 また、<xref:System.Web.ClientServices.Providers.ClientRoleProvider.ServiceUri%2A> プロパティを使用して、サービスの場所をプログラムによって設定することもできます。<br /><br /> このクラスのインスタンスは、`static` <xref:System.Web.Security.Roles.Provider%2A?displayProperty=nameWithType> プロパティを使用して取得できます。|  
|<xref:System.Web.ClientServices.Providers.ClientSettingsProvider>|このクラスは、リモート Web 設定サービスへのアクセスを管理します。<br /><br /> このクラスにアクセスする主な理由は、<xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> イベントを処理するためです。 また、<xref:System.Web.ClientServices.Providers.ClientSettingsProvider.ServiceUri%2A> プロパティを使用して、サービスの場所をプログラムによって設定することもできます。|  
|<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>|このインターフェイスは、このトピックの「認証」セクションで先述されているように、アプリケーションが検証時にユーザーの資格情報を取得するための間接的な手段を提供します。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。|  
|<xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>|このクラスは、<xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> イベント ハンドラー内で使用する <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs.FailedSettingsList%2A> プロパティを提供します。|  
|<xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>|このクラスは、<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.UserValidated> イベント ハンドラー内で使用する <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs.UserName%2A> プロパティを提供します。|  
  
## <a name="see-also"></a>関連項目  
 [クライアント アプリケーション サービス](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [チュートリアル : クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [アプリケーション設定の概要](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [ASP.NET AJAX でのフォーム認証の使用](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [Microsoft Ajax を使用したロール情報を使用します。](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [Microsoft Ajax でのプロファイル情報の使用](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [ASP.NET 認証](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [ロールを使用して承認を管理します。](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  
 [SQL Server 向けアプリケーション サービス データベースの作成と構成](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
