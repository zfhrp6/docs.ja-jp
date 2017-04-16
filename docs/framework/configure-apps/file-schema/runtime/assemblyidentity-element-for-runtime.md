---
title: "&lt;runtime&gt; の &lt;assemblyIdentity&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<assemblyIdentity> 要素"
  - "assemblyIdentity 要素"
  - "コンテナー タグ, <assemblyIdentity> 要素"
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;runtime&gt; の &lt;assemblyIdentity&gt; 要素
アセンブリに関する識別情報が含まれています。  
  
## 構文  
  
```  
  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`name`|必須の属性です。<br /><br /> アセンブリの名前。|  
|`culture`|省略可能な属性。<br /><br /> アセンブリの言語、および国または地域を指定する文字列。|  
|`publicKeyToken`|省略可能な属性。<br /><br /> アセンブリの厳密な名前を指定する 16 進値。|  
|`processorArchitecture`|省略可能な属性。<br /><br /> "x86"、"amd64"、"msil"、または "ia64" のいずれかの値で、プロセッサ固有のコードを含むアセンブリのプロセッサ アーキテクチャを指定します。  値の大文字と小文字は区別されません。  この属性にこれ以外の値を割り当てると、`<assemblyIdentity>` 要素全体が無視されます。  「<xref:System.Reflection.ProcessorArchitecture>」を参照してください。|  
  
## processorArchitecture 属性  
  
|値|説明|  
|-------|--------|  
|`amd64`|64 ビット AMD プロセッサのみ|  
|`ia64`|64 ビット Intel プロセッサのみ|  
|`msil`|プロセッサおよびワードあたりのビット数に関して中立|  
|`x86`|32 ビット Intel プロセッサ \(ネイティブまたは 64 ビット プラットフォーム上の WOW \(Windows on Windows\) 環境\)|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`assemblyBinding`|アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`dependentAssembly`|各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。  アセンブリごとに 1 つの `<dependentAssembly>` 要素を使用します。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## 解説  
 **\<dependentAssembly\>** の各要素は **\<assemblyIdentity\>** の 1 種類の子要素が必要です。  
  
 `processorArchitecture` 属性が指定されている場合、`<assemblyIdentity>` 要素は対応するプロセッサ アーキテクチャを使用するアセンブリにのみ適用されます。  `processorArchitecture` 属性が指定されていない場合、`<assemblyIdentity>` 要素はどのプロセッサ アーキテクチャを使用するアセンブリにも適用できます。  
  
 次の例は、2 種類のプロセッサ アーキテクチャをターゲットとし、かつバージョン管理が同期していない、同じ名前の 2 つのアセンブリ用の構成ファイルを示しています。  アプリケーションが x86 プラットフォームで実行される場合は、最初の `<assemblyIdentity>` 要素が適用され、もう 1 つの要素が無視されます。  アプリケーションが x86 または ia64 以外のプラットフォームで実行される場合は、両方の要素が無視されます。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 構成ファイルに、`processorArchitecture` 属性が指定されていない `<assemblyIdentity>` 要素が含まれ、かつプラットフォームと一致する要素が含まれていない場合は、`processorArchitecture` 属性が指定されていない要素が使用されます。  
  
## 使用例  
 アセンブリの情報を提供する例を示します。  
  
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
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリ バージョンのリダイレクト](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)