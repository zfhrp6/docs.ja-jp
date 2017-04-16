---
title: "&lt;switches&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#switches"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<switches> 要素"
  - "switches 要素"
  - "トレース スイッチ, <switches> 要素"
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;switches&gt; 要素
トレース スイッチとトレース スイッチを設定するレベルを保持します。  
  
## 構文  
  
```  
  
      <switches>   
</switches>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|トレース スイッチを設定するレベルを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`System.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## 解説  
 トレース スイッチのレベルは、構成ファイル内に配置することにより変更できます。  スイッチが <xref:System.Diagnostics.BooleanSwitch> の場合は、スイッチのオン\/オフを切り替えることができます。  スイッチが <xref:System.Diagnostics.TraceSwitch> の場合は、スイッチにさまざまなレベルを割り当てて、アプリケーションが出力するトレース メッセージまたはデバッグ メッセージの型を指定できます。  
  
## 使用例  
 次の例は、`General` トレースを設定するには **\<switch\>** 要素を使用する方法を [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) のレベルをに切り替え、`Data` ブール トレース スイッチを有効にします。  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## 参照  
 <xref:System.Diagnostics.Switch>   
 <xref:System.Diagnostics.TraceSwitch>   
 <xref:System.Diagnostics.BooleanSwitch>   
 [トレースおよびデバッグ設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)