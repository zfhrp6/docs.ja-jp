---
title: アプリケーション設定アーキテクチャ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 769077ddbe42d4d774d359de75417bdca6bcaeb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520004"
---
# <a name="application-settings-architecture"></a>アプリケーション設定アーキテクチャ
このトピックでは、アプリケーション設定アーキテクチャのしくみについて説明します。また、グループ化された設定や設定キーなど、アーキテクチャの高度な機能についても説明します。  
  
 アプリケーション設定アーキテクチャでは、アプリケーション スコープまたはユーザー スコープで厳密に型指定された設定の定義と、アプリケーション セッション間での設定の永続化をサポートします。 このアーキテクチャは、ローカル ファイル システムに設定を保存し、ローカル ファイル システムから設定を読み込むための既定の永続化エンジンを提供します。 また、カスタム永続化エンジンを指定するためのインターフェイスも定義します。  
  
 アプリケーションでカスタム コンポーネントがホストされているときに、そのコンポーネントの独自の設定を永続化できるようにするインターフェイスが提供されます。 設定キーを使用することで、各コンポーネントはそのコンポーネントの複数のインスタンスの設定を区別できます。  
  
## <a name="defining-settings"></a>設定の定義  
 アプリケーション設定アーキテクチャは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 内と Windows フォーム内で使用されます。アーキテクチャには、この両方の環境で共有される多数の基本クラスが含まれます。 最も重要なは<xref:System.Configuration.SettingsBase>が、コレクションを使用した設定にアクセスできるように低レベルのメソッドを提供の読み込みと設定を保存します。 それぞれの環境から派生した独自のクラスを実装する<xref:System.Configuration.SettingsBase>その環境内の他の設定機能を提供します。 派生したクラスで Windows フォーム ベースのアプリケーションでは、すべてのアプリケーション設定を定義する必要があります、<xref:System.Configuration.ApplicationSettingsBase>クラスは、基本クラスに次の機能を追加します。  
  
-   上位レベルの読み込み操作と保存操作  
  
-   ユーザー スコープの設定のサポート  
  
-   ユーザーの設定を定義済みの既定値に戻す機能  
  
-   以前のバージョンのアプリケーションの設定のアップグレード  
  
-   設定の変更前または保存前の検証  
  
 設定の説明は、さまざまな内で定義されている属性を使用して、<xref:System.Configuration>名前空間については、[アプリケーション設定の属性](../../../../docs/framework/winforms/advanced/application-settings-attributes.md)です。 設定を定義するときは、いずれかで適用する必要があります<xref:System.Configuration.ApplicationScopedSettingAttribute>または<xref:System.Configuration.UserScopedSettingAttribute>、全体のアプリケーションまたは現在のユーザーにだけ設定を適用するかどうかを説明します。  
  
 次のコード例では、`BackgroundColor` という 1 つの設定を指定してカスタム設定クラスを定義しています。  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>設定の永続化  
 <xref:System.Configuration.ApplicationSettingsBase>クラス自体を永続化またはしていない設定を読み込む以外の場合は、このジョブはから派生したクラスの設定プロバイダーに<xref:System.Configuration.SettingsProvider>です。 場合の派生クラス<xref:System.Configuration.ApplicationSettingsBase>を通じて設定プロバイダーが指定されていません、 <xref:System.Configuration.SettingsProviderAttribute>、し、既定のプロバイダー<xref:System.Configuration.LocalFileSettingsProvider>を使用します。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] と共にリリースされた構成システムでは、ローカル コンピューターの machine.config ファイルまたはアプリケーションと共に配置される `app.`exe.config ファイルを使用した静的なアプリケーション構成データの提供をサポートしています。 <xref:System.Configuration.LocalFileSettingsProvider>クラスは、次の方法でこのネイティブ サポートを拡張します。  
  
-   アプリケーション スコープの設定は、machine.config ファイルまたは `app.`exe.config ファイルに保存できます。 machine.config は常に読み取り専用です。`app`.exe.config は、セキュリティを考慮して、ほとんどのアプリケーションで読み取り専用に制限されています。  
  
-   ユーザー スコープの設定は、`app`.exe.config ファイルに保存できます。この場合、設定は静的な既定値として扱われます。  
  
-   既定値以外のユーザー スコープの設定は、*user*.config という新しいファイルに保存されます。*user* は、アプリケーションを現在実行しているユーザーのユーザー名です。 ユーザー スコープ設定で、既定値を指定することができます<xref:System.Configuration.DefaultSettingValueAttribute>です。 ユーザー スコープの設定はアプリケーションの実行時に変更されることが多いため、`user`.config は常に読み取り/書き込みになります。  
  
 この 3 つの構成ファイルはいずれも XML 形式で設定を保存します。 アプリケーション スコープの設定の最上位の XML 要素は `<appSettings>` であり、ユーザー スコープの設定には `<userSettings>` が使用されます。 アプリケーション スコープの設定と、ユーザー スコープの設定の既定値が含まれた `app`.exe.config ファイルは、次のようになります。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
 構成ファイルのアプリケーション設定セクション内の要素の定義については、「[アプリケーション設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)」を参照してください。  
  
### <a name="settings-bindings"></a>設定のバインド  
 アプリケーション設定では、Windows フォーム データ バインド アーキテクチャを使用して、設定オブジェクトとコンポーネント間で設定の更新の双方向通信を行います。 Visual Studio を使用してアプリケーション設定を作成し、設定をコンポーネントのプロパティに割り当てると、これらのバインドが自動的に生成されます。  
  
 アプリケーションの設定をサポートするコンポーネントにしかバインド、<xref:System.Windows.Forms.IBindableComponent>インターフェイスです。 また、コンポーネントを特定のバインド プロパティの変更イベントを実装またはアプリケーションの設定を通じて、プロパティが変更されたことを通知する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスです。 コンポーネントを実装しない場合<xref:System.Windows.Forms.IBindableComponent>Visual Studio をバインドして、バインドされたプロパティは、最初に設定されますは更新されません。 コンポーネントを実装する場合<xref:System.Windows.Forms.IBindableComponent>が、変更通知をサポート プロパティではないが、設定ファイルには、プロパティが変更されたときに、バインディングは更新されません。  
  
 Windows フォームの一部のコンポーネントなど<xref:System.Windows.Forms.ToolStripItem>設定のバインディングをサポートしていません。  
  
### <a name="settings-serialization"></a>設定のシリアル化  
 ときに<xref:System.Configuration.LocalFileSettingsProvider>設定をディスクに保存する必要があります、次の操作を実行します。  
  
1.  リフレクションを使用して、すべてで定義されたプロパティを調べて、<xref:System.Configuration.ApplicationSettingsBase>いずれかに適用されるものを検索するクラスを派生<xref:System.Configuration.ApplicationScopedSettingAttribute>または<xref:System.Configuration.UserScopedSettingAttribute>です。  
  
2.  プロパティをディスクにシリアル化します。 呼び出すに初めて試みる、<xref:System.ComponentModel.TypeConverter.ConvertToString%2A>または<xref:System.ComponentModel.TypeConverter.ConvertFromString%2A>の種類の関連付けられた<xref:System.ComponentModel.TypeConverter>です。 この呼び出しが失敗すると、代わりに XML シリアル化を使用します。  
  
3.  設定の属性に基づいて、どの設定がどのファイルに指定されているかを判断します。  
  
 使用することができます独自設定クラスを実装する場合、<xref:System.Configuration.SettingsSerializeAsAttribute>バイナリまたはカスタムのシリアル化を使用するかの設定を示すために、<xref:System.Configuration.SettingsSerializeAs>列挙します。 コードで独自の設定クラスを作成する方法の詳細については、「[方法 : アプリケーション設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)」を参照してください。  
  
### <a name="settings-file-locations"></a>設定ファイルの場所  
 `app`.exe.config ファイルと *user*.config ファイルの場所は、アプリケーションのインストール方法によって異なります。 ローカル コンピューターにコピーする Windows フォーム ベースのアプリケーションの`app`..exe.config に変更がアプリケーションのメイン実行可能ファイルでは、基本ディレクトリと同じディレクトリに存在して*ユーザー*で .config が存在する、指定された位置、<xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType>プロパティです。 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] を使用してインストールされたアプリケーションの場合、どちらのファイルも %InstallRoot%\Documents and Settings\\*username*\Local Settings の下の [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] データ ディレクトリに配置されます。  
  
 ユーザーが移動プロファイルを有効にしている場合、これらのファイルの格納場所は若干異なります。移動プロファイルを使用すると、ユーザーはドメイン内の他のコンピューターを使用するときに Windows とアプリケーションの異なる設定を定義できます。 この場合、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションと [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 以外のアプリケーションのどちらについても、`app`.exe.config ファイルと *user*.config ファイルが %InstallRoot%\Documents and Settings\\*username*\Application Data に格納されます。  
  
 アプリケーション設定機能と新しい配置テクノロジの連携の詳細については、「[ClickOnce とアプリケーション設定](/visualstudio/deployment/clickonce-and-application-settings)」を参照してください。 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] データ ディレクトリの詳細については、「[ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)」を参照してください。  
  
## <a name="application-settings-and-security"></a>アプリケーション設定とセキュリティ  
 アプリケーション設定は部分信頼で機能するように設計されています。部分信頼は、インターネットまたはイントラネット上でホストされる Windows フォーム アプリケーションの既定の制限された環境です。 既定の設定プロバイダーでアプリケーション設定を使用する場合、部分信頼以外の特別なアクセス許可は不要です。  
  
 アプリケーション設定を [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーション内で使用する場合、`user`.config ファイルは [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] データ ディレクトリに格納されます。 アプリケーションの `user`.config ファイルのサイズは、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] で設定されたデータ ディレクトリ クォータを超えることはできません。 詳細については、「[ClickOnce とアプリケーション設定](/visualstudio/deployment/clickonce-and-application-settings)」を参照してください。  
  
## <a name="custom-settings-providers"></a>カスタム設定プロバイダー  
 アプリケーション設定アーキテクチャでは、アプリケーション設定の間の疎結合から派生したラッパー クラス<xref:System.Configuration.ApplicationSettingsBase>から派生した、関連付けられている設定プロバイダーまたはプロバイダー、および<xref:System.Configuration.SettingsProvider>です。 この関連付けは定義されているだけで、<xref:System.Configuration.SettingsProviderAttribute>ラッパー クラスまたはその個々 のプロパティに適用します。 プロバイダーは明示的に設定が指定されている、既定のプロバイダー場合<xref:System.Configuration.LocalFileSettingsProvider>を使用します。 そのため、このアーキテクチャではカスタム設定プロバイダーの作成と使用がサポートされています。  
  
 たとえば、すべての設定データを Microsoft SQL Server データベースに格納するプロバイダーである `SqlSettingsProvider` を開発して使用するとします。 <xref:System.Configuration.SettingsProvider>-派生クラスでは、この情報を受信します。 その`Initialize`メソッドの型のパラメーターとして<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>です。 実装する、<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>データ ストアからの設定を取得する方法と<xref:System.Configuration.SettingsProvider.SetPropertyValues%2A>に保存します。 プロバイダーを使用して、<xref:System.Configuration.SettingsPropertyCollection>に指定された<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A>だけでなく、その他の設定の属性をプロパティの名前、種類、およびスコープを確認するのには、そのプロパティに対して定義されています。  
  
 カスタム プロバイダーでは、1 つのプロパティと 1 つのメソッドを実装する必要がありますが、この実装はわかりにくいことがあります。 <xref:System.Configuration.SettingsProvider.ApplicationName%2A>プロパティは、抽象の<xref:System.Configuration.SettingsProvider>; を次を返すをプログラミングする必要があります。  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 派生クラスでは、引数を受け取らず値を返さない `Initialize` メソッドも実装する必要があります。 このメソッドは、によって定義されていない<xref:System.Configuration.SettingsProvider>です。  
  
 最後に、実装<xref:System.Configuration.IApplicationSettingsProvider>プロバイダーの設定を更新するためのサポートを提供するには、元に戻すには既定の設定と、1 つのアプリケーションのバージョンから別の設定をアップグレードします。  
  
 カスタム プロバイダーを実装してコンパイルしたら、既定のプロバイダーではなく、このプロバイダーを使用するよう設定クラスに指示する必要があります。 これを行う、<xref:System.Configuration.SettingsProviderAttribute>です。 クラスが定義する各設定に対してプロバイダーが使用される設定クラス全体に適用する場合アプリケーション設定アーキテクチャがのみ、これらの設定をそのプロバイダーを使用しを使用して個々 の設定を適用し場合、<xref:System.Configuration.LocalFileSettingsProvider>残りの部分です。 次のコード例は、カスタム プロバイダーを使用するよう設定クラスに指示する方法を示しています。  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 プロバイダーを複数のスレッドから同時に呼び出すことができますが、プロバイダーは常に同じ格納場所に書き込みを行います。したがって、アプリケーション設定アーキテクチャによってインスタンス化されるカスタム プロバイダー クラスのインスタンスは 1 つに限られます。  
  
> [!IMPORTANT]
>  カスタム プロバイダーがスレッドセーフであり、構成ファイルへの書き込みを実行できるスレッドが一度に 1 つだけであることを確認する必要があります。  
  
 プロバイダーはすべての設定で定義されている属性をサポートする必要はありません、<xref:System.Configuration?displayProperty=nameWithType>名前空間、最小のサポートである必要がありますが<xref:System.Configuration.ApplicationScopedSettingAttribute>と<xref:System.Configuration.UserScopedSettingAttribute>もサポートされていると<xref:System.Configuration.DefaultSettingValueAttribute>です。 サポートされていない属性がある場合、カスタム プロバイダーは通知なしに失敗します。例外をスローする必要はありません。 設定クラスがただし、属性の無効な組み合わせを使用するかどうか: 適用など<xref:System.Configuration.ApplicationScopedSettingAttribute>と<xref:System.Configuration.UserScopedSettingAttribute>の同じ設定を:、プロバイダーが例外をスローし、操作を停止する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [カスタム コントロールのアプリケーション設定](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 [ClickOnce とアプリケーション設定](/visualstudio/deployment/clickonce-and-application-settings)  
 [アプリケーション設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)
