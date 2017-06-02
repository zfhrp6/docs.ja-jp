---
title: "コード アクセス セキュリティ ポリシーの互換性と移行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CLR ポリシー移行"
  - "ポリシー移行, 互換性"
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# コード アクセス セキュリティ ポリシーの互換性と移行
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、コード アクセス セキュリティ \(CAS\) のポリシー部分は廃止されました。  その結果、廃止されたポリシーの種類とメンバーを[明示的](#explicit_use)に呼び出したり、\(他の種類およびメンバーを介して\) [暗黙的](#implicit_use)に呼び出したりすると、コンパイルの警告やランタイム例外が発生する可能性があります。  
  
 以下のいずれかの方法で警告やエラーを回避できます。  
  
-   廃止された呼び出しに代わる [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] の代替方法に[移行](#migration)します。  
  
     または  
  
-   [\<NetFx40\_LegacySecurityPolicy\> 構成要素](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)を使用して、レガシーの CAS ポリシー動作を選択します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [明示的な使用](#explicit_use)  
  
-   [暗黙的な使用](#implicit_use)  
  
-   [エラーと警告](#errors_and_warnings)  
  
-   [移行: 廃止された呼び出しの代替方法](#migration)  
  
-   [互換性: CAS ポリシーのレガシー オプションを使用する](#compatibility)  
  
> [!CAUTION]
>  コード アクセス セキュリティと部分的に信頼できるコード  
>   
>  .NET Framework には、コード アクセス セキュリティ \(CAS\) と呼ばれる、同一アプリケーションで実行される各種コードにさまざまな信頼レベルを強制的に適用するメカニズムが備わっています。  .NET Framework におけるコード アクセス セキュリティを、部分的に信頼できるコード、特に発生元の不明なコードのセキュリティ境界として使用しないでください。  発生元の不明なコードの読み込みと実行に関しては、他のセキュリティ対策を適切に導入することなく行わないようにしてください。  
>   
>  このポリシーは .NET Framework のすべてのバージョンに適用されますが、Silverlight に含まれる .NET Framework には適用されません。  
  
<a name="explicit_use"></a>   
## 明示的な使用  
 直接セキュリティ ポリシーを操作するメンバー、または CAS ポリシーをサンドボックス化することが必要なメンバーは廃止され、既定ではエラーを発生するようになりました。  
  
 以下に例を示します。  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=fullName>  
  
<a name="implicit_use"></a>   
## 暗黙的な使用  
 アセンブリの読み込みオーバーロードの中にはエラーを生成するものがあります。CAS ポリシーを暗黙的に使用することが原因です。  これらのオーバーロードはCAS ポリシーを解決するために <xref:System.Security.Policy.Evidence> パラメーターを取り、アセンブリにアクセス許可セットを提供します。  
  
 以下に例をいくつか示します。  パラメーターとして <xref:System.Security.Policy.Evidence> を取るオーバーロードが廃止されました。  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
<a name="errors_and_warnings"></a>   
## エラーと警告  
 廃止された種類とメンバーが使用されると、以下のエラー メッセージが生成されます。  <xref:System.Security.Policy.Evidence?displayProperty=fullName> 型自体は廃止されていないことに注意してください。  
  
 コンパイル時の警告:  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework.  Please use <suggested alternate API>.  See <link> for more information.'`  
  
 実行時の例外:  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## 移行: 廃止された呼び出しの代替方法  
  
### アセンブリの信頼レベルの判別  
 CAS ポリシーは多くの場合、アセンブリ、アプリケーション ドメインのアクセス許可セット、または信頼レベルを判断するために使用されます。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] では、セキュリティ ポリシーを解決する必要のない次の便利なプロパティが公開されています。  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=fullName>  
  
### アプリケーション ドメインのサンドボックス化  
 通常 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName> メソッドは、アプリケーション ドメイン内のアセンブリをサンド ボックス化するために使用します。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] では、このために <xref:System.Security.Policy.PolicyLevel> を使用する必要がないメンバーが公開されています。 詳しくは、「[方法 : サンドボックスで部分信頼コードを実行する](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)」をご覧ください。  
  
### 部分的に信頼できるコードに対する安全なまたは適切なアクセス許可セットの決定  
 多くの場合ホストでは、ホストされているコードをサンドボックス化するための適切なアクセス許可を判別する必要があります。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] より前のバージョンでは、CAS ポリシーでは <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName> メソッドを使用してこれが行われていました。  代わりに、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] では <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName> メソッドが提供され、提供されている証拠に基づいて安全な標準のアクセス許可セットが返されます。  
  
### サンドボックス化以外のシナリオ: アセンブリ読み込みのオーバーロード  
 アセンブリ読み込みオーバーロードを使用する目的は、アセンブリのサンドボックス化の代わりに、アセンブリ読み込みオーバーロードでないと使用できないパラメーターを指定することです。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降、<xref:System.Security.Policy.Evidence?displayProperty=fullName> オブジェクトをパラメーターとして必要としないアセンブリ読み込みオーバーロード \([AppDomain.ExecuteAssembly\(String, String\[\], Byte\<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=fullName> など\) をこのシナリオで使用できます。  
  
 アセンブリをサンドボックス化する場合には、[AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> オーバー ロードを使用します。  
  
<a name="compatibility"></a>   
## 互換性: CAS ポリシーのレガシー オプションを使用する  
 [\<NetFx40\_LegacySecurityPolicy\> 構成要素](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)を使用すると、CAS レガシー ポリシーを使用するプロセスまたはライブラリを指定できます。  この要素を有効にすると、ポリシーと証拠のオーバーロードは、framework の以前のバージョンの場合と同様に動作します。  
  
> [!NOTE]
>  CAS ポリシーの動作は特定のランタイム バージョンに固有なので、そのランタイム バージョンの CAS ポリシーを変更しても、別のバージョンの CAS ポリシーには影響しません。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [方法 : サンドボックスで部分信頼コードを実行する](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)