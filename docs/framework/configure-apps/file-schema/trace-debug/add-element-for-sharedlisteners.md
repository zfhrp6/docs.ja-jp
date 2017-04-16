---
title: "&lt;sharedListeners&gt; の &lt;add&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> の <add> 要素"
  - "<sharedListeners> の add 要素"
  - "initializeData 属性"
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;sharedListeners&gt; の &lt;add&gt; 要素
`sharedListeners` コレクションにリスナーを追加します。  `sharedListeners` は、任意の [\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) または [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) が参照できるリスナーのコレクションです。既定では、`sharedListeners` コレクションのリスナーは `Listeners` コレクションに配置されません。  これらは、[\<source\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) または [\<trace\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) に名前で追加する必要があります。  実行時に、`sharedListeners` コレクションのリスナーをコードで取得することはできません。  
  
## 構文  
  
```  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`name`|必須の属性です。<br /><br /> 共有リスナーを `Listeners` コレクションに追加するために使用されるリスナーの名前を指定します。|  
|`type`|必須の属性です。<br /><br /> リスナーの型を指定します。  「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定されている要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性。<br /><br /> 指定したクラスのコンストラクターに渡す文字列。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|フィルターを `sharedListeners` コレクションのリスナーに追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意の source 要素または trace 要素が参照できるリスナーのコレクション。|  
  
## 解説  
 .NET Framework に付属のリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスの派生クラスです。  `name` 属性の値は、トレースまたはトレース ソースの `Listeners` コレクションに共有リスナーを追加するために使用されます。  `initializeData` 属性の値は、作成するリスナーの型によって異なります。  `initializeData` を指定する必要のないトレース リスナーもあります。  
  
> [!NOTE]
>  `initializeData` 属性を使用すると、"initializeData 属性は宣言されていません" というコンパイラの警告が表示される場合があります。この警告は、`initializeData` 属性を認識しない <xref:System.Diagnostics.TraceListener> 抽象基本クラスに対して構成設定が検証されたために発生します。  通常、パラメーターを受け取るコンストラクターのあるトレース リスナーの実装では、この警告を無視してもかまいません。  
  
 .NET Framework に付属するトレース リスナーを次の表に示し、各リスナーの `initializeData` 属性の値を説明します。  
  
|トレース リスナー クラス|initializeData 属性の値|  
|-------------------|-------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。`initializeData` 属性を "`true`" に設定すると、トレース出力とデバッグ出力を標準エラー出力ストリームに書き込みます。"`false`" に設定すると、標準出力ストリームに書き込みます。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<xref:System.Diagnostics.XmlWriterTraceListener> が出力を書き込むファイルの名前。|  
  
## 構成ファイル  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 次の例に `sharedListeners` のコレクションに <xref:System.Diagnostics.TextWriterTraceListener>`textListener` を追加するには `<add>` 要素を使用する方法を示します。`textListener` にトレース ソース `TraceSourceApp`の `Listeners` のコレクションに名前で追加されます。  `textListener` リスナーは、トレース出力を myListener.log ファイルに書き込みます。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## 参照  
 <xref:System.Diagnostics.TraceSource>   
 <xref:System.Diagnostics.TraceListener>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)