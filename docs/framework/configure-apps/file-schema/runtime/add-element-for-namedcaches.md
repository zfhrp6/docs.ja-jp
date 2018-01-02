---
title: "&lt;追加&gt;要素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0000e92c89920b05e0ffc93fab58fb0bd6ea6b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a>&lt;追加&gt;要素&lt;namedCaches&gt;
追加、`namedCache`エントリを`namedCaches`メモリ キャッシュのコレクション。  
  
 \<system.runtime.caching >  
\<memoryCache >  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>型  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|-|-|  
|`CacheMemoryLimitMegabytes`|許容最大サイズ (メガバイト) 単位を指定する整数値のインスタンス、<xref:System.Runtime.Caching.MemoryCache>まで拡大できます。 既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスのサイズの自動変更ヒューリスティックが既定で使用されます。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|キャッシュで利用できる物理的にインストールされているコンピューターのメモリの最大パーセンテージを指定する整数 0 ~ 100 の値。 既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスのサイズの自動変更ヒューリスティックが既定で使用されます。|  
|`PollingInterval`|時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。 この値は"HH:MM:SS"形式で入力します。|  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。|  
  
## <a name="remarks"></a>コメント  
 `add`要素へのエントリは追加、`namedCaches`メモリ キャッシュのコレクション。 使用することができます、[オフ](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)要素を使用する前に、`add`というコレクション内のキャッシュのあるものがあることの他の要素。 この要素は、machine.config ファイルでは、Web.config ファイルで使用できます。  
  
## <a name="example"></a>例  
 次の例は、既定値の設定を定義する方法を示しています。`namedCache`エントリを、`namedCaches`メモリ キャッシュのコレクション。  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [\<namedCaches > 要素 (キャッシュの設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
