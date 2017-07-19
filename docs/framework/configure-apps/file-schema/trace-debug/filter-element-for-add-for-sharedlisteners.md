---
title: "&lt;sharedListeners&gt; の &lt;add&gt; の &lt;filter&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> の <add> の <filter> 要素"
  - "<sharedListeners> の <add> の filter 要素"
  - "フィルター, トレース リスナー"
  - "initializeData 属性"
  - "トレース リスナー, フィルター"
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# &lt;sharedListeners&gt; の &lt;add&gt; の &lt;filter&gt; 要素
フィルターを `sharedListeners` コレクションのリスナーに追加します。  
  
## 構文  
  
```  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**type**|必須の属性です。<br /><br /> フィルターの型を指定します。  型の完全名 \(<xref:System.Type.FullName%2A?displayProperty=fullName> プロパティの形式\) のみ使用できます。または、アセンブリ情報を含む完全修飾型名 \(<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> プロパティの形式\) を使用することもできます。  完全修飾型名の作成の詳細については、「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。|  
|**initializeData**|省略可能な属性。<br /><br /> 指定したクラスのコンストラクターに渡す文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sharedListeners`|任意の source 要素または trace 要素が参照できるリスナーのコレクション。|  
|`add`|**sharedListeners** コレクションにリスナーを追加します。|  
  
## 解説  
 リスナーが `<sharedListeners>` 要素の `<add>` 要素で定義されている場合、そのリスナーのフィルターは `<add>` 要素の子である `<filter>` 要素で定義する必要があります。  
  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 `<filter>` 要素を使用してフィルターを `sharedListeners` コレクション内のトレース リスナー `console` に追加する方法を次の例に示します。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.TraceFilter>   
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.TraceSource>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)