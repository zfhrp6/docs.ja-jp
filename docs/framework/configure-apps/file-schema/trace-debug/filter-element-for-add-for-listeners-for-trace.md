---
title: "&lt;trace&gt; の &lt;listeners&gt; の &lt;add&gt; の &lt;filter&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<filter> 要素 (<trace> の <listeners> の <add>)"
  - "filter 要素 (<trace> の <listeners> の <add>)"
  - "initializeData 属性"
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;trace&gt; の &lt;listeners&gt; の &lt;add&gt; の &lt;filter&gt; 要素
トレース用の `Listeners` コレクションのリスナーにフィルターに追加します。  
  
## 構文  
  
```  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`type`|必須の属性です。<br /><br /> <xref:System.Diagnostics.TraceFilter> クラスを継承するフィルターの型を指定します。  指定する型の <xref:System.Type.FullName%2A> プロパティに対応する型の名前空間修飾名を使用するか、<xref:System.Type.AssemblyQualifiedName%2A> プロパティに対応する、アセンブリ情報を含む完全修飾型名を使用できます。  完全修飾型名については、「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。|  
|`initializeData`|省略可能な属性。<br /><br /> 指定したフィルター クラスのコンストラクターに渡す文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを保持します。  リスナーは、トレース出力を適切なターゲットに転送します。|  
|`add`|`Listeners` コレクションにリスナーを追加します。|  
  
## 解説  
 `<filter>` 要素は、[\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md) で定義されているリスナーの名前だけでなく、リスナーの型を指定するトレース リスナーの `<add>` 要素に含まれている必要があります。  リスナーが [\<sharedListeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md) で定義されている場合は、そのリスナーのフィルターをその要素内で定義する必要があります。  
  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 `<filter>`  要素を使用して、トレースのための `Listeners` コレクション内のリスナー `console` にフィルターを追加する方法を次の例に示します。フィルター イベント レベルは、`Error` として指定します。  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.TraceFilter>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)