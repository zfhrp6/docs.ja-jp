---
title: '&lt;alwaysFlowImpersonationPolicy&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cc704bbf8631936dbbeb3539ea5ed0d8499f378
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752274"
---
# <a name="ltalwaysflowimpersonationpolicygt-element"></a>&lt;alwaysFlowImpersonationPolicy&gt;要素
偽装の実行方法に関係なく、Windows ID が常に非同期ポイント間でフローすることを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<alwaysFlowImpersonationPolicy>  
  
## <a name="syntax"></a>構文  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> Windows id が非同期ポイント間をフローするかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|管理されているメソッドをなど、Windows のユーザーでは、使用して、権限の借用が実行しない限り、非同期ポイント間フローしません<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>です。 既定値です。|  
|`true`|権限借用の実行方法に関係なく、非同期ポイント間では、Windows id が常にフローします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework バージョン 1.0 および 1.1 では、Windows id は非同期ポイント間をフローしません。 .NET Framework version 2.0 では、<xref:System.Threading.ExecutionContext>オブジェクトを現在実行中のスレッドに関する情報を格納し、アプリケーション ドメイン内での非同期ポイント間をフローします。 <xref:System.Security.Principal.WindowsIdentity>またメソッドの管理ポイント間をフロー、非同期を使用して、権限の借用が達成された提供情報の一部としてフローなど<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>プラットフォームなどの他の方法ではなく、ネイティブ メソッドを呼び出すとします。 この要素を使用してを Windows id 偽装の実行方法に関係なく、非同期ポイント間をフローするを指定します。  
  
 他の 2 つの方法でこの既定の動作を変更することができます。  
  
1.  スレッドごとにマネージ コード。  
  
     スレッドごとのフローを抑制するには変更することによって、<xref:System.Threading.ExecutionContext>と<xref:System.Security.SecurityContext>設定を使用して、 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>、または<xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>メソッドです。  
  
2.  呼び出しで、アンマネージ ホスト インターフェイスを共通言語ランタイム (CLR) を読み込めません。  
  
     呼び出しで特別なフラグを指定できます (単純なマネージ実行可能ファイル) ではなく、アンマネージ ホスト インターフェイスが、CLR の読み込みに使用されている場合、 [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数。 プロセス全体の互換モードを有効にするには設定、`flags`パラメーター [CorBindToRuntimeEx 関数](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)に`STARTUP_ALWAYSFLOW_IMPERSONATION`です。  
  
## <a name="configuration-file"></a>構成ファイル  
 .NET Framework アプリケーションでこの要素は、アプリケーション構成ファイルでのみ使用できます。  
  
 内で見つかった aspnet.config ファイルで、ASP.NET アプリケーションの権限借用のフローを構成できます、 \<Windows フォルダー > \Microsoft.NET\Framework\vx.x.xxxx ディレクトリ。  
  
 既定では ASP.NET には、次の構成設定を使用して、aspnet.config ファイルで、権限借用フローが無効にします。  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 ASP.NET では、代わりに、権限借用のフローを許可したい場合必要があります明示的に使用する次の構成設定。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例では、Windows id は、マネージ メソッド以外の方法で、権限の借用を実現する場合でも、非同期ポイント間でフローを指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<legacyImpersonationPolicy > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
