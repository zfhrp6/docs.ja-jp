---
title: "&lt;disableFusionUpdatesFromADManager&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "<disableFusionUpdatesFromADManager> 要素"
  - "disableFusionUpdatesFromADManager 要素"
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;disableFusionUpdatesFromADManager&gt; 要素
アプリケーション ドメインの構成設定をランタイム ホストがオーバーライドできるという既定の動作を、無効にするかどうかを指定します。  
  
## 構文  
  
```  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> Fusion の設定をオーバーライドする既定の機能を無効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|0|Fusion の設定をオーバーライドする機能を無効にしません。  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、これが既定の動作です。|  
|1|Fusion の設定をオーバーライドする機能を無効にします。  これにより、.NET Framework の以前のバージョンの動作に戻ります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降の既定の動作では、<xref:System.AppDomainManager> オブジェクトが構成設定をオーバーライドできます。そのためには、<xref:System.AppDomainManager> の独自のサブクラスで、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName> メソッドの実装に渡された <xref:System.AppDomainSetup> オブジェクトの <xref:System.AppDomainSetup.ConfigurationFile%2A> プロパティまたは <xref:System.AppDomainSetup.SetConfigurationBytes%2A> メソッドを使用します。  既定のアプリケーション ドメインでは、変更された設定によって、アプリケーション構成ファイルで指定された設定がオーバーライドされます。  その他のアプリケーション ドメインでは、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> メソッドまたは <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName> メソッドに渡された構成設定がオーバーライドされます。  
  
 渡された構成情報を削除するには、新しい構成情報を渡すか、または null \(Visual Basic では `Nothing`\) を渡すことができます。  
  
 構成情報は、<xref:System.AppDomainSetup.ConfigurationFile%2A> プロパティと <xref:System.AppDomainSetup.SetConfigurationBytes%2A> メソッドのどちらか一方に渡すようにしてください。  両方に構成情報を渡した場合、<xref:System.AppDomainSetup.SetConfigurationBytes%2A> メソッドはアプリケーション構成ファイルの構成情報をオーバーライドするため、<xref:System.AppDomainSetup.ConfigurationFile%2A> プロパティに渡した情報は無視されます。  <xref:System.AppDomainSetup.ConfigurationFile%2A> プロパティを使用する場合は、<xref:System.AppDomainSetup.SetConfigurationBytes%2A> メソッドに null \(Visual Basic では `Nothing`\) を渡すことで、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> メソッドまたは <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName> メソッドの呼び出しで指定されたすべての構成バイトを削除できます。  
  
 構成情報に加えて、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName> メソッドの実装に渡される <xref:System.AppDomainSetup> オブジェクトの設定も変更できます。変更できる設定には、<xref:System.AppDomainSetup.ApplicationBase%2A>、<xref:System.AppDomainSetup.ApplicationName%2A>、<xref:System.AppDomainSetup.CachePath%2A>、<xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、<xref:System.AppDomainSetup.DisallowBindingRedirects%2A>、<xref:System.AppDomainSetup.DisallowCodeDownload%2A>、<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>、<xref:System.AppDomainSetup.DynamicBase%2A>、<xref:System.AppDomainSetup.LoaderOptimization%2A>、<xref:System.AppDomainSetup.PrivateBinPath%2A>、<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>、および <xref:System.AppDomainSetup.ShadowCopyFiles%2A> があります。  
  
 `<disableFusionUpdatesFromADManager>` 要素を使用する代わりに、レジストリ設定を作成するか環境変数を設定して、既定の動作を無効にすることもできます。  レジストリの場合、`HKCU\Software\Microsoft\.NETFramework` または `HKLM\Software\Microsoft\.NETFramework` の下に `COMPLUS_disableFusionUpdatesFromADManager` という名前の DWORD 値を作成し、その値を 1 に設定します。  コマンド ラインの場合、`COMPLUS_disableFusionUpdatesFromADManager` 環境変数を 1 に設定します。  
  
## 使用例  
 次のコード例は、`<disableFusionUpdatesFromADManager>` 要素を使用して、Fusion の設定をオーバーライドする機能を無効にする方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)