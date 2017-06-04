---
title: "&lt;UseSmallInternalThreadStacks&gt; 要素 | Microsoft Docs"
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
  - "<UseSmallInternalThreadStacks> 要素"
  - "UseSmallInternalThreadStacks 要素"
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;UseSmallInternalThreadStacks&gt; 要素
共通言語ランタイム \(CLR: Common Language Runtime\) で内部的に使用する特定のスレッドを作成するときに、それらのスレッドに既定のスタック サイズを使用せずに、明示的なスタック サイズを指定してメモリ使用量を減らすことを要求します。  
  
## 構文  
  
```  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|enabled|必須の属性です。<br /><br /> CLR で内部的に使用する特定のスレッドを作成するときに、既定のスタック サイズではなく明示的なスタック サイズを使用することを要求するかどうかを指定します。  明示的なスタック サイズは、既定のスタック サイズの 1 MB よりも小さい値になります。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|true|明示的なスタック サイズを要求します。|  
|false|既定のスタック サイズを使用します。  これは [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] の既定値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 この構成要素は、プロセスでの仮想メモリ使用量を減らすことを要求するために使用します。CLR で内部スレッドに使用する明示的なスタック サイズは、要求が受け入れられる場合、既定のサイズよりも小さくなります。  
  
> [!IMPORTANT]
>  この構成要素は CLR に対する要求であり、絶対要件ではありません。  [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] では、この要求は x86 アーキテクチャについてのみ受け入れられます。  この要素は、CLR の将来のバージョンでは完全に無視されるか、選択した内部スレッドに対して常に使用される明示的なスタック サイズに置き換えられる可能性があります。  
  
 この構成要素を指定すると、要求が受け入れられる場合は仮想メモリ使用量を減らすことができる一方で、スタック サイズが小さくなるとスタック オーバーフローが発生する可能性が高くなるため、信頼性が低下します。  
  
## 使用例  
 CLR で内部的に使用する特定のスレッドに明示的なスタック サイズを使用することを要求する方法を、次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)