---
title: 'チュートリアル : クライアント アプリケーション サービスの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application services host [client application services]
- client application services, walkthroughs
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
ms.openlocfilehash: 9193dc56a0f92daf486d95666ba820cb09d588d0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="walkthrough-using-client-application-services"></a>チュートリアル : クライアント アプリケーション サービスの使用
このトピックでは、ユーザーを認証し、ユーザーのロールと設定を取得するクライアント アプリケーション サービスを使用する Windows アプリケーションを作成する方法について説明します。  
  
 このチュートリアルでは次のタスクを実行します。  
  
-   Windows フォーム アプリケーションを作成し、Visual Studio プロジェクト デザイナーを使用してクライアント アプリケーション サービスの有効化および構成を行います。  
  
-   アプリケーション サービスのホストと、クライアント構成のテストを行う、簡単な ASP.NET Web サービス アプリケーションを作成します。  
  
-   フォーム認証をアプリケーションに追加します。 最初に、ハード コーディングされたユーザー名とパスワードを使用して、サービスをテストします。 次に、アプリケーション構成でログイン フォームを資格情報プロバイダーとして指定して、ログイン フォームを追加します。  
  
-   "manager” ロールのユーザーのみに対してボタンを有効にして表示し、ロール ベースの機能を追加します。  
  
-   Web 設定にアクセスします。 最初に、プロジェクト デザイナーの **[設定]** ページで認証済みの (テスト) ユーザーの Web 設定を読み込みます。 次に、Windows フォーム デザイナーを使用して、テキスト ボックスを Web 設定にバインドします。 最後に、変更済みの値をサーバーに保存し直します。  
  
-   ログアウトを実装します。 フォームにログアウト オプションを追加して、logout メソッドを呼び出します。  
  
-   オフライン モードを有効にします。 ユーザーが接続状態を指定できるように、チェック ボックスを用意します。 次に、この値を使用して、クライアント アプリケーション サービス プロバイダーが Web サービスにアクセスするのではなく、ローカルにキャッシュされたデータを使用するかどうかを指定します。 最後に、アプリケーションがオンライン モードに戻るときに、現在のユーザーを再認証します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)]。  
  
## <a name="creating-the-client-application"></a>クライアント アプリケーションの作成  
 最初に、Windows フォーム プロジェクトを作成します。 このチュートリアルでは Windows フォームを使用します。これはより多くの人が使い慣れているためです。しかし、プロセスは Windows Presentation Foundation (WPF) プロジェクトと類似しています。  
  
#### <a name="to-create-a-client-application-and-enable-client-application-services"></a>クライアント アプリケーションを作成し、クライアント アプリケーション サービスを有効にするには  
  
1.  Visual Studio で、**[ファイル] &#124; [新規作成] &#124; [プロジェクト]** メニュー オプションを選択します。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Visual Basic]** または **[Visual C#]** ノードを展開し、プロジェクトの種類 **[Windows]** をクリックします。  
  
3.  **[.NET Framework 3.5]** が選択されていることを確認してから、 **[Windows フォーム アプリケーション]** テンプレートをクリックします。  
  
4.  プロジェクトの **[名前]** を `ClientAppServicesDemo`に変更してから、 **[OK]** をクリックします。  
  
     Visual Studio に新しい Windows フォーム プロジェクトが開きます。  
  
5.  **[プロジェクト]** メニューで、 **ClientAppServicesDemo**プロパティを選択します。  
  
     プロジェクト デザイナーが表示されます。  
  
6.  **[サービス]** タブで、 **[クライアント アプリケーション サービスを有効にする]** をクリックします。  
  
7.  **[フォーム認証]** が選択されていることを確認してから、 **[認証サービスの場所]**、 **[ロール サービスの場所]**、および **[Web 設定サービスの場所]** を `http://localhost:55555/AppServices`に設定します。  
  
8.  Visual Basic では、**[アプリケーション]** タブで、**[認証モード]** を **[アプリケーション定義]** に設定します。  
  
 デザイナーは、アプリケーションの app.config ファイルに指定された設定を格納します。  
  
 この時点で、アプリケーションは、同じホストの 3 つのすべてのサービスにアクセスするように構成されます。 次のセクションでは、簡単な Web サービス アプリケーションとしてホストを作成し、クライアントの構成をテストできるようにします。  
  
## <a name="creating-the-application-services-host"></a>アプリケーションのサービス ホストを作成する  
 このセクションでは、ローカルの SQL Server Compact データベース ファイルのユーザー データにアクセスする簡単な Web サービス アプリケーションを作成します。 次に、 [ASP.NET Web Site Administration Tool](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)を使用してデータベースにデータを入力します。 この簡単な構成では、クライアント アプリケーションを短時間でテストすることができます。 あるいは、Web サービス ホストを構成して、完全な SQL Server データベースから、またはユーザー設定の <xref:System.Web.Security.MembershipProvider> クラスと <xref:System.Web.Security.RoleProvider> クラスを介してユーザー データにアクセスすることもできます。 詳細については、「 [Creating and Configuring the Application Services Database for SQL Server](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)」を参照してください。  
  
 次の手順では、AppServices の Web サービスを作成および構成します。  
  
#### <a name="to-create-and-configure-the-application-services-host"></a>アプリケーション サービス ホストを作成および構成するには  
  
1.  **[ソリューション エクスプローラー]** で、ClientAppServicesDemo ソリューションを選択してから、**[ファイル]** メニューで **[追加] &#124; [新しいプロジェクト]** の順にクリックします。  
  
2.  **[新しいプロジェクトの追加]** ダイアログ ボックスの **[プロジェクトの種類]** ペインで、**[Visual Basic]** または **[Visual C#]** ノードを展開し、プロジェクトの種類 **[Web]** をクリックします。  
  
3.  **[.NET Framework 3.5]** が選択されていることを確認してから、 **[ASP.NET サービス アプリケーション]** テンプレートをクリックします。  
  
4.  プロジェクトの **[名前]** を `AppServices` に変更してから、 **[OK]** をクリックします。  
  
     新しい ASP.NET Web サービス アプリケーション プロジェクトがソリューションに追加され、Service1.asmx.vb または Service1.asmx.cs ファイルがエディターに表示されます。  
  
    > [!NOTE]
    >  この例では、Service1.asmx.vb または Service1.asmx.cs ファイルは使用しません。 作業環境をきちんと整頓したい場合は、このファイルを閉じて **[ソリューション エクスプローラー]** から削除してください。  
  
5.  **[ソリューション エクスプローラー]** で、AppServices プロジェクトを選択し、 **[プロジェクト]** メニューで **[AppServices のプロパティ]** をクリックします。  
  
     プロジェクト デザイナーが表示されます。  
  
6.  **[Web]** タブで、 **[Visual Studio 開発サーバーを使用する]** が選択されていることを確認します。  
  
7.  **[特定のポート]** をクリックし、値に `55555`を指定してから、 **[仮想パス]** を `/AppServices`に設定します。  
  
8.  すべてのファイルを保存します。  
  
9. **[ソリューション エクスプローラー]** で、Web.config を開き、 `<system.web>` の開始タグを検索します。  
  
10. `<system.web>` タグの前に次のマークアップを追加します。  
  
     このマークアップの `authenticationService`、 `profileService`、および `roleService` の各要素で、アプリケーション サービスの有効化と構成を行います。 テスト目的で、 `requireSSL` 要素の `authenticationService` 属性が "false" に設定されています。 `readAccessProperties` 要素の `writeAccessProperties` 属性と `profileService` 属性は、 `WebSettingsTestText` プロパティが読み取りと書き込みが可能であることを示しています。  
  
    > [!NOTE]
    >  実稼働コードでは、HTTPS プロトコルを使用して、常に Secure Socket Layer (SSL) 上の認証サービスにアクセスする必要があります。 SSL の設定方法については、「 [SSL (Secure Sockets Layer) を構成する](http://go.microsoft.com/fwlink/?LinkId=91844)」を参照してください。  
  
    ```xml  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. 次のマークアップを、 `<system.web>` 要素内に収まるように、 `<system.web>` の開始タグの後に追加します。  
  
     `profile` 要素は、 `WebSettingsTestText`という名前の 1 つの Web 設定を構成します。  
  
    ```xml  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
    ```  
  
 次の手順では、ASP.NET Web サイト管理ツールを使用して、サービスの構成を完了するとともに、ローカル データベース ファイルにデータを読み込みます。 同じ名前の 2 つのロールに属する、 `employee` と `manager` という名前の 2 人のユーザーを追加します。 ユーザーのパスワードはそれぞれ、 `employee!` と `manager!` です。  
  
#### <a name="to-configure-membership-and-roles"></a>メンバーシップとロールを構成するには  
  
1.  **[ソリューション エクスプローラー]** で、AppServices プロジェクトを選択し、 **[プロジェクト]** メニューで **[ASP.NET の構成]** をクリックします。  
  
     **ASP.NET Web サイト管理ツール** が表示されます。  
  
2.  **[セキュリティ]** タブで、 **[セキュリティ設定ウィザードを使用して手順に従ってセキュリティを構成する]** をクリックします。  
  
     **[セキュリティ セットアップ ウィザード]** が表示され、 **[ようこそ]** 手順が表示されます。  
  
3.  **[次へ]** をクリックします。  
  
     **[アクセス方法の選択]** 手順が表示されます。  
  
4.  **[インターネットから]** を選択します。 そうすることで、Windows 認証ではなくフォーム認証を使用するようサービスが構成されます。  
  
5.  **[次へ]** を 2 回クリックします。  
  
     **[ロールの定義]** 手順が表示されます。  
  
6.  **[この Web サイトのロールを有効化]** をクリックします。  
  
7.  **[次へ]** をクリックします。 **[新しいロールの作成]** フォームが表示されます。  
  
8.  **[新しいロール名]** テキスト ボックスで、「 `manager` 」と入力してから、 **[ロールの追加]** をクリックします。  
  
     指定した値が入った **[既存のロール]** テーブルが表示されます。  
  
9. **[新しいロール名]** テキスト ボックスで、 `manager` を `employee` に置き換えてから、 **[ロールの追加]** をクリックします。  
  
     **[既存のロール]** テーブルに新しい値が表示されます。  
  
10. **[次へ]** をクリックします。  
  
     **[新しいユーザーの追加]** 手順が表示されます。  
  
11. **[ユーザーの作成]** フォームで、次の値を指定します。  
  
  	|||  
  	|-|-|  
  	|**ユーザー名**|`manager`|  
  	|**パスワード**|`manager!`|  
  	|**パスワードの確認入力**|`manager!`|  
  	|**電子メール**|`manager@contoso.com`|  
  	|**セキュリティの質問**|`manager`|  
  	|**セキュリティ返答**|`manager`|  
  
12. **[ユーザーの作成]** をクリックします。  
  
     成功のメッセージが表示されます。  
  
    > [!NOTE]
    >  フォームでは **[電子メール]**、**[秘密の質問]**、**[秘密の答え]** の値が必要ですが、この例では使用しません。  
  
13. **[続行]** をクリックします。  
  
     **[ユーザーの作成]** フォームが再表示されます。  
  
14. **[ユーザーの作成]** フォームで、次の値を指定します。  
  
  	|||  
  	|-|-|  
  	|**ユーザー名**|`employee`|  
  	|**パスワード**|`employee!`|  
  	|**パスワードの確認入力**|`employee!`|  
  	|**電子メール**|`employee@contoso.com`|  
  	|**セキュリティの質問**|`Employee`|  
  	|**セキュリティ返答**|`employee`|  
  
15. **[ユーザーの作成]** をクリックします。  
  
     成功のメッセージが表示されます。  
  
16. **[完了]** をクリックします。  
  
     **Web サイト管理ツール** が再表示されます。  
  
17. **[管理者ユーザー]** をクリックします。  
  
     ユーザーの一覧が表示されます。  
  
18. **employee** ユーザーの **[ロールの編集]** をクリックしてから、 **employee** ロールをクリックします。  
  
19. **manager** ユーザーの **[ロールの編集]** をクリックしてから、 **manager** ロールをクリックします。  
  
20. **Web サイト管理ツール**をホストするブラウザのウィンドウを閉じます。  
  
21. 変更した Web.config ファイルを再度読み込むかどうかを尋ねるメッセージ ボックスが表示された場合は、 **[はい]** をクリックします。  
  
 これにより、Web サービスのセットアップが完了します。 この時点で、F5 キーを押すとクライアント アプリケーションを実行します。 **ASP.NET 開発サーバー** は、クライアント アプリケーションとともに自動的に起動します。 サーバーは、アプリケーションが終了しても引き続き実行しますが、アプリケーションを再起動するとサーバーも再起動します。 そうすることで、Web.config に対して行われたすべての変更を検出することができます。  
  
 サーバーを手動で停止するには、タスク バーの通知領域にある ASP.NET 開発サーバーのアイコンを右クリックしてから、 **[停止]** をクリックします。 これは、時折クリーン再起動を確実に行うために役立ちます。  
  
## <a name="adding-forms-authentication"></a>フォーム認証を追加する  
 次の手順では、ユーザーの検証を試みるとともに、ユーザーが無効な資格情報を指定した場合にアクセスを拒否するコードをメイン フォームに追加します。 ハードコーディングされたユーザー名とパスワードを使用して、サービスをテストします。  
  
#### <a name="to-validate-the-user-in-your-application-code"></a>アプリケーション コードでユーザーを検証するには  
  
1.  **[ソリューション エクスプローラー]** の ClientAppServicesDemo プロジェクトで、System.Web アセンブリへの参照を追加します。  
  
2.  Form1 ファイルを選択し、Visual Studio のメイン メニューから **[表示] &#124; [コード]** を選択します。  
  
3.  コード エディターで、Form1 ファイルの先頭に次のステートメントを追加します。  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  **[ソリューション エクスプローラー]** で、Form1 をダブルクリックしてデザイナーを表示します。  
  
5.  デザイナーで、フォーム領域をダブルクリックして、 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> という名前の `Form1_Load`イベント ハンドラーを生成します。  
  
     `Form1_Load` メソッドにカーソルがある状態でコード エディターが表示されます。  
  
6.  `Form1_Load` メソッドに次のコードを追加します。  
  
     このコードは認証されていないユーザー アクセスを拒否してアプリケーションを終了します。 あるいは、認証されていないユーザーによるフォームへのアクセスを許可するものの、特定の機能へのアクセスを拒否することもできます。 通常、このようにユーザー名とパスワードをハードコーディングすることはありませんが、テスト目的には役立ちます。 次のセクションではこのコードをより堅牢なコードに置き換えて、ログイン ダイアログ ボックスを表示する、例外処理を含んだものにします。  
  
     `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> メソッドが [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)]にあることに注意してください。 このメソッドは、構成済みの認証プロバイダーに作業を委任し、認証が成功した場合は `true` を返します。 アプリケーションに、クライアントの認証プロバイダーへの直接の参照は必要ありません。  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 ここで、F5 キーを押してアプリケーションを実行します。正しいユーザー名とパスワードを指定しているため、フォームが表示されます。  
  
> [!NOTE]
>  アプリケーションを実行できない場合は、ASP.NET 開発サーバーを停止してください。 サーバーを再起動する際、ポートが 55555 に設定されていることを確認します。  
  
 代わりにエラー メッセージを表示するには、 <xref:System.Web.Security.Membership.ValidateUser%2A> のパラメーターを変更します。 たとえば、2 番目の `"manager!"` パラメーターを `"MANAGER"`などの正しくないパスワードに置き換えます。  
  
## <a name="adding-a-login-form-as-a-credentials-provider"></a>資格情報プロバイダーとしてログイン フォームを追加する  
 アプリケーション コードでユーザーの資格情報を取得して、 <xref:System.Web.Security.Membership.ValidateUser%2A> メソッドに渡すことができます。 しかし、資格情報を取得するコードをアプリケーション コードと分けておくと、後でこれを変更するときに便利な場合もあります。  
  
 次の手順では、資格情報プロバイダーを使用するようにアプリケーションを構成してから、両方のパラメーターに <xref:System.Web.Security.Membership.ValidateUser%2A> を渡すように <xref:System.String.Empty> メソッドの呼び出しを変更します。 文字列が空の場合、 <xref:System.Web.Security.Membership.ValidateUser%2A> メソッドは構成済みの資格情報プロバイダーの <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> メソッドを呼び出します。  
  
#### <a name="to-configure-your-application-to-use-a-credentials-provider"></a>アプリケーションが資格情報プロバイダーを使用するように構成するには  
  
1.  **[ソリューション エクスプローラー]** で、ClientAppServicesDemo プロジェクトを選択し、 **[プロジェクト]** メニューで **[ClientAppServicesDemo のプロパティ]** をクリックします。  
  
     プロジェクト デザイナーが表示されます。  
  
2.  **[サービス]** タブで、 **[省略可能な資格情報プロバイダー]** を次の値に設定します。 この値は、アセンブリ修飾型名を示しています。  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  Form1 コード ファイルで、 `Form1_Load` メソッドのコードを次のコードに置き換えます。  
  
     このコードは、ようこそメッセージを表示してから、次の手順で追加する `ValidateUsingCredentialsProvider` メソッドを呼び出します。 ユーザーが認証されない場合、 `ValidateUsingCredentialsProvider` メソッドは `false` を返し、 `Form1_Load` メソッドが戻ります。 これにより、アプリケーションが終了するまでそれ以上コードを実行できなくなります。 ようこそメッセージは、アプリケーションが再起動するときが明確になるため便利です。 このチュートリアルの後半でログアウトを実装するときに、アプリケーションを再起動するコードを追加します。  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  `Form1_Load` メソッドの後に次のメソッドを追加します。  
  
     このメソッドは、 `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> メソッドに空の文字列を渡すことによって、[ログイン] ダイアログ ボックスを表示させます。 認証サービスが使用できない場合、 <xref:System.Web.Security.Membership.ValidateUser%2A> メソッドは <xref:System.Net.WebException>をスローします。 この場合、 `ValidateUsingCredentialsProvider` メソッドは警告メッセージを表示し、オフライン モードで再試行するかどうかをユーザーに尋ねます。 この機能には、「 **How to: Configure Client Application Services** 」で説明する [[オフラインでログインできるようにパスワードのハッシュをローカルに保存する]](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)機能が必要です。 この機能は、新しいプロジェクトでは既定で有効になっています。  
  
     ユーザーが検証されない場合、 `ValidateUsingCredentialsProvider` メソッドはエラー メッセージを表示し、アプリケーションを終了します。 最後に、このメソッドは、認証の結果を返します。  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### <a name="creating-a-login-form"></a>ログイン フォームを作成する  
 資格情報プロバイダーとは、 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装するクラスです。 このインターフェイスには、 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> オブジェクトを返す <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> という名前の 1 つのメソッドがあります。 次の手順ではログイン ダイアログ ボックスの作成方法を示します。これは <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> を実装してダイアログ ボックスを表示し、ユーザー指定の資格情報を返します。  
  
 Visual Basic は **[ログイン フォーム]** テンプレートを備えているため、Visual Basic と C# で手順が別々に説明されています。 このテンプレートを使用すると、時間の節約になり、コーディングの手間も省けます。  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-visual-basic"></a>Visual Basic で資格情報プロバイダーとしてログイン ダイアログ ボックスを作成するには  
  
1.  **[ソリューション エクスプローラー]** で、ClientAppServicesDemo プロジェクトを選択してから、 **[プロジェクト]** メニューで **[新しい項目の追加]** をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[ログイン フォーム]** テンプレートを選択し、項目の **[名前]** を `Login.vb`に変更してから、 **[追加]** をクリックします。  
  
     Windows フォーム デザイナーにログイン ダイアログ ボックスが表示されます。  
  
3.  デザイナーで、 **[OK]** ボタンをクリックし、 **[プロパティ]** ウィンドウで、[ `DialogResult` ] を ” `OK`" に設定します。  
  
4.  デザイナーで、 `CheckBox` コントロールを、 **[パスワード]** テキスト ボックスの下にあるフォームに追加します。  
  
5.  **[プロパティ]** ウィンドウで、**[(名前)]** の値を "`rememberMeCheckBox`" と指定し、**[テキスト]** の値を "`&Remember me`" と指定します。  
  
6.  Visual Studio のメイン メニューで、**[表示] &#124; [コード]** の順に選択します。  
  
7.  コード エディターで、ファイルの先頭に次のコードを追加します。  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  クラスが <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> インターフェイスを実装するようにクラスのシグネチャを変更します。  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. カーソルが `IClientformsAuthenticationCredentialsProvider`の後にあることを確認してから、Enter キーを押して `GetCredentials` メソッドを生成します。  
  
10. <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> の実装を見つけて、次のコードに置き換えます。  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 次の C# の手順では、簡単なログイン ダイアログ ボックス用のコード全体を一覧で示します。 このダイアログ ボックスのレイアウトは少し粗雑ですが、重要な部分は <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> の実装です。  
  
##### <a name="to-create-a-login-dialog-box-as-a-credentials-provider-in-c"></a>C# で資格情報プロバイダーとしてログイン ダイアログ ボックスを作成するには  
  
1.  **[ソリューション エクスプローラー]** で、ClientAppServicesDemo プロジェクトを選択してから、 **[プロジェクト]** メニューで **[クラスの追加]** をクリックします。  
  
2.  **[新しい項目の追加]** ダイアログ ボックスで、 **[名前]** を `Login.cs`に変更してから、 **[追加]** をクリックします。  
  
     コード エディターで Login.cs ファイルが開きます。  
  
3.  既定のコードを次のコードに置き換えます。  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 アプリケーションを実行してログイン ダイアログ ボックスを表示できるようになりました。 このコードをテストするには、有効と無効の両方のさまざまな資格情報を試し、資格情報が有効な場合にのみフォームにアクセスできることを確認します。 有効なユーザー名は、 `employee` と `manager` になります。パスワードはそれぞれ、 `employee!` と `manager!` です。  
  
> [!NOTE]
>  この時点で **[アカウントを記憶]** は選択しないでください。そうしないと、このチュートリアルの後半でログアウトを実装するまで、別のユーザーとしてログインできなくなります。  
  
## <a name="adding-role-based-functionality"></a>ロール ベースの機能を追加する  
 次の手順では、フォームにボタンを追加して、manager ロールのユーザーにだけこれを表示します。  
  
#### <a name="to-change-the-user-interface-based-on-user-role"></a>ユーザーのロールに基づいてユーザー インターフェイスを変更するには  
  
1.  **[ソリューション エクスプローラー]** の ClientAppServicesDemo プロジェクトで、Form1 を選択してから、Visual Studio のメイン メニューで **[表示] &#124; [デザイナー]** を選択します。  
  
2.  デザイナーで、**[ツールボックス]** からフォームに <xref:System.Windows.Forms.Button> コントロールを追加します。  
  
3.  **[プロパティ]** ウィンドウで、ボタンの次のプロパティを設定します。  
  
  	|プロパティ|[値]|  
  	|--------------|-----------|  
  	|**[(名前)]**|managerOnlyButton|  
  	|**[テキスト]**|&Manager task|  
  	|**Visible**|`False`|  
  
4.  Form1 のコード エディターで、 `Form1_Load` メソッドの末尾に次のコードを追加します。  
  
     このコードは、次の手順で追加する `DisplayButtonForManagerRole` メソッドを呼び出します。  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  次のメソッドを Form1 クラスの末尾に追加します。  
  
     このメソッドは、`static` <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティによって返される <xref:System.Security.Principal.IPrincipal> の <xref:System.Security.Principal.IPrincipal.IsInRole%2A> メソッドを呼び出します。 クライアント アプリケーション サービスを使用するように構成されたアプリケーションで、このプロパティは <xref:System.Web.ClientServices.ClientRolePrincipal> を返します。 このクラスは <xref:System.Security.Principal.IPrincipal> インターフェイスを実装しているため、明示的に参照する必要はありません。  
  
     ユーザーが "manager" ロールの場合、 `DisplayButtonForManagerRole` メソッドは <xref:System.Windows.Forms.Control.Visible%2A> の `managerOnlyButton` プロパティを `true`に設定します。 また、このメソッドは、 <xref:System.Net.WebException> がスローされるとエラー メッセージを表示します。これは、ロール サービスが使用できないことを示します。  
  
    > [!NOTE]
    >  ユーザー ログインの有効期限が切れている場合、 <xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> メソッドは常に `false` を返します。 このチュートリアルのコードの使用例に示すように、アプリケーションが認証のすぐ後に <xref:System.Security.Principal.IPrincipal.IsInRole%2A> メソッドを 1 回呼び出した場合、これは発生しません。 アプリケーションが他のタイミングでユーザーのロールを取得する必要がある場合は、ログインの有効期限が切れたユーザーを再検証するコードを追加することができます。 有効なユーザーすべてにロールが割り当てられている場合は、 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=nameWithType> メソッドを呼び出してログインの有効期限が切れていないか判断できます。 ロールが返されない場合は、ログインの有効期限が切れています。 この機能の例については、 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> メソッドを参照してください。 この機能が必要なのは、アプリケーションの構成で **[サーバー クッキーの期限が切れた場合は常に再度ログオンすることをユーザーに要求する]** を選択した場合だけです。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 認証が成功した場合に、クライアント認証プロバイダーは <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティを <xref:System.Web.ClientServices.ClientRolePrincipal> クラスのインスタンスに設定します。 このクラスは、構成済みのロール プロバイダーに作業を委任するよう、 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> メソッドを実装します。 上記と同様、アプリケーションのコードにサービス プロバイダーへの直接の参照は必要ありません。  
  
 ここでアプリケーションを実行し、従業員としてログインして、ボタンが表示されないことを確認できます。次いで、管理者としてログインして、ボタンが表示されることを確認します。  
  
## <a name="accessing-web-settings"></a>Web 設定にアクセスする  
 次の手順では、フォームにテキスト ボックスを追加するとともに、Web 設定にバインドします。 認証とロールを使用する前のコードと同様、設定コードは設定プロバイダーに直接アクセスしません。 代わりに、Visual Studio がプロジェクト用に生成する、厳密に型指定された `Settings` クラスを使用します (C# では `Properties.Settings.Default` として、Visual Basic では `My.Settings` としてアクセスします)。  
  
#### <a name="to-use-web-settings-in-your-user-interface"></a>ユーザー インターフェイスで Web 設定を使用するには  
  
1.  タスクバーの通知領域をチェックして、 **ASP.NET Web 開発サーバー** がまだ実行中であることを確認します。 サーバーが停止している場合は、アプリケーションを再起動して (これによりサーバーが自動的に起動します)、その後、ログイン ダイアログ ボックスを閉じます。  
  
2.  **[ソリューション エクスプローラー]** で、ClientAppServicesDemo プロジェクトを選択し、 **[プロジェクト]** メニューで **[ClientAppServicesDemo のプロパティ]** をクリックします。  
  
     プロジェクト デザイナーが表示されます。  
  
3.  **[設定]** タブで、 **[Web 設定の読み込み]** をクリックします。  
  
     **[ログイン]** ダイアログ ボックスが表示されます。  
  
4.  従業員またはマネージャーの資格情報を入力してから、 **[ログイン]** をクリックします。 使用する Web 設定は認証されたユーザーのみがアクセスできるように構成されているため、 **[ログインのスキップ]** をクリックすると設定は読み込まれません。  
  
     `WebSettingsTestText` の設定が、既定値の `DefaultText`でデザイナーに表示されます。 さらに、`WebSettingsTestText` プロパティを含む `Settings` クラスがプロジェクトに生成されます。  
  
5.  **[ソリューション エクスプローラー]** の ClientAppServicesDemo プロジェクトで、Form1 を選択してから、Visual Studio のメイン メニューで **[表示] &#124; [デザイナー]** を選択します。  
  
6.  デザイナーで、フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。  
  
7.  **[プロパティ]** ウィンドウで、 **[(名前)]** の値を " `webSettingsTestTextBox`" と指定します。  
  
8.  コード エディターで、 `Form1_Load` メソッドの末尾に次のコードを追加します。  
  
     このコードは、次の手順で追加する `BindWebSettingsTestTextBox` メソッドを呼び出します。  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. 次のメソッドを Form1 クラスの末尾に追加します。  
  
     このメソッドは、 <xref:System.Windows.Forms.TextBox.Text%2A> の `webSettingsTestTextBox` プロパティを、この手順の前半で生成した `WebSettingsTestText` クラスの `Settings` プロパティにバインドします。 また、このメソッドは、 <xref:System.Net.WebException> がスローされるとエラー メッセージを表示します。これは、Web 設定サービスが使用できないことを示します。  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  通常は、データ バインドを使用して、コントロールと Web 設定間の自動双方向通信を有効にします。 しかし、次の例に示すとおり、直接 Web 設定にアクセスすることもできます。  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. デザイナーで、フォームを選択してから、 **[プロパティ]** ウィンドウの **[イベント]** ボタンをクリックします。  
  
11. <xref:System.Windows.Forms.Form.FormClosing> イベントをクリックしてから、Enter キーを押すとイベント ハンドラーが生成されます。  
  
12. 生成されたメソッドを次のコードで置き換えます。  
  
     <xref:System.Windows.Forms.Form.FormClosing> イベント ハンドラーが `SaveSettings` メソッドを呼び出します。このメソッドは、次のセクションで追加するログアウト機能でも使用されます。 まず、 `SaveSettings` メソッドは、ユーザーがログアウトしていないことを確認します。これは、現在のプリンシパルによって返される <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> の <xref:System.Security.Principal.IIdentity> プロパティをチェックして行います。 現在のプリンシパルは `static` <xref:System.Threading.Thread.CurrentPrincipal%2A> プロパティを介して取得します。 ユーザーがクライアント アプリケーション サービスで認証済みであれば、認証の種類は "ClientForms" になります。 `SaveSettings` メソッドは、単に <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=nameWithType> プロパティをチェックすることはできません。これは、ユーザーがログアウト後に有効な Windows ID を持っていることがあるためです。  
  
     ユーザーがログアウトしていない場合、 `SaveSettings` メソッドは、この手順の前半で生成された <xref:System.Configuration.ApplicationSettingsBase.Save%2A> クラスの `Settings` メソッドを呼び出します。 認証クッキーの有効期限が切れている場合、このメソッドは <xref:System.Net.WebException> をスローすることがあります。 これが発生するのは、アプリケーションの構成で **[サーバー クッキーの期限が切れた場合は常に再度ログオンすることをユーザーに要求する]** を選択した場合だけです。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。 `SaveSettings` メソッドは、 <xref:System.Web.Security.Membership.ValidateUser%2A> を呼び出してログイン ダイアログ ボックスを表示することで、クッキーの有効期限を処理します。 ユーザーが正常にログインすると、 `SaveSettings` メソッドは自身を呼び出して設定を再度保存しようとします。  
  
     前のコードと同様、リモート サービスが使用できない場合、 `SaveSettings` メソッドはエラー メッセージを表示します。 設定プロバイダーがリモート サービスにアクセスできない場合、設定はローカル キャッシュに保存されたままとなり、アプリケーションの再起動時に再度読み込まれます。  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. 次のメソッドを Form1 クラスの末尾に追加します。  
  
     このコードは <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=nameWithType> イベントを処理し、設定のいずれかが保存できなかった場合は警告を表示します。 設定サービスが使用できない場合、または認証クッキーの有効期限が切れている場合、 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> イベントは発生しません。 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> イベントが発生する 1 つの例は、ユーザーが既にログアウトしている場合です。このイベント ハンドラーは、 `SaveSettings` メソッドの呼び出しの直前にある <xref:System.Configuration.ApplicationSettingsBase.Save%2A> メソッドにログアウトのコードを追加することでテストできます。 使用できるログアウトのコードは、次のセクションで説明します。  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. C# では、 `Form1_Load` メソッドの末尾に次のコードを追加します。 このコードは、最後の手順で追加したメソッドと <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> イベントを関連付けます。  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 この時点でアプリケーションをテストするため、従業員として、およびマネージャーとして複数回これを実行し、テキスト ボックスに異なる値を入力します。 値は、ユーザーごとにセッションをまたいで保持されます。  
  
## <a name="implementing-logout"></a>ログアウトを実装する  
 ユーザーがログイン時に **[アカウントを記憶]** チェック ボックスをオンにすると、アプリケーションは以降の実行時に自動的にユーザーを認証します。 自動認証は、アプリケーションがオフライン モードの場合、または認証クッキーの有効期限が切れるまで継続します。 ただし、場合によっては、複数のユーザーがアプリケーションにアクセスしなければならなくなることや、1 人のユーザーが別の資格情報でログインすることもあります。 このシナリオを有効にするには、次の手順に説明するログアウト機能を実装する必要があります。  
  
#### <a name="to-implement-logout-functionality"></a>ログアウト機能を実装するには  
  
1.  Form1 デザイナーで、**[ツールボックス]** から <xref:System.Windows.Forms.Button> コントロールをフォームに追加します。  
  
2.  **[プロパティ]** ウィンドウで、**[(名前)]** の値を "`logoutButton`" と指定し、**[テキスト]** の値を "**&Log Out**" と指定します。  
  
3.  `logoutButton` をダブルクリックすると、<xref:System.Windows.Forms.Control.Click> イベント ハンドラーが生成されます。  
  
     `logoutButton_Click` メソッドにカーソルがある状態でコード エディターが表示されます。  
  
4.  生成された `logoutButton_Click` メソッドを次のコードで置き換えます。  
  
     まず、このイベント ハンドラーは、前のセクションで追加した `SaveSettings` メソッドを呼び出します。 次に、イベント ハンドラーは <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=nameWithType> メソッドを呼び出します。 認証サービスが使用できない場合、 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> メソッドは <xref:System.Net.WebException>をスローします。 この場合、 `logoutButton_Click` メソッドは警告メッセージを表示し、一時的にオフライン モードに切り替えてユーザーをログアウトします。オフライン モードについては、次のセクションで説明します。  
  
     ログアウトすると、アプリケーションの再起動時にログインが必要になるように、ローカルの認証クッキーが削除されます。 ログアウト後、イベント ハンドラーは、アプリケーションを再起動します。 アプリケーションは、再起動すると、ようこそメッセージに続いてログイン ダイアログ ボックスを表示します。 ようこそメッセージにより、アプリケーションが再起動したことが明確になります。 こうすることで、ユーザーが設定の保存のためのログインに続いて、アプリケーションの再起動に伴うログインを再度行わなければならない場合に、起こりうる混乱を避けられます。  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 ログアウト機能をテストするには、アプリケーションを実行し、[ログイン] ダイアログ ボックスで **[アカウントを記憶]** をクリックします。 次に、ログインする必要がなくなることを確認するため、アプリケーションを閉じて再起動します。 最後に、[Log out] をクリックして、アプリケーションを再起動します。  
  
## <a name="enabling-offline-mode"></a>オフライン モードを有効にする  
 次の手順では、ユーザーがオフライン モードに入れるようにするチェック ボックスをフォームに追加します。 `static` <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=nameWithType> プロパティを `true`に設定すると、アプリケーションはオフライン モードを示します。 オフラインの状態は、ローカルのハード ディスク上の、 <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> プロパティが示す場所に格納されます。 つまり、オフラインの状態は、ユーザーごと、アプリケーションごとに格納されます。  
  
 オフライン モードの場合、クライアント アプリケーション サービス要求はどれも、サービスへのアクセスを試みることなく、ローカル キャッシュからデータを取得します。 既定の構成では、ローカル データには暗号化された形式のユーザーのパスワードが含まれています。 これにより、ユーザーは、アプリケーションがオフライン モードのときにログインできます。 詳細については、「 [How to: Configure Client Application Services](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)」を参照してください。  
  
#### <a name="to-enable-offline-mode-in-your-application"></a>アプリケーションでオフライン モードを有効にするには  
  
1.  **[ソリューション エクスプローラー]** の ClientAppServicesDemo プロジェクトで、Form1 を選択してから、Visual Studio のメイン メニューで **[表示] &#124; [デザイナー]** を選択します。  
  
2.  デザイナーで、フォームに <xref:System.Windows.Forms.CheckBox> コントロールを追加します。  
  
3.  **[プロパティ]** ウィンドウで、**[(名前)]** の値を "`workOfflineCheckBox`" と指定し、**[テキスト]** の値を "**&Work offline**" と指定します。  
  
4.  **[プロパティ]** ウィンドウで、 **[イベント]** ボタンをクリックします。  
  
5.  <xref:System.Windows.Forms.CheckBox.CheckedChanged> イベントをクリックしてから、Enter キーを押すとイベント ハンドラーが生成されます。  
  
6.  生成されたメソッドを次のコードで置き換えます。  
  
     このコードは、 <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> の値を更新し、オンライン モードに戻るときに、ダイアログを表示せずにユーザーを再検証します。 <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=nameWithType> メソッドでは、ユーザーが明示的にログインする必要がないように、キャッシュされた資格情報を使用します。 認証サービスが使用できない場合、警告メッセージが表示され、アプリケーションはオフラインのままになります。  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> メソッドは便宜的なものに過ぎません。 このメソッドには戻り値がないため、再検証が失敗したかどうかを示すことはできません。 再検証は失敗することがあります。たとえば、サーバーでユーザーの資格情報が変更された場合などです。 この場合、サービスの呼び出しが失敗した後に、明示的にユーザーを検証するコードを含めることができます。 詳細については、このチュートリアルの上述の「Web 設定にアクセスする」を参照してください。  
  
     再検証後、前に追加した `SaveSettings` メソッドを呼び出すことで、このコードはローカルの Web 設定への変更をすべて保存します。 続いて、プロジェクトの `Settings` クラスの <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> メソッドを呼び出して、新しい値をすべて取得します (C# では `Properties.Settings.Default` として、Visual Basic では `My.Settings` としてアクセスします)。  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  `Form1_Load` メソッドの末尾に次のコードを追加して、チェック ボックスが現在の接続状態を示すようにします。  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 これで、サンプル アプリケーションが完成しました。 オフライン機能をテストするには、アプリケーションを実行し、従業員またはマネージャーとしてログインしてから、 **[Work offline]** をクリックします。 テキスト ボックスの値を変更してから、アプリケーションを終了します。 アプリケーションを再起動します ログインする前に、タスク バーの通知領域にある ASP.NET 開発サーバーのアイコンを右クリックしてから、 **[停止]** をクリックします。 次に、通常どおりにログインします。 サーバーが実行されていない場合でもログインできます。 テキスト ボックスの値を変更してから、終了および再起動を行って、変更された値を確認します。  
  
## <a name="summary"></a>まとめ  
 このチュートリアルでは、Windows フォーム アプリケーションでのクライアント アプリケーション サービスの有効化および使用方法について学習しました。 テスト サーバーをセットアップした後、アプリケーションにコードを追加し、ユーザーを認証したり、サーバーからユーザーのロールとアプリケーションの設定を取得したりできるようにしました。 また、接続を使用できない場合に、アプリケーションがリモート サービスではなく、ローカル データ キャッシュを使用できるように、オフライン モードを有効にする方法についても学びました。  
  
## <a name="next-steps"></a>次の手順  
 実際のアプリケーションではリモート サーバーから多数のユーザーのデータを取得しますが、サーバーは常に使用可能であるとは限らず、予告なく停止する可能性もあります。 アプリケーションを堅牢にするため、サービスが利用できない場合に状況に適切に対応する必要があります。 このチュートリアルには、サービスが利用できない場合に <xref:System.Net.WebException> をキャッチしてエラー メッセージを表示する try ブロックと catch ブロックが含まれています。 実稼働コードでは、このケースに対処するため、オフライン モードに切り替えることや、アプリケーションを終了すること、特定の機能へのアクセスを拒否することができます。  
  
 アプリケーションのセキュリティを向上させるため、配置する前に必ずアプリケーションとサーバーを十分にテストしてください。  
  
## <a name="see-also"></a>参照  
 [クライアント アプリケーション サービス](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [クライアント アプリケーション サービスの概要](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [方法 : クライアント アプリケーション サービスを構成する](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [ASP.NET Web サイト管理ツール](http://msdn.microsoft.com/library/100ddd8b-7d11-4df9-91ef-0bbbe92e5aec)  
 [SQL Server 向けアプリケーション サービス データベースの作成と構成](http://msdn.microsoft.com/library/ab894e83-7e2f-4af8-a116-b1bff8f815b2)  
 [チュートリアル: ASP.NET アプリケーション サービスの使用](http://msdn.microsoft.com/library/f3f394f0-20d6-4361-aa8f-4b21bf4933eb)
