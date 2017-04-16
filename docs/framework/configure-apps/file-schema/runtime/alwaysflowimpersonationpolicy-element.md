---
title: "&lt;alwaysFlowImpersonationPolicy&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<alwaysFlowImpersonationPolicy> 要素"
  - "alwaysFlowImpersonationPolicy 要素"
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;alwaysFlowImpersonationPolicy&gt; 要素
偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間をフローするように指定します。  
  
## 構文  
  
```  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> Windows ID が非同期ポイント間をフローするかどうかを示します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> などのマネージ メソッドを介して偽装が実行されない限り、Windows ID は非同期ポイント間をフローしません。  これは、既定の設定です。|  
|`true`|偽装の実行方法に関係なく、Windows ID は常に非同期ポイント間をフローします。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework Version 1.0 および 1.1 では、Windows ID は非同期ポイント間をフローしません。  一方、.NET Framework Version 2.0 には、現在の実行スレッドに関する情報を格納し、これをアプリケーション ドメイン内の非同期ポイント間でフローさせる <xref:System.Threading.ExecutionContext> オブジェクトがあります。  <xref:System.Security.Principal.WindowsIdentity> も、非同期ポイント間をフローする情報の一部としてフローします。ただし、偽装が <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> などのマネージ メソッドを使用して実行され、ネイティブ メソッドのプラットフォーム呼び出しなど、他の手段によって実行されていない場合に限ります。  この要素を使用して、偽装の実行方法に関係なく、Windows ID が非同期ポイント間をフローするように指定します。  
  
 この既定の動作は、さらに次の 2 つの方法で変更できます。  
  
1.  スレッドごとにマネージ コードを使用する。  
  
     <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName> メソッド、<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> メソッド、または <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName> メソッドを使用して <xref:System.Threading.ExecutionContext> 設定と <xref:System.Security.SecurityContext> 設定を変更すると、スレッドごとにフローを止めることができます。  
  
2.  共通言語ランタイム \(CLR: Common Language Runtime\) を読み込むアンマネージ ホスト インターフェイスの呼び出しを使用する。  
  
     単純なマネージ実行可能ファイルの代わりに、アンマネージ ホスト インターフェイスを使用して CLR を読み込むと、[CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 関数の呼び出しで特別なフラグを指定できます。  プロセス全体の互換モードを有効にするには、[CorBindToRuntimeEx 関数](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) の `flags` パラメーターを STARTUP\_ALWAYSFLOW\_IMPERSONATION に設定します。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## 使用例  
 マネージ メソッド以外の手段によって偽装が実行されている場合でも、Windows ID が非同期ポイント間をフローするように指定する方法を次の例に示します。  
  
```  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<legacyImpersonationPolicy\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)