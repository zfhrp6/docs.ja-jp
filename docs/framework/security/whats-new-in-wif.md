---
title: "Windows Identity Foundation 4.5 の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# Windows Identity Foundation 4.5 の新機能
Windows Identity Foundation \(WIF\) の最初のバージョンは、スタンドアロンのダウンロードとして提供され、.NET 3.5 SP1 タイム フレームで導入されたため、WIF 3.5 と呼ばれています。  .NET 4.5 以降、WIF は .NET Framework の一部になっています。  .NET Framework 自体で直接 WIF クラスを使用できるようになったため、.NET プラットフォームでクレーム ベースの ID をより深く統合できるようになり、クレームを簡単に使用できるようになりました。  WIF 3.5 用に作成されたアプリケーションは、新しいモデルを利用するために、変更する必要があります。詳細については、「[WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)」を参照してください。  
  
 主な変更点は、以下のとおりです。  
  
## WIF の .NET Framework への組み込み  
 WIF クラスは、複数のアセンブリに分散されています。主なものは、`mscorlib`、`System.IdentityModel`、`System.IdentityModel.Services`、および `System.ServiceModel` です。  同様に、WIF クラスは、複数の名前空間 \(<xref:System.Security.Claims?displayProperty=fullName>、複数の[System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) 名前空間、および <xref:System.ServiceModel.Security?displayProperty=fullName>\) に分散されています。  <xref:System.Security.Claims?displayProperty=fullName> 名前空間には、新しい <xref:System.Security.Claims.ClaimsPrincipal> クラスと <xref:System.Security.Claims.ClaimsIdentity> クラスが含まれています \(以下を参照\)。  .NET のすべての原則は、<xref:System.Security.Claims.ClaimsPrincipal> から派生しています。  WIF の名前空間およびそれに含まれるクラスの種類の詳細については、「[WIF API リファレンス](../../../docs/framework/security/wif-api-reference.md)」を参照してください。  WIF 3.5 と WIF 4.5 間の名前空間のマッピング方法の詳細については、「[WIF 3.5 と WIF 4.5 間での名前空間マッピング](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)」を参照してください。  
  
## 新しいクレームのモデルとプリンシパル オブジェクト  
 クレームは、.NET Framework 4.5 の中核にあります。基本クレーム クラス \(<xref:System.Security.Claims.Claim>、<xref:System.Security.Claims.ClaimsIdentity>、<xref:System.Security.Claims.ClaimsPrincipal>、<xref:System.Security.Claims.ClaimTypes>および <xref:System.Security.Claims.ClaimValueTypes>\) はすべて、<xref:System.Security.Claims?displayProperty=fullName> 名前空間の `mscorlib` 直下に存在しています。  インターフェイスを使用しなくても、.NET の ID システムにクレームを入力できるようになりました。<xref:System.Security.Principal.WindowsPrincipal>、<xref:System.Security.Principal.GenericPrincipal>、および <xref:System.Web.Security.RolePrincipal> は、<xref:System.Security.Claims.ClaimsPrincipal> から継承されるようになりました。また、<xref:System.Security.Principal.WindowsIdentity>、<xref:System.Security.Principal.GenericIdentity>、および <xref:System.Web.Security.FormsIdentity> は、<xref:System.Security.Claims.ClaimsIdentity> から継承されるようになりました。  つまり、主要なクラスはすべて、クレームに対応しています。  WIF 3.5 の統合クラスとインターフェイス \(`WindowsClaimsIdentity`、`WindowsClaimsPrincipal`、`IClaimsPrincipal`、および `IClaimsIdentity`\) は削除されました。  また、<xref:System.Security.Claims.ClaimsIdentity> クラスはメソッドを公開しているため、その ID のクレームのコレクションを照会しやすくなっています。  
  
## WIF 4.5 の Visual Studio の機能の変更点  
  
-   **\[STS 参照の追加\]** という Visual Studio の機能 \(cmdline ユーティリティの FedUtil\) は既に存在しません。代わりに、新しい Visual Studio の拡張機能 **Identity and Access Tool for Visual Studio 2012** を使用できるようになっています。  これにより、既存の STS を使用してフェデレーションを行うか、LocalSTS を使用して、ソリューションをテストできるようになりました。  拡張機能をインストールした後で、プロジェクトを右クリックし、コンテキスト メニューで **\[Identity and Access\]** を探してください。  
  
-   ASP.NET、Web サイト、および WCF の既存のプロジェクト テンプレートでクレームを直接使用できるようになったため、ASP.NET および STS のテンプレートは現在提供されていません。  
  
-   `Microsoft.IdentityModel.Web.Controls` 名前空間 \(`SignInControl`、`FederatedPassiveSignInControl`、および `FederatedPassiveSignInStatus`\) のコントロールは、WIF 4.5 に引き継がれません。  
  
## WIF 4.5 API の変更点  
  
-   一般的に、クレーム関連クラスは <xref:System.Security.Claims?displayProperty=fullName> 名前空間にあります。WCF 関連クラス \(WS\-Trust シナリオに使用されるサービス コントラクト、チャネル、チャネル ファクトリ、およびサービス ホスト\) は <xref:System.ServiceModel.Security?displayProperty=fullName> にあります。また、他のすべての WIF クラスは、さまざまな [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) 名前空間 \(たとえば、WS\-\* および SAML 成果物を表すクラス、トークン ハンドラーおよび関連クラス、WS フェデレーション シナリオで使用されるクラスなど\) に分散されています。  詳細については、「[WIF 3.5 と WIF 4.5 間での名前空間マッピング](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)」および「[WIF API リファレンス](../../../docs/framework/security/wif-api-reference.md)」を参照してください。  
  
-   マシン キーは、Web ファームのシナリオのセッション クッキーで使用できるように有効化されています。  詳細については、「[WIF および Web ファーム](../../../docs/framework/security/wif-and-web-farms.md)」を参照してください。  
  
-   [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) および [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 要素の下で、宣言によって WIF を構成できます。  WIF 構成の詳細については、「[WIF 構成のリファレンス](../../../docs/framework/security/wif-configuration-reference.md)」を参照してください。  
  
## .NET に WIF を統合したことによるその他の主な .NET の変更点および機能  
  
-   クレーム ベースの承認 \(CBAC\) を実行する潜在力が、.NET Framework に不可欠になりました。  <xref:System.Security.Claims.ClaimsAuthorizationManager> オブジェクトを構成し、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> クラスおよび <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> クラスを使用して、強制アクセス チェックおよび宣言アクセス チェックをコードで実行できます。  CBAC は、従来のロール ベース アクセス チェック \(RBAC\) より柔軟かつ詳細です。  また、ビジネス ロジックは特定のクレームまたはクレーム セットおよび承認ポリシーに基づいてアクセス チェックを実行でき、これらのクレームは宣言によって [\<claimsAuthorizationManager\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) 要素の下で構成できることから、承認ポリシーとビジネス ロジックの分離が向上しています。  
  
## WIF 統合の結果としての WCF の変更点:  
  
-   WCF クレーム ベース ID モデルは WIF に置き換えられています。  これは、WIF クラスの使用を優先し、<xref:System.IdentityModel.Claims?displayProperty=fullName>、<xref:System.IdentityModel.Policy?displayProperty=fullName>、および <xref:System.IdentityModel.Selectors?displayProperty=fullName> 名前空間のクラスは削除する必要があることを意味します。  
  
-   次の XML に示すように `<system.serviceModel>`\/`<behaviors>`\/`<serviceBehaviors>`\/`<serviceCredentials>` 要素で `useIdentityConfiguration` 属性が指定され、WCF サービス上で WIF が有効になりました。  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     **Identity and Access Tool for Visual Studio 2012** \(前の「**Visual Studio の機能の変更点**」を参照\) を使用する場合、`useIdentityConfiguration` 属性が構成ファイルに設定された `<serviceCredentials>` 要素が追加されます。  また、WIF 構成設定が含まれ、対応する [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 要素も追加されます。選択した STS に認証を外部委託するために必要なバインディングやその他の設定も追加されます。  
  
## 参照  
 [WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)   
 [WIF 3.5 と WIF 4.5 間での名前空間マッピング](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)   
 [WIF API リファレンス](../../../docs/framework/security/wif-api-reference.md)   
 [WIF 構成のリファレンス](../../../docs/framework/security/wif-configuration-reference.md)