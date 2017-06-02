---
title: "&lt;etwEnable&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<etwEnable> 要素"
  - "etwEnable 要素"
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;etwEnable&gt; 要素
共通言語ランタイム イベントで Windows イベント トレーシング \(ETW\) を有効にするかどうかを指定します。  
  
## 構文  
  
```  
<etwEnable enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> ETW を有効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|true|ETW を有効にします。  これは、Windows Vista および Windows Server 2008 オペレーティング システム以降のバージョンの Windows の既定値です。|  
|false|ETW を無効にします。  これは、旧バージョンの Windows の既定値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 Windows Vista 以降、ETW は既定で有効になっています。  この要素を使用すると、アプリケーションに対して ETW を無効にできます。  それ以前の Windows バージョンでは、この要素を使用すると、アプリケーションに対して ETW を有効にできます。  
  
> [!NOTE]
>  レジストリ設定を使用すると、サーバーでグローバルに ETW を有効または無効にできます。  「[.NET Framework のログ記録の制御](../../../../../docs/framework/performance/controlling-logging.md)」を参照してください。  
  
## 使用例  
 アプリケーションに対して ETW トレースを有効にする方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [.NET Framework のログ記録の制御](../../../../../docs/framework/performance/controlling-logging.md)