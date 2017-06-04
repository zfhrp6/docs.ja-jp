---
title: "&lt;system.codedom&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.codedom> 要素"
  - "コンパイラ構成要素, <system.codedom> 要素"
  - "system.codedom 要素"
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: 17
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 17
---
# &lt;system.codedom&gt; 要素
利用可能な言語プロバイダー用のコンパイラ構成設定を指定します。  
  
## 構文  
  
```  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラの設定要素のコンテナー; [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 内に含まれています。また、より多くの要素を示します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
  
## .NET Framework Version 2.0  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) 要素は <xref:Microsoft.CSharp.CSharpCodeProvider> と <xref:Microsoft.VisualBasic.VBCodeProvider>などの .NET Framework と、インストールされている既定のプロバイダーの他に、コンピューターにインストールされる言語プロバイダーのコンパイラの構成設定が含まれます。  [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 要素が含まれています [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) のゼロ以上の要素を紹介します。  [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) の各要素は、特定の言語プロバイダー用のコンパイラ設定属性を指定します。  
  
 開発者やコンパイラの販売元では、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> 実装用にマシンの構成ファイル \(Machine.config\) に構成の設定を追加できます。  <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> メソッドを使用して、既定の言語プロバイダーおよびコンピューターのコンパイラ設定で識別される言語プロバイダーの両方をプログラムで列挙します。  
  
> [!NOTE]
>  .NET Framework Version 1.0 および 1.1 では、.NET Framework に用意されている既定の言語プロバイダーは [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 要素で識別されます。  .NET Framework version 2.0 では、既定の言語プロバイダーは [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 要素では識別されませんが、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> のメソッドを使用して列挙できます。  
  
## .NET Framework Version 1.0 および 1.1  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) 要素はコンピューター上の言語プロバイダー用のコンパイラの構成設定が含まれます。  [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) 要素が含まれています [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) のゼロ以上の要素を紹介します。  [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) の各要素は、特定の言語プロバイダー用のコンパイラ設定属性を指定します。  
  
 .NET Framework では、マシン構成ファイル \(Machine.config\) にコンパイラの初期設定を定義します。  開発者やコンパイラの販売元では、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> 実装用に構成の設定を追加できます。  コンピューター上の言語プロバイダーおよびコンパイラの構成の設定をプログラムで列挙するには、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> メソッドを使用します。  
  
## 構成ファイル  
 この要素は、マシン構成ファイルとアプリケーション構成ファイルで使用できます。  
  
## 使用例  
 一般的なコンパイラ設定を次の例に示します。  
  
```  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
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