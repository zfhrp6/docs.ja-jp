---
title: '&lt;PreferComInsteadOfManagedRemoting&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cac4ebb46fabad49e2e4e6a7d566522ca027094
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745475"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;PreferComInsteadOfManagedRemoting&gt;要素
かどうか、ランタイムを使用して COM 相互運用機能リモート処理ではなく呼び出しは、すべてのアプリケーション ドメインの境界を越えてを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<PreferComInsteadOfManagedRemoting >  
  
## <a name="syntax"></a>構文  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムは COM 相互運用機能のリモート処理ではなくアプリケーション ドメインの境界を越えて使用するかどうかを示します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムは、アプリケーション ドメインの境界を越えて、リモート処理を使用します。 既定値です。|  
|`true`|ランタイムは、アプリケーション ドメインの境界を越えて COM 相互運用機能を使用します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 設定すると、`enabled`属性を`true`ランタイムが次のように動作します。  
  
-   ランタイムは呼び出しません[iunknown::queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)の[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)インターフェイスの場合、 [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003)インターフェイスが COM インターフェイスを使用してドメインを入力します。 代わりに、構築、[ランタイム呼び出し可能ラッパー](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) オブジェクトの周りです。  
  
-   受信すると、ランタイムは E_NOINTERFACE を返します、`QueryInterface`を呼び出して、 [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)のいずれかのインターフェイス[COM 呼び出し可能ラッパー](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) このドメインで作成されました。  
  
 これら 2 つの動作では、COM 経由でのすべての呼び出しがアプリケーション ドメインの境界を使用して COM を越えてマネージ オブジェクトとリモート処理ではなく COM 相互運用機能間でやり取りすることを確認します。  
  
## <a name="example"></a>例  
 次の例では、分離の境界を越えて相互運用、ランタイムで COM を使用するように指定する方法を示します。  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
