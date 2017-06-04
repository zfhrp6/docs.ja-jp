---
title: "&lt;codeBase&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<codeBase> 要素"
  - "codeBase 要素"
  - "コンテナー タグ, <codeBase> 要素"
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;codeBase&gt; 要素
共通言語ランタイムがアセンブリを検索できる場所を指定します。  
  
## 構文  
  
```  
  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`href`|必須の属性です。<br /><br /> 指定したアセンブリのバージョンをランタイムが検索できる URL を指定します。|  
|`version`|必須の属性です。<br /><br /> コードベースを適用するアセンブリのバージョンを指定します。  アセンブリのバージョン番号の形式は、*major.minor.build.revision* です。|  
  
## version 属性  
  
|値|説明|  
|-------|--------|  
|バージョン番号の各部分で有効値は、0 ～ 65535 です。|使用できません。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`buildproviders`|カスタム リソース ファイルをコンパイルするためのビルド プロバイダーのコレクションを定義します。  ビルド プロバイダーの数は任意です。|  
|`compilation`|ASP.NET で使用されるすべてのコンパイル設定値を構成します。|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`System.web`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## 解説  
 設定するマシン構成ファイルまたは発行者ポリシー ファイルの **\<codeBase\>** を使用するランタイムのファイルは、アセンブリ バージョンのリダイレクトしなければなりません。  アプリケーション構成ファイルは、アセンブリ バージョンをリダイレクトせずにコードベース設定を指定できます。  使用するアセンブリ バージョンを決定した後、ランタイムはバージョンを決定したファイルのコードベース設定を適用します。  コードベースを指定しないと、ランタイムはアセンブリを通常の方法でプローブします。  
  
 アセンブリが厳密な名前を持つ場合、コードベース設定はローカル イントラネットまたはインターネットの任意の場所に保存できます。  プライベート アセンブリの場合、コードベース設定はアプリケーションのディレクトリからの相対パスにする必要があります。  
  
 厳密な名前のないアセンブリの場合、ローダーはバージョンの使用コードベース\> の \<現れるまで dependentAssembly\>で \<無視されます。  バインディングを他のアセンブリにリダイレクトするアプリケーション構成ファイルにエントリがある場合は、アセンブリのバージョンがバインディング要求と一致しないときでも、リダイレクトが優先されます。  
  
## 使用例  
 ランタイムがアセンブリを検索できる場所を指定する例を示します。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリの場所の指定](../../../../../docs/framework/configure-apps/specify-assembly-location.md)   
 [ランタイムがアセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)