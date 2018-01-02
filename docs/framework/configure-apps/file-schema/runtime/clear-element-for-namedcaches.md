---
title: "&lt;オフ&gt;要素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 501371346b3c1496122d93a98eb89dd4afc6bcd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a>&lt;オフ&gt;要素&lt;namedCaches&gt;
すべてを消去`namedCache`内のエントリ、`namedCaches`メモリ キャッシュのコレクション。  
  
 \<system.runtime.caching >  
\<memoryCache >  
\<namedCaches >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>型  
 `Type`  
  
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
 `clear`要素には、すべてを消去`namedCache`メモリ キャッシュの名前付きキャッシュ コレクション内のエントリ。 使用することができます、`clear`要素を使用する前に、`add`があるユーザーが何を特定するために新しい名前付きキャッシュ エントリを追加する要素がコレクション内のキャッシュをという名前です。  
  
## <a name="see-also"></a>参照  
 [\<namedCaches > 要素 (キャッシュの設定)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
