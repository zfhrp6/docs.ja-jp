---
title: "&lt;developmentMode&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<developmentMode> 要素"
  - "コンテナー タグ, <developmentMode> 要素"
  - "developmentMode 要素"
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;developmentMode&gt; 要素
DEVPATH 環境変数で指定されたディレクトリでランタイムがアセンブリを検索するかどうかを指定します。  
  
## 構文  
  
```  
<developmentMode developerInstallation="true | false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|**developerInstallation**|DEVPATH 環境変数で指定されたディレクトリでランタイムがアセンブリを検索するかどうかを指定します。|  
  
## developerInstallation 属性  
  
|値|説明|  
|-------|--------|  
|**true**|DEVPATH 環境変数で指定されたディレクトリでアセンブリを検索します。|  
|**false**|DEVPATH 環境変数で指定されたディレクトリでアセンブリを検索しません。  これが既定値です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 この設定は、開発時にだけ使用します。  ランタイムは、DEVPATH で見つかった厳密な名前付きアセンブリのバージョンを確認しません。  単純に、最初に見つかったアセンブリを使用します。  
  
## 使用例  
 DEVPATH 環境変数で指定されたディレクトリでランタイムがアセンブリを検索するように指定する例を示します。  
  
```  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [方法 : DEVPATH を使用してアセンブリを指定する](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)