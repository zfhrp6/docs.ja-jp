---
title: "&lt;system.diagnostics&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.diagnostics"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.diagnostics> 要素"
  - "system.diagnostics 要素"
ms.assetid: 3f348f42-fa72-4ff2-aa1c-bb9eecad4bb2
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;system.diagnostics&gt; 要素
メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。  
  
## 構文  
  
```  
<system.diagnostics>   
</system.diagnostics>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<アサート\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。|  
|[\<performanceCounters\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。|  
|[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|任意の source 要素または trace 要素が参照できるリスナーを含みます。  共有リスナーとして識別されたリスナーは、ソースまたはトレースに名前で追加できます。|  
|[\<ソース\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|トレース メッセージを開始するトレース ソースを指定します。|  
|[\<スイッチ\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|トレース スイッチとトレース スイッチを設定するレベルを保持します。|  
|[\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 使用例  
 次の例 **\<system.diagnostics\>** 要素内のトレース スイッチおよびトレース リスナーを埋め込む方法について説明します。  `General` トレース スイッチは、[TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) レベルに設定されています。  トレース リスナー `myListener` は、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、テキストを使用してスイッチの値を指定できます。  たとえば、<xref:System.Diagnostics.BooleanSwitch> に `true` を指定したり、`Error` などの列挙値を表すテキストを <xref:System.Diagnostics.TraceSwitch> に使用したりできます。  `<add name="myTraceSwitch" value="Error" />` 行は、`<add name="myTraceSwitch" value="1" />` に相当します。  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
      </switches>  
      <trace autoflush="true" indentsize="2">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="MyListener.log" traceOutputOptions="ProcessId, LogicalOperationStack, Timestamp, ThreadId, Callstack, DateTime" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)