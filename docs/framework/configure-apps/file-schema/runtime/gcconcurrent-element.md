---
title: "&lt;gcConcurrent&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<gcConcurrent> 要素"
  - "コンテナー タグ, <gcConcurrent> 要素"
  - "gcConcurrent 要素"
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# &lt;gcConcurrent&gt; 要素
共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。  
  
## 構文  
  
```  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|ガベージ コレクションを並列に実行しません。|  
|`true`|ガベージ コレクションを並列に実行します。  既定値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework 4 より前の場合、ワークステーション ガベージ コレクションは、同時実行ガベージ コレクションをサポートしており、別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。  .NET Framework 4 では同時実行ガベージ コレクションはバックグラウンド GC に置き換えられており、これも別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。  .NET Framework 4.5 以降では、バックグラウンド コレクションをサーバー ガベージ コレクションで使用できるようになりました。  `<gcConcurrent>` 要素は、ランタイムが同時実行ガベージ コレクションを実行するかバックグラウンド ガベージ コレクションを実行するか \(使用可能な場合\)、またはフォアグラウンドでガベージ コレクションを実行するかどうかを制御します。  
  
> [!WARNING]
>  .NET Framework 4 以降では、同時実行ガベージ コレクションはバックグラウンド ガベージ コレクションに置き換えられています。  *同時実行*と*バックグラウンド*という用語は、.NET Framework ドキュメントでは同義です。  バックグラウンド ガベージ コレクションを無効にするには、この記事説明されているように `<gcConcurrent>` 要素を使用します。  
  
 既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。  アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。  `<gcConcurrent>` 要素の `enabled` 属性を `false` に設定すると、ランタイムは非同時実行ガベージ コレクションを使用します。これはスループットについて最適化されています。  次の構成ファイルはバック グラウンド ガベージ コレクションを無効にします。  
  
```xml  
  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
  
```  
  
 マシン構成ファイルに `<gcConcurrentSetting>` 設定が存在する場合、すべての .NET Framework アプリケーションの既定値を定義します。  マシン構成ファイルの設定は、アプリケーション構成ファイルの設定を上書きします。  
  
 同時実行ガベージ コレクションおよびバックグラウンド ガベージ コレクションの詳細については、「[Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md)」トピックの「同時実行ガベージ コレクション」セクションを参照してください。  
  
## 使用例  
 同時実行ガベージ コレクションを有効にする方法を次の例に示します。  
  
```  
  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md)