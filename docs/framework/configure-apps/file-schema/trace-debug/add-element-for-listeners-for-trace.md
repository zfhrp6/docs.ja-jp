---
title: "&lt;trace&gt; の &lt;listeners&gt; の &lt;add&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<listeners> の <add> 要素"
  - "<listeners> の add 要素"
  - "initializeData 属性"
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 24
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;trace&gt; の &lt;listeners&gt; の &lt;add&gt; 要素
**Listeners** コレクションにリスナーを追加します。  
  
## 構文  
  
```  
<add name="name"   
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**type**|必須の属性です。<br /><br /> リスナーの型を指定します。  「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」に指定されている要件に合った文字列を使用する必要があります。|  
|**initializeData**|省略可能な属性。<br /><br /> 指定したクラスのコンストラクターに渡す文字列。|  
|**name**|省略可能な属性。<br /><br /> リスナーの名前を指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|トレース用の `Listeners` コレクションのリスナーにフィルターに追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。  リスナーは、トレース出力を適切なターゲットに転送します。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
## 解説  
 <xref:System.Diagnostics.Debug> クラスおよび <xref:System.Diagnostics.Trace> クラスは、同じ **Listeners** コレクションを共有します。  これらのクラスの一方のコレクションにリスナー オブジェクトを追加すると、もう一方のクラスは同じリスナーを使用します。  リスナー クラスは、[TraceListener クラス](frlrfSystemDiagnosticsTraceListenerClassTopic)の派生クラスです。  
  
 トレース リスナーの `name` 属性を指定しない場合は、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> は、既定で空の文字列 \(""\) に設定されます。  アプリケーションにリスナーが 1 つしかない場合、名前を指定しなくてもリスナーを追加でき、名前に空の文字列を指定してリスナーを削除できます。  ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーの一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.Debug.Listeners%2A> および <xref:System.Diagnostics.Trace.Listeners%2A> コレクション内の個別のトレース リスナーを識別および管理できます。  
  
> [!NOTE]
>  同じ名前を持つ同じ型のトレース リスナーを複数追加すると、その型と名前を持つトレース リスナーが 1 つだけ `Listeners` コレクションに追加されます。  ただし、プログラムを使用すると、複数の同一のリスナーを `Listeners` コレクションに追加できます。  
  
 **initializeData** 属性の値は、作成するリスナーの型によって異なります。  **initializeData** を指定する必要のないトレース リスナーもあります。  
  
> [!NOTE]
>  `initializeData` 属性を使用すると、"initializeData 属性は宣言されていません" というコンパイラの警告が表示される場合があります。この警告は、`initializeData` 属性を認識しない <xref:System.Diagnostics.TraceListener> 抽象基本クラスに対して構成設定が検証されたために発生します。  通常、パラメーターを受け取るコンストラクターのあるトレース リスナーの実装では、この警告を無視してもかまいません。  
  
 .NET Framework に付属するトレース リスナーを次の表に示し、各リスナーの **initializeData** 属性の値を説明します。  
  
|トレース リスナー クラス|initializeData 属性の値|  
|-------------------|-------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。`initializeData` 属性を "`true`" に設定すると、トレースとデバッグの出力を <xref:System.Console.Error%2A?displayProperty=fullName> に書き込みます。"`false`" に設定すると、<xref:System.Console.Out%2A?displayProperty=fullName> に書き込みます。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.XmlWriterTraceListener> が出力を書き込むファイルの名前。|  
  
## 使用例  
 次の例に **リスナー** のコレクションにリスナーを追加するには `MyListener` と `MyEventListener`**\<追加\>** 要素を使用する方法を示します。  `MyListener` は、`MyListener.log` というファイルを作成し、そのファイルに出力を書き込みます。  `MyEventListener` は、イベント ログにエントリを作成します。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 <xref:System.Diagnostics.ConsoleTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)