---
title: "&lt;switches&gt; の &lt;add&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<switches> の <add> 要素"
  - "<switches> の add 要素"
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;switches&gt; の &lt;add&gt; 要素
トレース スイッチを設定するレベルを指定します。  
  
## 構文  
  
```  
<add name="switch name"  
     value="value"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**name**|必須の属性です。<br /><br /> スイッチの名前を指定します。  この属性の値は、スイッチ コンストラクターに渡される *displayName* パラメーターと一致します。|  
|**値**|必須の属性です。<br /><br /> スイッチのレベルを指定します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`switches`|トレース スイッチとトレース スイッチを設定するレベルを保持します。|  
|`system.diagnostics`|メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。|  
  
## 解説  
 トレース スイッチのレベルは、構成ファイル内に配置することにより変更できます。  スイッチが <xref:System.Diagnostics.BooleanSwitch> の場合は、スイッチのオン\/オフを切り替えることができます。  スイッチが <xref:System.Diagnostics.TraceSwitch> の場合は、スイッチにさまざまなレベルを割り当てて、アプリケーションが出力するトレース メッセージまたはデバッグ メッセージの型を指定できます。  
  
## 使用例  
 次の例に `General` トレースを設定するには **\<追加\>** 要素を使用する方法をに切り替え [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) レベルを有効にします `Data` ブール トレース スイッチを示します。  
  
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