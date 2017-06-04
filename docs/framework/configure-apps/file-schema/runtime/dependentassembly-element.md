---
title: "&lt;dependentAssembly&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<dependentAssembly> 要素"
  - "コンテナー タグ, <dependentAssembly> 要素"
  - "dependentAssembly 要素"
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;dependentAssembly&gt; 要素
各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。  アセンブリごとに 1 つの `dependentAssembly` 要素を使用します。  
  
## 構文  
  
```  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|`assemblyIdentity`|アセンブリに関する識別情報が含まれています。  各 `dependentAssembly` 要素にこの要素を含める必要があります。|  
|`codeBase`|アセンブリがコンピューターにインストールされていない場合に、ランタイムが共有アセンブリを検索できるかどうかを指定します。|  
|`bindingRedirect`|1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。|  
|`publisherPolicy`|ランタイムがこのアセンブリに発行者ポリシーを適用するかどうかを指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 使用例  
 2 つのアセンブリのアセンブリ情報をカプセル化する例を示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)