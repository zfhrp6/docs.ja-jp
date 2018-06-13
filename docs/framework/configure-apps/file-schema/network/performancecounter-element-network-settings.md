---
title: '&lt;performanceCounter&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5879614fd34fe645899f1b95f41e9b0675418292
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742638"
---
# <a name="ltperformancecountergt-element-network-settings"></a>&lt;performanceCounter&gt;要素 (ネットワーク設定)
有効またはネットワークのパフォーマンス カウンターを無効にします。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<performanceCounters>  
  
## <a name="syntax"></a>構文  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|ネットワークのパフォーマンス カウンターが有効になっているかどうかを指定します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[settings](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>コメント  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
 ネットワーク パフォーマンス カウンターは、使用される構成ファイルで有効になっている必要があります。 すべてのネットワーク パフォーマンス カウンターは、構成ファイル内の 1 つの設定で有効または無効にされます。 ネットワーク パフォーマンス カウンターを個別に有効または無効にすることはできません。 特定のネットワークのパフォーマンス カウンターの詳細については、次を参照してください。[ネットワーク パフォーマンス カウンター](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)です。  
  
 既定値は、そのネットワークのパフォーマンス カウンターが無効です。  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、**有効になっている**該当する構成ファイルからの属性です。  
  
## <a name="example"></a>例  
 次の例は、構成する方法を示します、<xref:System.Net>および関連名前空間をネットワークのパフォーマンス カウンターを有効にします。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [ネットワーク パフォーマンス カウンター](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
