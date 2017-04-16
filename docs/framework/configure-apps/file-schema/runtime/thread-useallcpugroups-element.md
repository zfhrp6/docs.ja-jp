---
title: "&lt;Thread_UseAllCpuGroups&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;Thread_UseAllCpuGroups&gt; 要素
ランタイムによって、すべての CPU グループにマネージ スレッドを分散するかどうかを指定します。  
  
## 構文  
  
```vb  
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムによって、すべての CPU グループにマネージ スレッドを分散するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ランタイムは、複数の CPU グループにマネージ スレッドを分散しません。  これは、既定の設定です。|  
|`true`|コンピューターに複数の CPU グループがあり、[\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 要素が有効になっている場合、ランタイムは、複数の CPU グループにマネージ スレッドを分散します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 コンピューターに複数の CPU グループがある場合、この要素を有効にすると、ランタイムは、すべての CPU グループにマネージ スレッドを分散します。  この機能を使用するには、すべての CPU のグループにガベージ コレクションを拡張し、ヒープの作成時および調整時にすべてのコアを考慮する [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 要素も有効にする必要があります。  [\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) 要素を有効にするには、[\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) 要素も有効にする必要があります。  これらの要素が有効でない場合、`<Thread_UseAllCpuGroups>` 要素を有効にしても効力はありません。  
  
## 使用例  
 次の例は、複数の CPU グループのサポートを有効にする方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<GCCpuGroup\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)