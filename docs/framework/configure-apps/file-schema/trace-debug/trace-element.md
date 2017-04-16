---
title: "&lt;trace&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#trace"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> 要素"
  - "リスナー"
  - "trace 要素"
  - "トレース リスナー, <trace> 要素"
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;trace&gt; 要素
トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。  
  
## 構文  
  
```  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`autoflush`|省略可能な属性。<br /><br /> トレース リスナーが毎回の書き込み操作の後で出力バッファーを自動的にフラッシュするかどうかを指定します。|  
|`indentsize`|省略可能な属性。<br /><br /> インデントするスペース数を指定します。|  
|`useGlobalLock`|省略可能な属性。<br /><br /> グローバル ロックを使用する必要があるかどうかを示します。|  
  
## autoflush 属性  
  
|値|説明|  
|-------|--------|  
|`false`|出力バッファーを自動的にフラッシュしません。  これは、既定の設定です。|  
|`true`|出力バッファーを自動的にフラッシュします。|  
  
## useGlobalLock 属性  
  
|値|説明|  
|-------|--------|  
|`false`|リスナーがスレッド セーフである場合は、グローバル ロックを使用しません。それ以外の場合は、グローバル ロックを使用します。|  
|`true`|リスナーがスレッド セーフかどうかにかかわらず、グローバル ロックを使用します。  これは、既定の設定です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<リスナー\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## 使用例  
 `<trace>` 要素を使用して、リスナー `MyListener` を `Listeners` コレクションに追加する方法を次の例に示します。  `MyListener` は、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。  `useGlobalLock` 属性には `false` を設定します。これにより、トレース リスナーがスレッド セーフの場合は、グローバル ロックが使用されなくなります。  `autoflush` 属性には `true` を設定します。これにより、<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=fullName> メソッドが呼び出されるかどうかに関係なく、トレース リスナーからファイルに出力が書き込まれます。  `indentsize` 属性には 0 \(ゼロ\) を設定します。これにより、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=fullName> メソッドが呼び出されたときに、リスナーは 0 個のスペースをインデントします。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.DefaultTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)