---
title: "アセンブリの場所の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "アプリケーションの構成 [.NET Framework]"
  - "アセンブリ [.NET Framework], 指定 (場所を)"
  - "構成 [.NET Framework], アプリケーション"
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: 8
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 8
---
# アセンブリの場所の指定
アセンブリの場所は、次の 2 とおりの方法で指定できます。  
  
-   [\<コードベース\>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) 要素を使用します。  
  
-   [\<プローブ\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) 要素を使用します。  
  
 [.NET Framework 構成ツール](http://msdn.microsoft.com/ja-jp/a7106c52-68da-490e-b129-971b2c743764)を使用して、アセンブリの場所または共通言語ランタイムがアセンブリを検索する場所を指定することもできます。  
  
## codeBase 要素\>  \<を使用します。  
 、アセンブリ バージョンのリダイレクトする発行者ポリシー ファイルまたはマシン構成ファイルにのみ **\<codeBase\>** 要素を使用できます。  ランタイムは使用するアセンブリ バージョンを決定するときに、バージョンを決定するファイルからコード ベース設定を適用します。  コード ベースが指定されていない場合は、通常の方法でアセンブリを検索します。  詳細については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 アセンブリの場所を指定する方法の例を次に示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **version** 属性は、厳密な名前の付いたすべてのアセンブリに対して設定する必要がありますが、厳密な名前が付いていないアセンブリについては省略してください。  **\<codeBase\>** 要素は **href** 属性が必要です。  **\<codeBase\>** 要素のバージョンの範囲は指定できません。  
  
> [!NOTE]
>  厳密な名前の付いていないアセンブリに対してコード ベースのヒントを提供する場合は、そのヒントでアセンブリ ベースまたはアプリケーション ベース ディレクトリのサブディレクトリを示す必要があります。  
  
## プローブ \<\> 要素を使用します。  
 ランタイムは、コード ベースを持たないアセンブリの場所を検索して特定します。  検索の詳細については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 アプリケーション構成ファイルでランタイムが検索するサブディレクトリを指定するために [\<プローブ\>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) 要素を使用して、アセンブリの場所を特定するとき。  ランタイムが検索するディレクトリを指定する方法の例を次に示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **privatePath** 属性に、ランタイムがアセンブリを検索する必要があるディレクトリを指定します。  アプリケーションが C:\\Program Files\\MyApp に配置されている場合、ランタイムは、コード ベースが指定されていないアセンブリを C:\\Program Files\\MyApp\\Bin、C:\\Program Files\\MyApp\\Bin2\\Subbin、および C:\\Program Files\\MyApp\\Bin3 内で検索します。  **privatePath** に指定するディレクトリは、アプリケーション ベース ディレクトリのサブディレクトリであることが必要です。  
  
## 参照  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/ja-jp/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)