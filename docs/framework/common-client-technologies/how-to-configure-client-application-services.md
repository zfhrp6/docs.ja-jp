---
title: '方法 : クライアント アプリケーション サービスを構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- client application services, configuring
ms.assetid: 34a8688a-a32c-40d3-94be-c8e610c6a4e8
ms.openlocfilehash: 004798ce8cf429f2a94d856e6b3a55447c2ad5fa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-client-application-services"></a>方法 : クライアント アプリケーション サービスを構成する
このトピックでは、Visual Studio **プロジェクト デザイナー**を使用して、クライアント アプリケーション サービスを有効にし、構成する方法について説明します。 クライアント アプリケーション サービスを使用してユーザーを検証し、既存の [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスからユーザーのロールおよび設定を取得することができます。 構成した後に、「[クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)」に記載されているように、アプリケーション コード内で有効にされているサービスにアクセスできます。 [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] アプリケーション サービスの詳細については、「[ASP.NET アプリケーション サービスの概要](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)」を参照してください。  
  
 クライアント アプリケーション サービスは、**プロジェクト デザイナー**の **[サービス]** ページで有効にし、構成することができます。 **[サービス]** ページは、プロジェクトの App.config ファイル内の値を更新します。 **プロジェクト デザイナー**にアクセスするには、**[プロジェクト]** メニューの **[プロパティ]** を使用します。 **[サービス]** ページの詳細については、「[Services Page, Project Designer](https://msdn.microsoft.com/library/bb398109)」([サービス] ページ (プロジェクト デザイナー)) を参照してください。  
  
 次の手順では、クライアント アプリケーション サービスの基本構成を実行する方法について説明します。 高度な構成オプションについては、以降のセクションで説明します。  
  
### <a name="to-configure-client-application-services"></a>クライアント アプリケーション サービスを構成するには  
  
1.  **ソリューション エクスプ ローラー**で、プロジェクト ノードを選択し、**[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
     **プロジェクト デザイナー**が表示されます。  
  
2.  **[サービス]** タブをクリックします。次の図に示すように、**[サービス]** ページが表示されます。  
  
     ![プロジェクト デザイナーの [サービス] タブ](../../../docs/framework/common-client-technologies/media/casdesigner.png "casdesigner")  
  
3.  **[サービス]** ページで、**[クライアント アプリケーション サービスを有効にする]** を選択します。  
  
    > [!NOTE]
    >  クライアント アプリケーション サービスには完全版の .NET Framework が必要です。クライアント アプリケーション サービスは、.NET Framework Client Profile ではサポートされません。 **[クライアント アプリケーション サービスを有効にする]** チェック ボックスが無効になっている場合、**[ターゲット フレームワーク]** が .NET Framework 3.5 以降に設定されていることを確認します。 C# で **[ターゲット フレームワーク]** の設定を表示するには、プロジェクト デザイナーを開き、**[アプリケーション]** ページをクリックします。 Visual Basic で **[ターゲット フレームワーク]** の設定を表示するには、プロジェクト デザイナーを開き、**[コンパイル]** ページをクリックして、**[詳細コンパイル オプション]** をクリックします。  
  
4.  独自のログイン コントロールまたはダイアログ ボックスを提供する場合は **[フォーム認証を使用する]** を選択し、オペレーティング システムによって付与された ID を使用する場合は **[Windows 認証を使用する]** を選択します。 詳細については、「[クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)」を参照してください。  
  
    > [!NOTE]
    >  **[Windows 認証を使用する]** を選択すると、SQL Server Compact データベースを使用するために、クライアント アプリケーション サービスが自動的に構成されます。 これは次のセクションで説明するように、**[サービスの詳細設定]** ダイアログ ボックスに示されます。 **[フォーム認証を使用する]** を選択すると、**[カスタム接続文字列を使用する]** の設定は自動的にオフになりません。 これにより、[!INCLUDE[ssEW](../../../includes/ssew-md.md)] データベースが Windows 認証で使用するために既に生成されている場合、エラーが発生することがあります。 これらのエラーを修正するには、**[サービスの詳細設定]** ダイアログ ボックスの **[カスタム接続文字列を使用する]** の設定をオフにします。  
  
5.  **[フォーム認証を使用する]** を選択した場合は、**[認証サービスの場所]** ボックスで、ファイル名を含まないサービス ホストの URL を指定します。 デザイナーは、構成ファイルに値を書き込むときに、自動的に標準のファイル名 (Authentication_JSON_AppService.axd) を追加します。  
  
6.  必要に応じて、**[フォーム認証を使用する]** を選択した場合は、**[資格情報プロバイダー]** ボックスに値を指定することができます。 資格情報プロバイダーは、<xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装する必要があります。 資格情報プロバイダーを使用すると、他のアプリケーション コードからログイン ユーザー インターフェイスを分離できます。 これにより、複数のアプリケーションで使用する単一のログイン ダイアログ ボックスを作成することができます。 詳細については、「[方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)」を参照してください。  
  
     資格情報プロバイダーを指定する場合は、アセンブリ修飾型名としてを指定する必要があります。 詳細については、「<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>」および「[アセンブリ名](../../../docs/framework/app-domains/assembly-names.md)」を参照してください。 最も単純な形式で、アセンブリ修飾型名は、次のようになります。  
  
    ```  
    MyNamespace.MyLoginClass, MyAssembly  
    ```  
  
7.  **[ロール サービスの場所]** および **[Web 設定サービスの場所]** テキスト ボックスで、ファイル名を含まない、各サービスのサービスの場所を指定します。 デザイナーは、構成ファイルに値を書き込むときに、自動的に標準的なファイル名 (Role_JSON_AppService.axd および Profile_JSON_AppService.axd) を追加します。  
  
8.  必要に応じて、**[詳細設定]** をクリックして、ローカル キャッシュ動作などの詳細設定を変更します。 詳細については、次の手順を参照してください。  
  
## <a name="advanced-configuration"></a>詳細構成  
 次の手順では、あまり一般的ではないシナリオでクライアント アプリケーション サービスを構成する方法について説明します。 たとえば、これらの構成オプションは、公共の場所で使用したり、ローカル データ キャッシュとして暗号化された SQL Server Compact データベースを使用するために使用したりできます。  
  
#### <a name="to-configure-advanced-settings-for-client-application-services"></a>クライアント アプリケーション サービスの詳細設定を構成するには  
  
1.  **プロジェクト デザイナー**の **[サービス]** ページで、**[詳細設定]** をクリックします。  
  
     次の図に示すように、**[サービスの詳細設定]** ダイアログ ボックスが表示されます。 このダイアログ ボックスの詳細については、「[[サービスの詳細設定] ダイアログ ボックス](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)」を参照してください。  
  
     ![[サービスの詳細設定] ダイアログ ボックス](../../../docs/framework/common-client-technologies/media/casdialog.png "casdialog")  
  
2.  **[オフラインでログインできるようにパスワードのハッシュをローカルに保存する]** をオンまたはオフにします。 このオプションを選択すると、ユーザーのパスワードの暗号化された形式がローカルでキャッシュされます。 これは、アプリケーションにオフライン モードを実装する場合に便利です。 このオプションを選択すると、<xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> プロパティが `true` に設定されている場合でもユーザーを検証できます。  
  
3.  **[サーバー Cookie の期限が切れた場合は常に再度ログオンすることをユーザーに要求する]** をオンまたはオフにします。 認証 Cookie はリモート サービスで構成され、ユーザーのログインがアクティブであり続ける期間を示します。 Cookie を構成する方法の詳細については、「[authentication の forms 要素 (ASP.NET 設定スキーマ)](http://msdn.microsoft.com/library/8163b8b5-ea6c-46c8-b5a9-c4c3de31c0b3)」の「`timeout` 属性」を参照してください。  
  
     このオプションを選択した場合、認証 Cookie の有効期限が切れた後にリモート ロールまたは Web 設定サービスにアクセスしようとすると、<xref:System.Net.WebException> がスローされます。 この例外を処理し、ログイン ダイアログ ボックスを表示して、ユーザーを再検証することができます。 この動作の例は、「[チュートリアル: クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)」を参照してください。 このオプションは、公共の場所に配置されたアプリケーションで、使用後にアプリケーションを実行中のままにしているユーザーが無期限に認証されないようにするのに便利です。  
  
     このオプションをオフにし、認証 Cookie の有効期限が切れた後にリモート サービスへのアクセスを試行すると、ユーザーが自動的に再検証されます。  
  
4.  **[ロール サービスのキャッシュのタイムアウト]** の値を指定します。 この時間間隔は、ロールが頻繁に更新される場合は小さい値に設定し、ロールが頻繁に更新されない場合はより大きい値に設定します。 オフライン モードを実装する場合は、時間間隔を大きい値に設定して、ロール情報が、アプリケーションがオフラインのときに期限切れにならないようにします。  
  
     <xref:System.Web.Security.RolePrincipal.IsInRole%2A> メソッドを呼び出すと、ロール プロバイダーがキャッシュされたロール値またはロール サービスにアクセスします。 プログラムによってキャッシュをリセットし、強制的にこのメソッドがリモート サービスにアクセスするようにするには、<xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A> メソッドを呼び出します。  
  
5.  **[カスタム接続文字列を使用する]** をオンまたはオフにします。 詳細については、次の手順を参照してください。  
  
#### <a name="to-configure-client-application-services-to-use-a-database-for-the-local-cache"></a>ローカル キャッシュ用データベースを使用するようにクライアント アプリケーション サービスを構成するには  
  
1.  **プロジェクト デザイナー**の **[サービス]** ページで、**[詳細設定]** をクリックします。  
  
     **[サービスの詳細設定]** ダイアログ ボックスが表示されます。  
  
2.  **[カスタム接続文字列を使用する]** を選択します。  
  
     テキスト ボックスに `Data Source = |SQL/CE|` の既定値が表示されます。  
  
3.  SQL Server Compact データベースを生成して使用するには、接続文字列の既定値を保持します。 Visual Studio はデータベース ファイルを生成し、<xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> プロパティで指定されるディレクトリにそれを格納します。  
  
4.  暗号化された [!INCLUDE[ssEW](../../../includes/ssew-md.md)] データベースを生成し、使用するには、次の例に示すように、接続文字列に `password` および `encrypt database` 値を追加します。  
  
    > [!NOTE]
    >  必ず、強力なパスワードを指定してください。 データベースが生成された後は、パスワードを変更することはできません。  
  
    ```  
    Data Source = |SQL/CE|;password=<password>;encrypt database=true  
    ```  
  
5.  独自の SQL Server データベースを使用するには、独自の接続文字列を指定します。 有効な接続文字列の形式の詳細については、SQL Server のドキュメントを参照してください。 このデータベースは自動的には生成されません。 接続文字列は、次の SQL ステートメントを使用して作成できる既存のデータベースを参照する必要があります。  
  
    ```  
    CREATE TABLE ApplicationProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE UserProperties (PropertyName nvarchar(256),  
        PropertyValue nvarchar(256))  
    CREATE TABLE Roles (UserName nvarchar(256),   
        RoleName nvarchar(256))  
    CREATE TABLE Settings (PropertyName nvarchar(256),   
        PropertyStoredAs nvarchar(1), PropertyValue nvarchar(2048))  
    ```  
  
## <a name="using-custom-providers"></a>カスタム プロバイダーの使用  
 既定では、クライアント アプリケーション サービスの機能は、<xref:System.Web.ClientServices.Providers?displayProperty=nameWithType> 名前空間のプロバイダーを使用します。 **プロジェクト デザイナー**の **[サービス]** ページを使用してアプリケーションを構成すると、これらのプロバイダーへの参照が App.config ファイルに追加されます。 これらの既定のプロバイダーは、サーバー上の対応するプロバイダーにアクセスします。 Web サービスは、多くの場合、<xref:System.Web.Security.SqlMembershipProvider> や <xref:System.Web.Security.SqlRoleProvider> などのプロバイダーからユーザー データにアクセスするように構成されます。  
  
 カスタム サービス プロバイダーを使用する場合は、通常、サーバーにアクセスするすべてのクライアント アプリケーションに影響を与えるようにサーバー側のプロバイダーを変更します。 ただし、クライアント側で既定以外のプロバイダーを使用することもできます。 次の手順に示すように、プロジェクトの App.config ファイルでカスタム認証またはロール プロバイダーを指定できます。 カスタム認証とロール プロバイダーを作成する方法については、「[メンバーシップ プロバイダーを実装する](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)」と「[ロール プロバイダーを実装する](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)」を参照してください。 また、カスタム設定プロバイダーを使用するには、プロジェクトの `Settings` クラス (C# では `Properties.Settings.Default` として、Visual Basic では `My.Settings` としてアクセス) を変更します。 詳細については、「[アプリケーション設定アーキテクチャ](../../../docs/framework/winforms/advanced/application-settings-architecture.md)」を参照してください。  
  
#### <a name="to-configure-client-application-services-to-use-non-default-providers"></a>既定以外のプロバイダーを使用するようにクライアント アプリケーション サービスを構成するには  
  
1.  既定以外の認証またはロール サービス プロバイダーを使用するには、最初に、**[サービス]** ページを使用して、他のすべての構成設定を完了します。  
  
2.  **プロジェクト デザイナー**を閉じます。 これは、**[サービス]** ページが、設定を変更しない場合でも自動的に App.config ファイルを更新するため、必要となります。 この手順で説明するように、App.config ファイルを手動で変更し、**[サービス]** ページに戻ると、変更内容はリセットされます。  
  
3.  **ソリューション エクスプローラー**で、App.config をダブルクリックします。  
  
     アプリケーションの構成ファイルがテキスト エディターで開きます。  
  
4.  `<providers>` または `<membership>` 要素内の `<roleManager>` 要素を見つけます。 これらの要素は `<system.web>` 要素の子要素です。 `<membership>` 要素を使用して認証プロバイダーを指定し、`<roleManager>` 要素を使用してロール プロバイダーを指定します。  
  
5.  `<add>` 要素の子要素として `<providers>` 要素を追加します。 次の例に示すように、`name` および `type` 属性を指定する必要があります。 `type` 属性値はアセンブリ修飾型の名前である必要があります。 詳細については、「<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>」および「[アセンブリ名](../../../docs/framework/app-domains/assembly-names.md)」を参照してください。  
  
    ```xml  
    <add name="MyCustomRoleProvider" type="MyNamespace.MyRoleProvider, MyAssembly" />  
    ```  
  
6.  `defaultProvider` または `<membership>` 要素の `<roleManager>` 属性を変更して、前の手順で追加した `<add>` 要素から名前の値を指定します。  
  
    ```xml  
    <roleManager enabled="true" defaultProvider="MyCustomRoleProvider">  
    ```  
  
## <a name="see-also"></a>参照  
 [クライアント アプリケーション サービス](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [[サービス] ページ (プロジェクト デザイナー)](https://msdn.microsoft.com/library/bb398109)  
 [[サービスの詳細設定] ダイアログ ボックス](/visualstudio/ide/reference/advanced-settings-for-services-dialog-box)  
 [方法: クライアント アプリケーション サービスでユーザーのログインを実装する](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 [チュートリアル : クライアント アプリケーション サービスの使用](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [メンバシップ プロバイダの実装](http://msdn.microsoft.com/library/d8658b8e-c962-4f64-95e1-4acce35e4582)  
 [ロール プロバイダの実装](http://msdn.microsoft.com/library/851671ce-bf9b-43f2-aba4-bc9d28b11c7d)  
 [アプリケーション設定アーキテクチャ](../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [SQL Server 向けアプリケーション サービス データベースの作成と構成](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)
