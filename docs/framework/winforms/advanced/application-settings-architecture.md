---
title: "アプリケーション設定アーキテクチャ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション設定 [Windows フォーム], アーキテクチャ"
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# アプリケーション設定アーキテクチャ
このトピックでは、アプリケーション設定アーキテクチャのしくみについて説明し、グループ設定や設定キーなど、アーキテクチャの高度な機能についても解説します。  
  
 アプリケーション設定アーキテクチャにより、アプリケーション スコープまたはユーザー スコープを使用して厳密に型指定された設定の定義や、アプリケーション セッション間における設定の永続化がサポートされます。  また、このアーキテクチャによって、ローカル ファイル システムとの間で設定を保存したり、設定を読み込んだりするために使用する、既定の永続化エンジンが提供されます。  さらに、このアーキテクチャは、カスタムの永続化エンジンを指定するためのインターフェイスも定義します。  
  
 カスタム コンポーネントがアプリケーションにホストされる際に、そのコンポーネントの独自の設定を永続化できるようにするインターフェイスが提供されます。  設定キーを使用することにより、コンポーネントでそのコンポーネントの複数のインスタンスの設定を区別できます。  
  
## 設定の定義  
 アプリケーション設定アーキテクチャは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] および Windows フォームの内部で使用され、この両方の環境で共有される多くの基本クラスを含みます。  最も重要な基本クラスは <xref:System.Configuration.SettingsBase> であり、コレクションを介した設定へのアクセスと、設定を読み込んだり保存したりするための下位のメソッドを提供します。  各環境は、<xref:System.Configuration.SettingsBase> から派生した独自のクラスを実装し、その環境用の追加の設定機能を提供します。  Windows フォーム ベースのアプリケーションでは、次に示すような機能を基本クラスに追加する <xref:System.Configuration.ApplicationSettingsBase> クラスの派生クラス上で、すべてのアプリケーション設定を定義する必要があります。  
  
-   高水準の読み込み操作および保存操作  
  
-   ユーザー スコープの設定のサポート  
  
-   ユーザー設定から定義済み既定値への復帰  
  
-   以前のバージョンのアプリケーションで使用した設定のアップグレード  
  
-   設定の変更前または保存前における検証  
  
 設定は、<xref:System.Configuration> 名前空間内で定義されている数多くの属性を使用して表すことができます。これらの属性については、「[アプリケーション設定の属性](../../../../docs/framework/winforms/advanced/application-settings-attributes.md)」を参照してください。  設定を定義する際は、<xref:System.Configuration.ApplicationScopedSettingAttribute> または <xref:System.Configuration.UserScopedSettingAttribute> のいずれかを使用して設定を適用する必要があります。これにより、その設定がアプリケーション全体に適用されるか、または現在のユーザーにだけ適用されるかが指定されます。  
  
 次のコード例では、 `BackgroundColor` という単一の設定を持つカスタム設定クラスを定義します。  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## 設定の永続化  
 <xref:System.Configuration.ApplicationSettingsBase> クラス自体は設定の永続化も読み込みも行いません。この作業は <xref:System.Configuration.SettingsProvider> の派生クラスである設定プロバイダーによって行われます。  <xref:System.Configuration.ApplicationSettingsBase> の派生クラスが <xref:System.Configuration.SettingsProviderAttribute> を使用して設定プロバイダーを指定しない場合は、既定のプロバイダーである <xref:System.Configuration.LocalFileSettingsProvider> が使用されます。  
  
 もともと [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] と共にリリースされた構成システムでは、ローカル コンピューターの machine.config ファイルまたはアプリケーションと共に配置する `app.`exe.config ファイルを介した、静的なアプリケーション構成データの提供がサポートされています。  <xref:System.Configuration.LocalFileSettingsProvider> クラスによって、このネイティブ サポートが次のように拡張されます。  
  
-   アプリケーション スコープの設定は machine.config ファイルまたは `app.`exe.config ファイルに格納できます。  machine.config は常に読み取り専用です。一方、`app`.exe.config はセキュリティ上の配慮から、大部分のアプリケーションで読み取り専用に制限されています。  
  
-   ユーザー スコープの設定は `app`.exe.config ファイルに格納できます。この場合、設定は静的な既定値として扱われます。  
  
-   既定値以外のユーザー スコープの設定は、*user*.config という新しいファイルに格納されます。*user* は現在このアプリケーションを実行しているユーザーの名前です。  ユーザー スコープの設定の既定値は、<xref:System.Configuration.DefaultSettingValueAttribute> を使用して指定できます。  ユーザー スコープの設定はアプリケーションの実行時に変更されることがよくあるため、`user`.config は常に読み取り\/書き込み用となります。  
  
 この 3 つの構成ファイルはいずれも XML 形式で設定を格納します。  アプリケーション スコープの設定の最上位 XML 要素は、`<appSettings>` で、ユーザー スコープの設定の最上位 XML 要素は `<userSettings>` です。  アプリケーション スコープの設定およびユーザー スコープの設定の既定値を含む `app`.exe.config ファイルは、次のようになります。  
  
```  
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
  
 構成ファイルのアプリケーション設定セクションに含まれる要素の定義については、「[アプリケーション設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)」を参照してください。  
  
### 設定のバインディング  
 アプリケーション設定では、Windows フォーム データのバインディング アーキテクチャを使用し、設定オブジェクトと設定コンポーネントの間で、設定の更新を双方向で通信します。  Visual Studio を使用してアプリケーション設定を作成し、その設定をコンポーネントのプロパティに割り当てる場合、このバインディングは自動的に生成されます。  
  
 <xref:System.Windows.Forms.IBindableComponent> インターフェイスをサポートするコンポーネントに対しては、アプリケーション設定のバインド以外は実行できません。  また、コンポーネントでは、特定のバインドされたプロパティに変更イベントを実装するか、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを使用してプロパティの変更をアプリケーション設定へ通知する必要があります。  コンポーネントで <xref:System.Windows.Forms.IBindableComponent> を実装せずに Visual Studio を使用してバインドした場合、バインドされたプロパティは初回のみ設定されますが、更新されません。  コンポーネントが <xref:System.Windows.Forms.IBindableComponent> を実装してもプロパティの変更通知をサポートしていない場合、プロパティが変更されたときに設定のバインディングは更新されません。  
  
 <xref:System.Windows.Forms.ToolStripItem> など、一部の Windows フォーム コンポーネントは、設定のバインディングをサポートしていません。  
  
### 設定のシリアル化  
 <xref:System.Configuration.LocalFileSettingsProvider> がディスクに設定を保存する必要がある場合、次のような処理を実行します。  
  
1.  リフレクションを使用して、<xref:System.Configuration.ApplicationSettingsBase> 派生クラスで定義されているすべてのプロパティを調べ、<xref:System.Configuration.ApplicationScopedSettingAttribute> または <xref:System.Configuration.UserScopedSettingAttribute> を使用して適用されたプロパティを見つけます。  
  
2.  プロパティをディスクにシリアル化します。  まず、型に関連付けられている <xref:System.ComponentModel.TypeConverter> に <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> または <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> を呼び出そうとします。  これが成功しない場合、代わりに XML シリアル化を使用します。  
  
3.  設定の属性に基づいて、どの設定がどのファイルに指定されているかを判断します。  
  
 独自の設定クラスを実装している場合、<xref:System.Configuration.SettingsSerializeAsAttribute> で <xref:System.Configuration.SettingsSerializeAs> 列挙値を使用して、バイナリのシリアル化またはカスタムのシリアル化の設定にマークを付けることができます。  コードで独自の設定クラスを作成する方法の詳細については、「[方法 : アプリケーション設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)」を参照してください。  
  
### 設定ファイルの場所  
 `app`.exe.config ファイルおよび *user*.config ファイルの場所は、アプリケーションのインストール方法によって異なります。  Windows フォーム ベースのアプリケーションをローカル コンピューターにコピーした場合、`app`.exe.config はアプリケーションのメインの実行可能ファイルのベース ディレクトリと同じディレクトリに配置され、*user*.config は <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=fullName> プロパティで指定した場所に配置されます。  アプリケーションを [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] を使用してインストールした場合、どちらのファイルも %InstallRoot%\\Documents and Settings\\*username*\\Local Settings の下にある [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] のデータ ディレクトリに配置されます。  
  
 ユーザーがローミング プロファイルを有効にしている場合、これらのファイルの格納場所はわずかに異なります。ローミング プロファイルでは、ユーザーがドメイン内の別のコンピューターを使用する際に Windows とアプリケーションに対して異なる設定を定義できます。  この場合、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーションも [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 以外のアプリケーションも、`app`.exe.config ファイルおよび *user*.config ファイルが %InstallRoot%\\Documents and Settings\\*username*\\Application Data に格納されます。  
  
 アプリケーション設定機能と新しい配置テクノロジの連携の詳細については、「[ClickOnce とアプリケーション設定](../Topic/ClickOnce%20and%20Application%20Settings.md)」を参照してください。  [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] のデータ ディレクトリの詳細については、「[ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../Topic/Accessing%20Local%20and%20Remote%20Data%20in%20ClickOnce%20Applications.md)」を参照してください。  
  
## アプリケーション設定とセキュリティ  
 アプリケーション設定は部分信頼で機能するように設計されています。部分信頼とは、インターネット上やイントラネット上でホストされる Windows フォーム アプリケーションにとって既定となる制限された環境のことです。  既定の設定プロバイダーと共にアプリケーション設定を使用する場合、部分信頼以外に特別なアクセス許可は必要ありません。  
  
 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] アプリケーション内でアプリケーション設定を使用する場合、`user`.config ファイルは [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] のデータ ディレクトリに格納されます。  アプリケーションの `user`.config ファイルのサイズを、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] で設定したデータ ディレクトリ クォータより大きくすることはできません。  詳細については、「[ClickOnce とアプリケーション設定](../Topic/ClickOnce%20and%20Application%20Settings.md)」を参照してください。  
  
## カスタム設定プロバイダー  
 アプリケーション設定アーキテクチャでは、<xref:System.Configuration.ApplicationSettingsBase> から派生したアプリケーション設定ラッパー クラスと、<xref:System.Configuration.SettingsProvider> から派生した、1 つまたは複数の関連するプロバイダーとの間には緩い結合があります。  この結合は、ラッパー クラスまたはその個々のプロパティに適用されている <xref:System.Configuration.SettingsProviderAttribute> によってのみ定義されます。  設定プロバイダーを明示的に指定しないと、既定のプロバイダーである <xref:System.Configuration.LocalFileSettingsProvider> が使用されます。  したがって、このアーキテクチャではカスタム設定プロバイダーの作成と使用がサポートされていることになります。  
  
 たとえば、すべての設定データを Microsoft SQL Server データベースに格納するプロバイダーである `SqlSettingsProvider` を使用するとします。  <xref:System.Configuration.SettingsProvider> 派生クラスは、この情報を <xref:System.Collections.Specialized.NameValueCollection?displayProperty=fullName> 型のパラメーターとして  `Initialize`  メソッドで受け取ります。  次に、<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> メソッドを実装して、設定値をデータ ストアから取得し、<xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> を使用して保存します。  このプロバイダーは、<xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> に指定される <xref:System.Configuration.SettingsPropertyCollection> を使用して、プロパティの名前、型、スコープや、このプロパティに対して定義されたその他の設定属性を判断します。  
  
 このプロバイダーでは、1 つのプロパティと 1 つのメソッドを実装する必要がありますが、この実装はわかりにくいことがあります。  <xref:System.Configuration.SettingsProvider.ApplicationName%2A> プロパティは、<xref:System.Configuration.SettingsProvider> の抽象プロパティです。次のような値を返すようにプログラムする必要があります。  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 また、派生クラスは、引数を受け取らず値を返さない `Initialize` メソッドも実装する必要があります。  このメソッドは <xref:System.Configuration.SettingsProvider> によって定義されません。  
  
 最後にプロバイダーに <xref:System.Configuration.IApplicationSettingsProvider> を実装して、設定の更新、設定値から既定値への復帰、およびアプリケーションのあるバージョンから別のバージョンへの設定のアップグレードをサポートします。  
  
 カスタム プロバイダーの実装とコンパイルを行った後、設定クラスに対して、既定のプロバイダーではなくこのプロバイダーを使用するように指示する必要があります。  これには、<xref:System.Configuration.SettingsProviderAttribute> を使用します。  設定クラス全体にこのプロバイダーを適用した場合、このプロバイダーはこのクラスが定義する各設定に対して使用されます。個々の設定に適用した場合、アプリケーション設定アーキテクチャは、該当する設定に対してのみこのプロバイダーを使用し、それ以外の設定については <xref:System.Configuration.LocalFileSettingsProvider> を使用します。  次のコード例では、設定クラスに対してカスタム プロバイダーを使用するように指示する方法を示します。  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 複数のスレッドから同時にプロバイダーを呼び出すことができますが、プロバイダーは常に同じストレージの場所に書き込みを行います。したがって、アプリケーション設定アーキテクチャによってインスタンス化されるカスタム プロバイダー クラスは 1 つだけです。  
  
> [!IMPORTANT]
>  カスタム プロバイダーがスレッド セーフであり、構成ファイルへの書き込みを実行できるのは一度に 1 つのスレッドだけであることを確認しておく必要があります。  
  
 カスタム プロバイダーは <xref:System.Configuration?displayProperty=fullName> 名前空間で定義されているすべての設定属性をサポートする必要はありませんが、少なくとも <xref:System.Configuration.ApplicationScopedSettingAttribute>、<xref:System.Configuration.UserScopedSettingAttribute>、および <xref:System.Configuration.DefaultSettingValueAttribute> をサポートしている必要があります。  サポートしていない属性については、カスタム プロバイダーは警告なしに失敗し、例外をスローしません。  ただし、設定クラスが無効な属性の組み合わせを使用した場合 \(同じ設定に <xref:System.Configuration.ApplicationScopedSettingAttribute> と <xref:System.Configuration.UserScopedSettingAttribute> を適用するなど\)、カスタム プロバイダーは例外をスローし、操作が中断されます。  
  
## 参照  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 <xref:System.Configuration.LocalFileSettingsProvider>   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [カスタム コントロールのアプリケーション設定](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)   
 [ClickOnce とアプリケーション設定](../Topic/ClickOnce%20and%20Application%20Settings.md)   
 [アプリケーション設定のスキーマ](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)