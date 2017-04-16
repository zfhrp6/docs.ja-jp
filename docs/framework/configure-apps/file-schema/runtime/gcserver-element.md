---
title: "&lt;gcServer&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<gcServer> 要素"
  - "gcServer 要素"
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;gcServer&gt; 要素
共通言語ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。  
  
## 構文  
  
```  
<gcServer    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがサーバーのガベージ コレクションを実行するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|サーバーのガベージ コレクションを実行しません。  既定値です。|  
|`true`|サーバーのガベージ コレクションを実行します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 共通言語ランタイム \(CLR\) は、2 種類のガベージ コレクションをサポートしています。1 つはワークステーション ガベージ コレクションで、すべてのシステムで使用できるものです。もう 1 つはサーバー ガベージ コレクションで、マルチプロセッサ システムで使用できるものです。  `<gcServer>` 要素を使用して、CLR によって実行されるガベージ コレクションの種類を制御します。  <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=fullName> プロパティを使用して、サーバー ガベージ コレクションが有効かどうかを決定します。  
  
 シングル プロセッサ コンピューターの場合、既定のワークステーション ガベージ コレクションが催促のオプションです。  2 つのプロセッサを搭載するコンピューターで、ワークステーションかサーバーのいずれかを使用できます。  3 つ以上のプロセッサでは、サーバー ガベージ コレクションが最速のオプションです。  
  
 この要素は、アプリケーション構成ファイルでのみ使用できます。要素がマシン構成ファイルにある場合には無視されます。  
  
> [!NOTE]
>  .NET Framework 4 以前のバージョンでは、サーバー ガベージ コレクションを有効にすると同時実行ガベージ コレクションが使用できません。  [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 以降では、サーバー ガベージ コレクションは同時実行されるようになりました。  非同時実行サーバー ガベージ コレクションを使用するには、`<gcServer>` 要素を `true` に設定し、[\<gcConcurrent\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)を `false` に設定します。  
  
## 使用例  
 サーバー ガベージ コレクションを有効にする方法を次の例に示します。  
  
```  
  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
  
```  
  
## 参照  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=fullName>   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/ja-jp/ba2c6c67-5778-497c-9fac-5f793b5500c7)