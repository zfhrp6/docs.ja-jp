---
title: '&lt;Directives&gt; 要素 (.NET ネイティブ)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd571255f924c9f3878c00a2bc01397d63e6d777
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394447"
---
# <a name="ltdirectivesgt-element-net-native"></a>&lt;Directives&gt; 要素 (.NET ネイティブ)
[!INCLUDE[net_native](../../../includes/net-native-md.md)]のすべてのランタイム ディレクティブ ファイルのルート要素です。  
  
 **\<ディレクティブ xmlns ="http://schemas.microsoft.com/netfx/2013/01/metadata">**  
  
## <a name="syntax"></a>構文  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`xmlns`|XML 名前空間。 その値は常に **"http://schemas.microsoft.com/netfx/2013/01/metadata"** です。|  
  
## <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|リフレクションで使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にメタデータを必要とする子型と型のメンバーを持つアセンブリを定義します。|  
  
## <a name="remarks"></a>コメント  
 各ランタイム ディレクティブ ファイルには、`<Directives>` 要素を 1 つのみ含めることができます。  
  
 `<Directives>` 要素には、0 または 1 個の [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素と、0 個以上の [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素を含めることができます。  
  
## <a name="see-also"></a>関連項目  
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
