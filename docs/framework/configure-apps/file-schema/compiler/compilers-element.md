---
title: "&lt;compilers&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compilers> 要素"
  - "コンパイラ構成要素, <compilers> 要素"
  - "compilers 要素"
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;compilers&gt; 要素
コンパイラの設定要素のコンテナー; [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 内に含まれています。また、より多くの要素を示します。  
  
## 構文  
  
```  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<compiler\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|言語プロバイダーのコンパイラ設定属性を指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|利用可能な言語プロバイダー用のコンパイラ構成設定を指定します。|  
  
## 解説  
 [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 要素はコンピューター上の言語プロバイダー用のコンパイラの構成設定が含まれます。  [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) の各要素は、特定の言語プロバイダー用のコンパイラ設定属性を指定します。  
  
 .NET Framework では、マシン構成ファイル \(Machine.config\) 内にコンパイラと言語プロバイダーの初期設定が定義されています。  開発者やコンパイラの販売元では、新しい <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> 実装用に構成の設定を追加できます。  コンピューター上の言語プロバイダーおよびコンパイラの構成の設定をプログラムで列挙するには、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> メソッドを使用します。  
  
## 構成ファイル  
 この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 一般的なコンパイラ設定要素を次の例に示します。  
  
```  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## 参照  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [コンパイラおよび言語プロバイダー設定のスキーマ](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)   
 [\<compiler\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)