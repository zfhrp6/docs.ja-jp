---
title: "&lt;linkedConfiguration&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<linkedConfiguration> 要素"
  - "構成ファイル [.NET Framework], リンクされた構成ファイル"
  - "インクルード (構成ファイルを)"
  - "リンクされた構成ファイル"
  - "linkedConfiguration 要素"
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;linkedConfiguration&gt; 要素
インクルードする構成ファイルを指定します。  
  
## 構文  
  
```  
<linkedConfiguration  
   href="URL of linked configuration file"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`href`|インクルードされる構成ファイルの URL です。  `href` 属性に指定できる形式は "file:\/\/" に限られています。  ローカル ファイルと UNC ファイルがサポートされています。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<assemblyBinding\> 要素](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)|構成レベルでのアセンブリ バインディング ポリシーを指定します。|  
  
## 解説  
 `<linkedConfiguration>` 要素は、コンポーネント アセンブリの供給を簡素化します。  既知の場所に構成ファイルがあるアセンブリを 1 つまたは複数のアプリケーションが使用する場合は、それらのアプリケーションの構成ファイルに、構成情報を直接取り込むのではなく、`<linkedConfiguration>` 要素を使用してアセンブリ構成ファイルをインクルードできます。  コンポーネント アセンブリが供給される場合は、共通の構成ファイルを更新することで、そのアセンブリを使用するすべてのアプリケーションに更新された構成情報が提供されます。  
  
> [!NOTE]
>  Windows side\-by\-side マニフェストを使用するアプリケーションに対しては、`<linkedConfiguration>` 要素がサポートされません。  
  
 リンクされた構成ファイルの使用については、次の規則が適用されます。  
  
-   インクルードされる構成ファイル内の設定は、ローダー バインディング ポリシーにのみ影響し、ローダーのみが使用します。  インクルードされる構成ファイルには、バインディング ポリシー以外の設定も指定できますが、それらの設定には効力がありません。  
  
-   `href` 属性に指定できる形式は "file:\/\/" に限られています。  ローカル ファイルと UNC ファイルがサポートされています。  
  
-   構成ファイルあたりのリンクされる構成の数には制限がありません。  
  
-   リンクされるすべての構成ファイルは、マージされて 1 つのファイルとなります。これは、C\/C\+\+ の `#include` ディレクティブの動作と似ています。  
  
-   `<linkedConfiguration>` 要素は、アプリケーション構成ファイルでのみ使用でき、Machine.config では無視されます。  
  
-   循環参照は、検出されて終了されます。  つまり、一連の構成ファイルの `<linkedConfiguration>` 要素がループを生成する場合は、そのループが検出されて停止されます。  
  
## 使用例  
 ローカル ハード ディスクから構成ファイルをインクルードする方法を、次のコード例に示します。  
  
```  
<configuration>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>  
   </assemblyBinding>  
</configuration>  
```  
  
## 参照  
 [\<assemblyBinding\> 要素](../../../../docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
 [構成ファイル スキーマ](../../../../docs/framework/configure-apps/file-schema/index.md)