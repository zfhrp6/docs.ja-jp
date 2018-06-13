---
title: '&lt;GCCpuGroup&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4461667bdb47d410c857b4ac2c9dd268438a02f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744019"
---
# <a name="ltgccpugroupgt-element"></a>&lt;GCCpuGroup&gt;要素
ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<GCCpuGroup>  
  
## <a name="syntax"></a>構文  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ガベージ コレクションは複数の CPU グループをサポートしていません。 既定値です。|  
|`true`|ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 コンピューターに複数の CPU グループとサーバーのガベージ コレクションが有効になっている (を参照してください、 [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)要素)、この要素を有効にするすべての CPU グループ全体でガベージ コレクションを拡張し、すべてのコアにアカウントを作成すると、ヒープを分散します。  
  
> [!NOTE]
>  この要素は、ガベージ コレクション スレッドにのみ適用されます。 すべての CPU グループにユーザー スレッドを分散するランタイムを有効にする必要がありますも有効にする、 [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)要素。  
  
## <a name="example"></a>例  
 次の例は、複数の CPU グループのガベージ コレクションを有効にする方法を示しています。  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [方法: 同時実行ガベージ コレクションを無効にします。](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [ワークステーションとサーバーのガベージ コレクション](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
