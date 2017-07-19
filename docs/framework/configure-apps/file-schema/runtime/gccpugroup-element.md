---
title: "&lt;GCCpuGroup&gt; 要素 | Microsoft Docs"
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
helpviewer_keywords: 
  - "<GCCpuGroup> 要素"
  - "GCCpuGroup 要素"
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;GCCpuGroup&gt; 要素
ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。  
  
## 構文  
  
```  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> ガベージ コレクションが複数の CPU グループをサポートするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ガベージ コレクションは複数の CPU グループをサポートしていません。  これは、既定の設定です。|  
|`true`|ガベージ コレクションは、サーバーのガベージ コレクションが有効な場合に複数の CPU グループをサポートします。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 コンピューターに複数の CPU グループがあり、サーバーのガベージ コレクション \([\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) 要素を参照\) が有効になっている場合、ヒープを作成および分散するときに、ガベージ コレクションが CPU グループ全体に分散し、すべてのコアが考慮されます。  
  
> [!NOTE]
>  この要素は、ガベージ コレクション スレッドにのみ適用されます。  ランタイムが CPU グループ全体にユーザー スレッドを分散できるようにするには、[\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) 要素を有効にする必要があります。  
  
## 使用例  
 次の例は、複数の CPU グループのガベージ コレクションを有効にする方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/ja-jp/ba2c6c67-5778-497c-9fac-5f793b5500c7)   
 [ワークステーションとサーバーのガベージ コレクション](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)