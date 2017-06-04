---
title: "&lt;trace&gt; の &lt;listeners&gt; の &lt;clear&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<trace> の <listeners> の <clear> 要素"
  - "<trace> の <listeners> の clear 要素"
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;trace&gt; の &lt;listeners&gt; の &lt;clear&gt; 要素
トレースの `Listeners` コレクションを削除します。  
  
## 構文  
  
```  
<clear/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
|`trace`|トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。|  
|`listeners`|メッセージを収集、格納、およびルーティングするリスナーを保持します。  リスナーは、トレース出力を適切なターゲットに転送します。|  
  
## 解説  
 `<clear>` 要素は、トレースの `Listeners` コレクションからすべてのリスナーを削除します。  `<add>` 要素を使用する前に、`<clear>` 要素を使用すると、コレクション内に他にアクティブなリスナーがないことを確認できます。  
  
 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName> プロパティ \(`System.Diagnostics.Trace.Listeners.Clear()`\) で <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> メソッドを呼び出すことにより、プログラムで `Listeners` コレクションを削除できます。  
  
 この要素は、マシン構成ファイル \(Machine.config\) およびアプリケーション構成ファイルで使用できます。  
  
> [!NOTE]
>  `<clear>` 要素は、`Listeners` コレクションから <xref:System.Diagnostics.DefaultTraceListener> を削除することで、<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>、および <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> の各メソッドの動作を変更します。  `Assert` メソッドまたは `Fail` メソッドを呼び出すと、通常はメッセージ ボックスが表示されます。  ただし、`Listeners` コレクションに <xref:System.Diagnostics.DefaultTraceListener> がない場合は、メッセージ ボックスが表示されません。  
  
## 使用例  
 `<add>` 要素を使用してリスナー `console` をトレースの `Listeners` コレクションに追加する前に、`<clear>` 要素を使用する方法を次の例に示します。  
  
```  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## 参照  
 <xref:System.Diagnostics.Trace.Listeners%2A>   
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.Debug>   
 <xref:System.Diagnostics.TraceSource>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [\<remove\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)   
 [Trace Listeners](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)