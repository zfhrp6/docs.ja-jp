---
title: "&lt;probing&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#probing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<probing> 要素"
  - "コンテナー タグ, <probing> 要素"
  - "probing 要素"
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# &lt;probing&gt; 要素
アセンブリを読み込むときに、共通言語ランタイムが検索するアプリケーション ベース サブディレクトリを指定します。  
  
## 構文  
  
```  
<probing privatePath="paths"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`privatePath`|必須の属性です。<br /><br /> アセンブリが格納されているアプリケーションのベース ディレクトリのサブディレクトリを指定します。  サブディレクトリは、セミコロン \(;\) で区切ります。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 使用例  
 ランタイムがアセンブリを検索するアプリケーション ベース サブディレクトリを指定する例を示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリの場所の指定](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)