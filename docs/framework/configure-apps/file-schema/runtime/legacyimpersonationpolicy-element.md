---
title: "&lt;legacyImpersonationPolicy&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<legacyImpersonationPolicy> 要素"
  - "legacyImpersonationPolicy 要素"
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;legacyImpersonationPolicy&gt; 要素
現在のスレッドの実行コンテキストのフロー設定に関係なく、Windows ID が非同期ポイント間をフローしないように指定します。  
  
## 構文  
  
```  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> 現在のスレッドの <xref:System.Threading.ExecutionContext> フロー設定に関係なく、<xref:System.Security.Principal.WindowsIdentity> が非同期ポイント間をフローしないように指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|現在のスレッドの <xref:System.Threading.ExecutionContext> フロー設定に基づいて、<xref:System.Security.Principal.WindowsIdentity> が非同期ポイント間をフローします。  これは、既定の設定です。|  
|`true`|現在のスレッドの <xref:System.Threading.ExecutionContext> フロー設定に関係なく、<xref:System.Security.Principal.WindowsIdentity> は非同期ポイント間をフローしません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework Version 1.0 および 1.1 では、<xref:System.Security.Principal.WindowsIdentity> はユーザー定義の非同期ポイント間をフローしません。  一方、.NET Framework Version 2.0 には、現在の実行スレッドに関する情報を格納し、これをアプリケーション ドメイン内の非同期ポイント間でフローさせる <xref:System.Threading.ExecutionContext> オブジェクトがあります。  <xref:System.Security.Principal.WindowsIdentity> も、非同期ポイント間をフローする情報の一部としてフローします。つまり、偽装コンテキストが終了した場合でもフローします。  この要素は、<xref:System.Security.Principal.WindowsIdentity> が非同期ポイント間をフローしないように指定するために使用されます。  
  
> [!NOTE]
>  共通言語ランタイム \(CLR: Common Language Runtime\) は、マネージ コードのみを使用して実行される偽装操作を認識し、アンマネージ コードに対するプラットフォーム呼び出しや Win32 関数に対する直接呼び出しなどを通じてマネージ コードの外部で実行される偽装は認識しません。  `alwaysFlowImpersonationPolicy` 要素が true に設定 \(`<alwaysFlowImpersonationPolicy enabled="true"/>`\) されていない場合は、マネージ <xref:System.Security.Principal.WindowsIdentity> オブジェクトのみが非同期ポイント間をフローできます。  `alwaysFlowImpersonationPolicy` を true に設定すると、偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間をフローするように指定されます。  非同期ポイント間のアンマネージ偽装のフローの詳細については、「[\<alwaysFlowImpersonationPolicy\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)」を参照してください。  
  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
 この既定の動作は、さらに次の 2 つの方法で変更できます。  
  
1.  スレッドごとにマネージ コードを使用する。  
  
     <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName> メソッド、<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> メソッド、または <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName> メソッドを使用して <xref:System.Threading.ExecutionContext> 設定と <xref:System.Security.SecurityContext> 設定を変更すると、スレッドごとにフローを止めることができます。  
  
2.  共通言語ランタイム \(CLR: Common Language Runtime\) を読み込むアンマネージ ホスト インターフェイスの呼び出しを使用する。  
  
     単純なマネージ実行可能ファイルの代わりに、アンマネージ ホスト インターフェイスを使用して CLR を読み込むと、[CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 関数の呼び出しで特別なフラグを指定できます。  プロセス全体の互換モードを有効にするには、[CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) の `flags` パラメーターを STARTUP\_LEGACY\_IMPERSONATION に設定します。  
  
## 使用例  
 非同期ポイント間で Windows ID をフローしないレガシ動作を指定する方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)