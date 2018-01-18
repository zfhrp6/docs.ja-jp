---
title: "接続文字列と構成ファイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 358bc0428a53817e85d5a5e278d8da4e1a8b6927
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-and-configuration-files"></a>接続文字列と構成ファイル
接続文字列をアプリケーションのコードに組み込むと、セキュリティ上の脆弱性やメンテナンスの問題を引き起こす可能性があります。 使用して、アプリケーションのソース コードにコンパイルされ暗号化されていない接続文字列を表示できます、 [Ildasm.exe (IL 逆アセンブラー)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md)ツールです。 さらに、接続文字列が変わるたびにアプリケーションを再コンパイルする必要性が生じます。 そのため、接続文字列はアプリケーション構成ファイルに保存することをお勧めします。  
  
## <a name="working-with-application-configuration-files"></a>アプリケーション構成ファイルの使用  
 アプリケーション構成ファイルには、特定のアプリケーションに固有の設定が格納されます。 1 つまたは複数の ASP.NET アプリケーションは、たとえば、 **web.config**ファイル、および Windows アプリケーションは、省略可能な可能性があります**app.config**ファイル。 構成ファイルの名前と場所はアプリケーションのホストによって異なりますが、どの構成ファイルにも共通の要素があります。  
  
### <a name="the-connectionstrings-section"></a>connectionStrings セクション  
 接続文字列は、キーと値のペアとして保存すること、 **connectionStrings**のセクションで、**構成**アプリケーション構成ファイルの要素。 子要素には、**追加**、**オフ**、および**削除**です。  
  
 次の構成ファイル フラグメントは、接続文字列を格納するためのスキーマと構文の例を示しています。 **名前**属性は、実行時に取得できるようにするために、接続文字列を一意に識別する指定した名前です。 **ProviderName** machine.config ファイルに登録されている .NET Framework データ プロバイダーの不変の名前を指定します。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  構成ファイルに接続文字列の一部を保存しておき、<xref:System.Data.Common.DbConnectionStringBuilder> クラスを使用して実行時に補完できます。 接続文字列の要素を事前に知ることができない場合や、機密情報を構成ファイルに保存したくない場合には有効な手段です。 詳細については、次を参照してください。[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)です。  
  
### <a name="using-external-configuration-files"></a>外部構成ファイルの使用  
 外部構成ファイルとは、単一のセクションから成る、構成ファイルのフラグメントを含んだ独立したファイルを言います。 外部構成ファイルは、メインの構成ファイルによって参照されます。 格納する、 **connectionStrings**物理的に独立したファイルのセクションは、アプリケーションの展開後の接続文字列を変更することが場合に便利です。 たとえば、構成ファイルに修正が加えられた場合、ASP.NET の標準的な動作ではアプリケーション ドメインが再起動され、その結果、状態情報が失われてしまいます。 しかし、外部構成ファイルに対する修正であればアプリケーションの再起動は伴いません。 外部構成ファイルは ASP.NET だけでなく、Windows アプリケーションでも使用できます。 また、ファイルのアクセス セキュリティや権限を使用して、外部構成ファイルへのアクセスを制限することもできます。 実行時における外部構成ファイルの使用は透過的であり、特殊なコーディングも不要です。  
  
 接続文字列を外部構成ファイルに保存するには、のみを含む別のファイルを作成、 **connectionStrings**セクションです。 それ以外の要素、セクション、または属性は含めないでください。 外部構成ファイルの構文の例を次に示します。  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 使用するメインのアプリケーション構成ファイルで、 **configSource**属性を完全修飾名と外部のファイルの場所を指定します。 この例では、`connections.config` という名前の外部構成ファイルを参照しています。  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>接続文字列の実行時の取得  
 .NET Framework 2.0 では、<xref:System.Configuration> 名前空間に新しいクラスが導入され、実行時に簡単に構成ファイルから接続文字列を取得できるようになりました。 プログラムから名前またはプロバイダー名を使用して接続文字列を取得できます。  
  
> [!NOTE]
>  **Machine.config**ファイルも含まれます、 **connectionStrings**セクションでは、Visual Studio によって使用される接続文字列が含まれています。 プロバイダー名を使用して接続文字列を取得するときに、 **app.config**ファイル内の接続文字列の Windows アプリケーションで**machine.config** からロードしてから、エントリを取得**app.config**です。追加**オフ**後すぐに、 **connectionStrings**要素は、接続文字列だけが、ローカルで定義されているように、メモリ内データ構造体から継承されたすべての参照を削除**app.config**ファイルと見なされます。  
  
### <a name="working-with-the-configuration-classes"></a>構成クラスの使用  
 .NET Framework 2.0 以降では、ローカル コンピューター上の構成ファイルで作業するときに、廃止された <xref:System.Configuration.ConfigurationManager> に代わって <xref:System.Configuration.ConfigurationSettings> を使用します。 ASP.NET 構成ファイルでの作業では、<xref:System.Web.Configuration.WebConfigurationManager> を使用します。 Web サーバー上の構成ファイルを使用するように設計されたなどにより、構成ファイルのセクションにプログラムでアクセス**system.web**です。  
  
> [!NOTE]
>  実行時に構成ファイルにアクセスするには、呼び出し元に権限を付与する必要があります。必要な権限は、アプリケーションの種類、構成ファイル、格納場所などによって異なります。 詳細については、次を参照してください。[構成クラスを使用して](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)と<xref:System.Web.Configuration.WebConfigurationManager>ASP.NET アプリケーション用と<xref:System.Configuration.ConfigurationManager>Windows アプリケーション用。  
  
 <xref:System.Configuration.ConnectionStringSettingsCollection> を使用すると、アプリケーション構成ファイルから接続文字列を取得できます。 コレクションが含まれています<xref:System.Configuration.ConnectionStringSettings>オブジェクト、単一のエントリを表す、 **connectionStrings**セクションです。 個々のプロパティは接続文字列の属性にマップされており、名前またはプロバイダー名を指定することによって接続文字列を取得できます。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|接続文字列の名前。 マップ、**名前**属性。|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|プロバイダーの完全修飾名。 マップ、 **providerName**属性。|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|接続文字列。 マップ、 **connectionString**属性。|  
  
### <a name="example-listing-all-connection-strings"></a>例 : すべての接続文字列を一覧表示する  
 この例では、`ConnectionStringSettings` コレクションを反復処理しながら、<xref:System.Configuration.ConnectionStringSettings.Name%2A>、<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>、<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> の各プロパティをコンソール ウィンドウに表示します。  
  
> [!NOTE]
>  プロジェクトの種類によっては System.Configuration.dll がインクルードされていない場合があります。構成クラスを使用する場合は、必要に応じて参照設定するようにしてください。 特定のアプリケーションの構成ファイルの名前と場所は、アプリケーションの種類やホストしているプロセスによって異なります。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>例 : 接続文字列を名前で取得する  
 次の例では、接続文字列の名前を指定することによって、接続文字列を構成ファイルから取得する方法を説明します。 このコードでは、指定された入力パラメーターと <xref:System.Configuration.ConnectionStringSettings> の名前とを照合することによって、<xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A> オブジェクトを作成します。 一致する名前が見つからなかった場合は `null` (Visual Basic の場合は `Nothing`) が返されます。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>例 : 接続文字列をプロバイダー名で取得する  
 この例は、の形式でプロバイダーの不変名を指定することによって、接続文字列を取得する方法を示します*System.Data.ProviderName*です。 このコードでは、<xref:System.Configuration.ConnectionStringSettingsCollection> を反復処理し、最初に見つかった <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> の接続文字列を返します。 プロバイダー名が見つからなかった場合は `null` (Visual Basic の場合は `Nothing`) が返されます。  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>保護構成を使った構成ファイル セクションの暗号化  
 ASP.NET 2.0 と呼ばれる、新しい機能が導入されました。*保護構成*、構成ファイル内の機密情報を暗号化することができます。 保護構成は、主に ASP.NET を想定して設計されたものですが、Windows アプリケーションの構成ファイル セクションを暗号化する目的でも使用できます。 保護された構成機能の詳細については、次を参照してください。[暗号化の構成情報を使用して保護された構成](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)です。  
  
 次の構成ファイル フラグメントは、 **connectionStrings**暗号化された後のセクションです。 **ConfigProtectionProvider**暗号化し、の接続文字列を暗号化解除に使用する保護された構成プロバイダーを指定します。 **EncryptedData**セクションには、暗号化テキストが含まれています。  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 .NET Framework で指定されたプロバイダーを使用して、暗号化を解除する実行時に暗号化された接続文字列が取得される場合、 **CipherValue**アプリケーションを利用できるようにします。 復号化のプロセスを管理するためのコードを自分で作成する必要はありません。  
  
### <a name="protected-configuration-providers"></a>保護構成プロバイダー  
 保護された構成プロバイダーが登録されている、 **configProtectedData**のセクションで、 **machine.config** 2 つを示しています、次のフラグメントに示すように、ローカル コンピューター上のファイル保護構成プロバイダーが .NET Framework に付属しています。 ここでは、読みやすくするために一部の値を省略しています。  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 追加することによって、別の保護構成プロバイダーを構成することができます、 **machine.config**ファイル。 また、<xref:System.Configuration.ProtectedConfigurationProvider> 抽象基本クラスを継承することで、保護構成プロバイダーを独自に作成することもできます。 次の表は、.NET Framework に含まれている 2 つの構成プロバイダーを示しています。  
  
|プロバイダー|説明|  
|--------------|-----------------|  
|<!--zz<xref:System.Configuration.RSAProtectedConfigurationProvider>-->`System.Configuration.RSAProtectedConfigurationProvider`|データの暗号化と復号化には、RSA 暗号化アルゴリズムが使用されます。 RSA アルゴリズムは、公開キー暗号化だけでなく、デジタル署名にも使用されます。 "公開キー" として知られているほか、2 つの異なるキーが使用されることから非対称暗号化と呼ばれる場合もあります。 使用することができます、 [ASP.NET IIS 登録ツール (Aspnet_regiis.exe)](http://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b)を Web.config ファイルのセクションを暗号化および暗号化キーを管理します。 構成ファイルは、その処理時に ASP.NET によって復号化されます。 ASP.NET アプリケーションの ID には、セクションの暗号化と復号化に使用される暗号化キーへの読み取りアクセスが必要です。|  
|<!--zz<xref:System.Configuration.DPAPIProtectedConfigurationProvider>-->`System.Configuration.DPAPIProtectedConfigurationProvider`|構成セクションの暗号化に Windows Data Protection API (DPAPI) が使用されます。 この API には、Windows の組み込み暗号化サービスが使用され、コンピューター単位またはユーザー アカウント単位の保護を構成できます。 コンピューター単位の保護は、同じサーバー上の複数のアプリケーションで情報を共有する必要がある場合に使用します。 共有ホスティング環境など、特定のユーザー ID で実行されるサービスには、ユーザー アカウント単位の保護を使用できます。 各アプリケーションは、ファイルやデータベースなど、各種リソースへのアクセスが制限された別々の ID で実行されます。|  
  
 どちらのプロバイダーも、強力なデータ暗号化機能を備えています。 ただし、Web ファームなど、複数のサーバーで、同じ構成ファイルを暗号化して使用する場合、データの暗号化に使用される暗号化キーをエクスポートしたり、それを別のサーバーにインポートしたりできるのは、`RsaProtectedConfigurationProvider` だけです。 詳細については、次を参照してください。[インポートおよびエクスポートする保護された構成の RSA キー コンテナー](http://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc)です。  
  
### <a name="using-the-configuration-classes"></a>構成クラスの使用  
 <xref:System.Configuration> 名前空間には、構成設定をプログラムから行うためのクラスが存在します。 <xref:System.Configuration.ConfigurationManager> クラスは、コンピューター、アプリケーション、ユーザーの各構成ファイルへのアクセスを提供します。 使用することができます、ASP.NET アプリケーションを作成する場合、<xref:System.Web.Configuration.WebConfigurationManager>内で検索できるなどの ASP.NET アプリケーションに固有の設定にアクセスすることもできます、同じ機能を提供するクラス **\<system.web >**です。  
  
> [!NOTE]
>  <xref:System.Security.Cryptography> 名前空間には、データの暗号化と復号化に関連した補足的なオプションを提供するクラスが存在します。 これらのクラスは、保護構成では利用できない暗号化サービスが必要な場合に使用します。 これらのクラスは必ずしも純粋なマネージ実装とは限らず、アンマネージ Microsoft CryptoAPI 用のラッパーもあります。 詳細については、「[暗号サービス](http://msdn.microsoft.com/en-us/68a1e844-c63c-44af-9247-f6716eb23781)」をご覧ください。  
  
### <a name="appconfig-example"></a>App.config の例  
 この例では、暗号化を切り替える、 **connectionStrings** 」の「、 **app.config** Windows アプリケーション用のファイルです。 この例に示したプロシージャは、MyApplication.exe など、アプリケーションの名前を引数として受け取ります。 **App.config**ファイルが、暗号化および MyApplication.exe.config という名前で実行可能ファイルが含まれているフォルダーにコピーします。  
  
> [!NOTE]
>  接続文字列は暗号化したときと同じコンピューターでしか復号化できません。  
  
 コードを使用して、<xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A>を開くメソッドを**app.config**ファイルを編集し、<xref:System.Configuration.ConfigurationManager.GetSection%2A>メソッドを返します。、 **connectionStrings**セクションです。 さらに、<xref:System.Configuration.SectionInformation.IsProtected%2A> プロパティをチェックし、セクションがまだ暗号化されていなければ、<xref:System.Configuration.SectionInformation.ProtectSection%2A> を呼び出して暗号化します。 それ以外の場合は、<xref:System.Configuration.SectionInformation.UnprotectSection%2A> メソッドを呼び出してセクションを復号化します。 最後に、<xref:System.Configuration.Configuration.Save%2A> メソッドで操作を完了し、変更内容を保存します。  
  
> [!NOTE]
>  このコードを実行するには、プロジェクトで `System.Configuration.dll` を参照設定する必要があります。  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Web.config の例  
 この例では、<xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> の `WebConfigurationManager` メソッドを使用しています。 ここで指定できる点への相対パスに注意してください、 **Web.config**チルダを使用してファイル。 このコードを実行するには、`System.Web.Configuration` クラスへの参照が必要です。  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 ASP.NET アプリケーションのセキュリティ保護の詳細については、次を参照してください。 [NIB: ASP.NET セキュリティ](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d)と[一目で ASP.NET 2.0 セキュリティ プラクティス](http://go.microsoft.com/fwlink/?LinkId=59997)ASP.NET デベロッパー センターにします。  
  
## <a name="see-also"></a>参照  
 [接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [構成クラスの使用](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [アプリの構成](../../../../docs/framework/configure-apps/index.md)  
 [ASP.NET Web サイトの管理](http://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
