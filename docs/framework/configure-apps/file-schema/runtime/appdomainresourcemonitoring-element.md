---
title: "&lt;appDomainResourceMonitoring&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58caa7458d96ca7bb9088b607a83b2d6be667cae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a>&lt;appDomainResourceMonitoring&gt;要素
プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。  
  
 \<configuration>  
\<ランタイム >  
\<appDomainResourceMonitoring >  
  
## <a name="syntax"></a>構文  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがアプリケーション ドメインのリソースの監視に関する統計を収集するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|アプリケーション ドメインのリソース監視の統計情報が収集されます。|  
|`false`|アプリケーション ドメインのリソース監視の統計情報が収集されません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 ホストしている、管理対象のアプリケーション ドメイン クラスを通じて利用できるがアプリケーション ドメインのリソース監視[ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)インターフェイス、およびイベント トレース for Windows (ETW)。 監視を有効にすると、すべてのアプリケーション ドメイン、プロセスの有効期間のプロセスの統計が収集されます。  
  
 マネージ コードからの監視を有効にするには、<xref:System.AppDomain.MonitoringIsEnabled%2A>プロパティです。  
  
 この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]およびそれ以降。  
  
## <a name="example"></a>例  
 次の例では、アプリケーション ドメインのリソース監視を有効にする方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
