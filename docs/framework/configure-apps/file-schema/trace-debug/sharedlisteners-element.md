---
title: "&lt;sharedListeners&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<sharedListeners> 要素"
  - "リスナー"
  - "共有リスナー"
  - "sharedListeners 要素"
  - "トレース リスナー, <sharedListeners> 要素"
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;sharedListeners&gt; 要素
任意の source 要素または trace 要素が参照できるリスナーを含みます。既定では、これらのリスナーはトレースを受け取りません。また、実行時にこれらのリスナーを取得することはできません。  共有リスナーとして識別されたリスナーは、ソースまたはトレースに名前で追加できます。  
  
## 構文  
  
```  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|`sharedListeners` コレクションにリスナーを追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`Configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## 解説  
 リスナーを共有リスナーのコレクションに追加しても、アクティブなリスナーにはなりません。  リスナーをさらにその trace 要素の `Listeners` コレクションに追加することによって、トレース ソースまたはトレースに追加する必要があります。  .NET Framework のリスナー クラスは、<xref:System.Diagnostics.TraceListener> クラスの派生クラスです。  
  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 `<sharedListeners>` 要素を使用して、リスナー `console` を<xref:System.Diagnostics.TraceSource> クラスと <xref:System.Diagnostics.Trace> クラスの `Listeners` コレクションに追加する方法を次の例に示します。  コンソール トレース リスナーは、<xref:System.Diagnostics.TraceSource> または <xref:System.Diagnostics.Trace> の呼び出しを通じて、トレース情報をコンソールに書き込みます。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## 参照  
 <xref:System.Diagnostics.TraceListener>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)