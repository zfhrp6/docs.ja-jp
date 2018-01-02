---
title: "&lt;削除&gt;要素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;削除&gt;要素&lt;namedCaches&gt;
名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。  
  
 \<system.runtime.caching >  
\<memoryCache >  
\<namedCaches >  
\<削除 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>型  
 `None`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 `None`  
  
### <a name="child-elements"></a>子要素  
 `None`  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。|  
  
## <a name="remarks"></a>コメント  
 `remove`要素を削除して、`namedCache`メモリ キャッシュの名前付きキャッシュのコレクションから入力します。  
  
## <a name="see-also"></a>参照  
 [\<namedCaches > 要素 (キャッシュの設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
