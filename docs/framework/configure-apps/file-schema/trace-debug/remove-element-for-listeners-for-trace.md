---
title: "&lt;trace&gt; の &lt;listeners&gt; の &lt;remove&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> 要素"
  - "remove 要素"
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;trace&gt; の &lt;listeners&gt; の &lt;remove&gt; 要素
**Listeners** コレクションからリスナーを削除します。  
  
## 構文  
  
```  
  
<remove name="listener name" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**name**|必須の属性です。<br /><br /> **Listeners** コレクションから削除するリスナーの名前。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを指定します。  リスナーは、トレース出力を適切なターゲットに転送します。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|ASP.NET トレース サービスを設定します。|  
  
## 解説  
  
> [!NOTE]
>  `Listeners` コレクションから <xref:System.Diagnostics.DefaultTraceListener> を削除すると、<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>、および <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> の各メソッドの動作が変わります。  `Assert` メソッドまたは `Fail` メソッドを呼び出すと、通常はメッセージ ボックスが表示されますが、`Listeners` コレクションに <xref:System.Diagnostics.DefaultTraceListener> がない場合はメッセージ ボックスが表示されません。  
  
## 使用例  
 トレース **Listeners** コレクションから既定のトレース リスナーを削除する方法を次の例に示します。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
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