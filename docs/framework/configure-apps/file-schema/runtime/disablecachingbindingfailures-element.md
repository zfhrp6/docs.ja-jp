---
title: '&lt;disableCachingBindingFailures&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 422888a595e8fdea01f9cb9d256830467d6822ac
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745680"
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt;要素
バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にするかどうかを指定します。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<disableCachingBindingFailures >  
  
## <a name="syntax"></a>構文  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|0|バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にできません。 これは、.NET Framework version 2.0 以降の既定のバインディングの動作です。|  
|1|バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にします。 この設定は、.NET Framework version 1.1 のバインドの動作に戻ります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 以降、.NET Framework version 2.0 では、アセンブリの読み込みの既定の動作をすべてのバインディングと読み込みエラーをキャッシュします。 つまり、アセンブリの読み込みに失敗した場合、同じアセンブリの読み込みに後続の要求は即座に失敗しようとするアセンブリの検索をします。 この要素は、そのアセンブリが調査パスに見つからなかったために発生するエラーをバインドするための既定の動作を無効にします。 このようなエラーをスロー<xref:System.IO.FileNotFoundException>です。  
  
 一部のバインドと障害の読み込みは、この要素の影響は受けませんされ、常にキャッシュされます。 アセンブリが見つかりましたが、読み込むことができないために、このようなエラーが発生します。 スロー<xref:System.BadImageFormatException>または<xref:System.IO.FileLoadException>です。 次の一覧には、このようなエラーの例いくつかにはが含まれています。  
  
-   読み込もうとした場合は、ファイルが有効なアセンブリではない、適切なアセンブリに無効なファイルが置き換えられた場合でも、後続のアセンブリの読み込みは失敗します。  
  
-   ファイル システムによってロックされているアセンブリをロードしようとすると、アセンブリが、ファイル システムによってリリースされた後でも後続のアセンブリの読み込みは失敗します。  
  
-   ロードしようとしているアセンブリの 1 つまたは複数のバージョンは、プローブ パスですが、要求している特定のバージョンはそれらの間にない場合、調査パスに正しいバージョンが移動された場合でもそのバージョンの読み込みに後続の試行は失敗します。  
  
## <a name="example"></a>例  
 次の例では、アセンブリ バインディング エラーを調査して、アセンブリが見つからなかったために発生するのキャッシュを無効にする方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
