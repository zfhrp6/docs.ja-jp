---
title: "&lt;source&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#source"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> 要素"
  - "source 要素"
ms.assetid: ecf86505-735d-4844-aaba-266fdd134218
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;source&gt; 要素
トレース メッセージを開始するトレース ソースを指定します。  
  
## 構文  
  
```  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`name`|省略可能な属性。<br /><br /> トレース ソースの名前を指定します。|  
|`switchName`|省略可能な属性。<br /><br /> アプリケーション内のトレース スイッチ インスタンスの名前を指定します。  スイッチが `<switches>` 要素で識別されていない場合、値はスイッチのレベルを指定します。|  
|`switchType`|省略可能な属性。<br /><br /> トレース スイッチの型を指定します。  型が存在する場合、その型は有効なクラス名である必要があり、空の文字列にはできません。|  
|`extraAttribute`|省略可能な属性。<br /><br /> トレース ソースの <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> メソッドによって識別されるそのトレース ソース固有の属性の値を指定します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`sources`|トレース メッセージを開始するトレース ソースを保持します。|  
  
## 解説  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 `<source>`  要素を使用してトレース ソース `mySource` を追加し、`sourceSwitch` という名前のソース スイッチのレベルを設定する方法を次の例に示します。  トレース情報をコンソールに書き込むコンソール トレース リスナーが追加されます。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## 参照  
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Switches](../../../../../docs/framework/debug-trace-profile/trace-switches.md)