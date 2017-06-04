---
title: "&lt;assert&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assert"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assert> 要素"
  - "assert 要素"
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;assert&gt; 要素
<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。  
  
## 構文  
  
```  
  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`assertuienabled`|省略可能な属性。<br /><br /> **Debug.Assert** メソッドが **false** になったときにメッセージ ボックスを表示するかどうかを指定します。|  
|`logfilename`|省略可能な属性。<br /><br /> **Debug.Assert** が **false** になった場合のメッセージの書き込み先のファイルの名前を指定します。|  
  
## assertuienabled 属性  
  
|値|説明|  
|-------|--------|  
|`true`|メッセージ ボックスを表示します。  これは、既定の設定です。|  
|`false`|メッセージ ボックスを表示しません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## 解説  
 **\<assert\>** 要素の属性は、両方とも省略可能です。  メッセージの書き込み先のファイルを指定せずにメッセージ ボックスを無効にするか、またはメッセージ ボックスを有効なままにして、メッセージの書き込み先のファイルを指定できます。  
  
## 使用例  
 **Debug.Assert** の呼び出し時のメッセージ ボックス表示を無効にし、メッセージを `c:\log.txt` に書き込む方法を次の例に示します。  
  
```  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.Debug>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)