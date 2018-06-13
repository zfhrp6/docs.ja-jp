---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744617"
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a>&lt;legacyCorruptedStateExceptionsPolicy&gt;要素
共通言語ランタイムにアクセス違反およびその他の破損状態例外をキャッチするマネージ コードができるかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<legacyCorruptedStateExceptionsPolicy >  
  
## <a name="syntax"></a>構文  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> アプリケーションがキャッチすることを指定の破損状態例外エラー アクセス違反などです。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|アプリケーションは検出されません破損状態例外エラー アクセス違反などです。 既定値です。|  
|`true`|アプリケーションがキャッチ破損状態例外エラー アクセス違反などです。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 .NET Framework バージョン 3.5 以前では、共通言語ランタイムは、破損しているプロセスの状態で発生した例外をキャッチするマネージ コードを許可します。 アクセス違反は、この種類の例外の例を示します。  
  
 以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、マネージ コードが不要になったこれらの型の例外をキャッチ`catch`ブロックします。 ただし、この変更をオーバーライドして、2 つの方法で破損状態例外の処理を維持できます。  
  
-   設定、`<legacyCorruptedStateExceptionsPolicy>`要素の`enabled`属性を`true`です。 この構成設定は適用されているプロセスであり、すべてのメソッドに影響します。  
  
 - または -  
  
-   適用、<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>属性、例外が含まれるメソッドを`catch`ブロックします。  
  
 この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]およびそれ以降。  
  
## <a name="example"></a>例  
 次の例は、アプリケーションは前に、の動作を戻すかを指定する方法を示しています、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]、およびすべての破損状態例外のエラーをキャッチします。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
