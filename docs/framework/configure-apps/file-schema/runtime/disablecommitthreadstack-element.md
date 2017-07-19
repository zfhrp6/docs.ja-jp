---
title: "&lt;disableCommitThreadStack&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableCommitThreadStack> 要素"
  - "disableCommitThreadStack 要素"
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;disableCommitThreadStack&gt; 要素
スレッドの起動時にスレッド スタック全体をコミットするかどうかを指定します。  
  
 \<configuration\>  
\<runtime\>  
\<disableCommitThreadStack\>  
  
## 構文  
  
```  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|enabled|必須の属性です。<br /><br /> スレッド起動時にスレッド スタック全体をコミットすること \(既定の動作\) を無効にするかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|0|共通言語ランタイムの既定の動作 \(スレッドの起動時にスレッド スタック全体をコミット\) を無効にしません。|  
|1|共通言語ランタイムの既定の動作 \(スレッドの起動時にスレッド スタック全体をコミット\) を無効にします。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 共通言語ランタイムの既定の動作では、スレッドの起動時にスレッド スタック全体がコミットされます。 メモリが限られているサーバーで多数のスレッドが作成する必要があり、それらのスレッドのほとんどがごくわずかのスタック スペースしか使用しない場合は、スレッドの起動時に共通言語ランタイムが直ちにスレッド スタック全体をコミットしなければ、サーバーのパフォーマンスが向上する可能性があります。  
  
> [!NOTE]
>  アンマネージ ホストは、[STARTUP\_FLAGS](../../../../../ocs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) 列挙体の `STARTUP_DISABLE_COMMITTHREADSTACK` 起動フラグを使用することにより、同じ結果を得ることができます。  
  
## 使用例  
 次の例は、共通言語ランタイムの既定の動作 \(スレッド起動時にスレッド スタック全体をコミット\) を無効にする方法を示しています。  
  
```  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)