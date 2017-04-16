---
title: "&lt;legacyCorruptedStateExceptionsPolicy&gt; 要素 | Microsoft Docs"
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
  - "<legacyCorruptedStateExceptionsPolicy> 要素"
  - "legacyCorruptedStateExceptionsPolicy 要素"
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;legacyCorruptedStateExceptionsPolicy&gt; 要素
共通言語ランタイムで、アクセス違反やその他の破損状態の例外をマネージ コードがキャッチできるようにするかどうかを指定します。  
  
## 構文  
  
```  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> アクセス違反などの破損状態の例外エラーをアプリケーションがキャッチするように指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|アプリケーションは、アクセス違反などの破損状態の例外エラーをキャッチしません。  これは、既定の設定です。|  
|`true`|アプリケーションは、アクセス違反などの破損状態の例外エラーをキャッチします。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 .NET Framework Version 3.5 以前では、共通言語ランタイムは、プロセス状態の破損によって発生した例外をマネージ コードがキャッチできるようにしていました。  このような例外の例として、アクセス違反があります。  
  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、このような例外がマネージ コードの `catch` ブロックでキャッチされなくなります。  ただし、次の 2 つの方法により、この変更をオーバーライドして破損状態の例外の処理を維持できます。  
  
-   `<legacyCorruptedStateExceptionsPolicy>` 要素の `enabled` 属性を `true` に設定します。  この構成設定はプロセス全体に適用され、すべてのメソッドに反映されます。  
  
 または  
  
-   例外の `catch` ブロックを含むメソッドに <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> 属性を適用します。  
  
 この構成要素は、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降でのみ使用できます。  
  
## 使用例  
 アプリケーションの動作を [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] より前の動作に戻し、破損状態の例外エラーをすべてキャッチするように指定する方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)