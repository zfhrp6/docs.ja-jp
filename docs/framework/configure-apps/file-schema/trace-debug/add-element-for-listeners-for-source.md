---
title: "&lt;source&gt; の &lt;listeners&gt; の &lt;add&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> の <listeners> の <add> 要素"
  - "<source> の <listeners> の add 要素"
  - "initializeData 属性"
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;source&gt; の &lt;listeners&gt; の &lt;add&gt; 要素
トレース ソース用の `Listeners` コレクションにリスナーを追加します。  
  
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
|`type`|必須の属性です。<br /><br /> リスナーの型を指定します。  「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」で指定されている要件を満たす文字列を使用する必要があります。|  
|`initializeData`|省略可能な属性。<br /><br /> 指定したクラスのコンストラクターに渡す文字列。  文字列を受け取るコンストラクターがクラスにない場合は、<xref:System.Configuration.ConfigurationException> がスローされます。|  
|`name`|省略可能な属性。<br /><br /> リスナーの名前を指定します。|  
|`traceOutputOptions`|省略可能な属性。<br /><br /> トレース リスナーの <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> プロパティ値を指定します。|  
|\[カスタム属性\]|省略可能な属性です。<br /><br /> このリスナーの <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> メソッドで識別されるリスナー固有の属性の値を指定します。  <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> は、<xref:System.Diagnostics.DelimitedListTraceListener> クラスに固有の追加属性の例です。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<filter\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|トレース ソースの `Listeners` コレクション内のリスナーにフィルターを追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
|`source`|トレース メッセージを開始するトレース ソースを指定します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。|  
  
## 解説  
 .NET Framework に付属のリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスの派生クラスです。  
  
 トレース リスナーの `name` 属性を指定しない場合は、トレース リスナーの <xref:System.Diagnostics.TraceListener.Name%2A> プロパティは、既定で空の文字列 \(""\) に設定されます。  アプリケーションにリスナーが 1 つしかない場合、名前を指定しなくてもリスナーを追加でき、名前に空の文字列を指定してリスナーを削除できます。  ただし、アプリケーションに複数のリスナーがある場合は、各トレース リスナーの一意の名前を指定する必要があります。これにより、<xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=fullName> コレクション内の個別のトレース リスナーを識別および管理できます。  
  
> [!NOTE]
>  同じ名前を持つ同じ型のトレース リスナーを複数追加すると、その型と名前を持つトレース リスナーが 1 つだけ `Listeners` コレクションに追加されます。  ただし、プログラムを使用すると、複数の同一のリスナーを `Listeners` コレクションに追加できます。  
  
 `initializeData` 属性の値は、作成するリスナーの型によって異なります。  `initializeData` を指定する必要のないトレース リスナーもあります。  
  
> [!NOTE]
>  `initializeData` 属性を使用すると、"initializeData 属性は宣言されていません" というコンパイラの警告が表示される場合があります。この警告は、`initializeData` 属性を認識しない <xref:System.Diagnostics.TraceListener> 抽象基本クラスに対して構成設定が検証されたために発生します。  通常、パラメーターを受け取るコンストラクターのあるトレース リスナーの実装では、この警告を無視してもかまいません。  
  
 .NET Framework に付属するトレース リスナーを次の表に示し、各リスナーの `initializeData` 属性の値を説明します。  
  
|トレース リスナー クラス|initializeData 属性の値|  
|-------------------|-------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> コンストラクターの `useErrorStream` 値。`initializeData` 属性を "`true`" に設定すると、トレース出力とデバッグ出力を標準エラー出力ストリームに書き込みます。"`false`" に設定すると、標準出力ストリームに書き込みます。|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.DelimitedListTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName>|既存のイベント ログ ソースの名前。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.EventSchemaTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.TextWriterTraceListener> が出力を書き込むファイルの名前。|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName>|<xref:System.Diagnostics.XmlWriterTraceListener> が出力を書き込むファイルの名前。|  
  
## 構成ファイル  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 `<add>` 要素を使用して、リスナー `console` および `textListener` をトレース リソース `TraceSourceApp` の `Listeners` コレクションに追加する方法を次の例に示します。  `textListener` リスナーは、トレース出力を myListener.log ファイルに書き込みます。  
  
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