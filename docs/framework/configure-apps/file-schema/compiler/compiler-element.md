---
title: "&lt;compiler&gt; 要素 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<compiler> 要素"
  - "コンパイラ構成属性"
  - "コンパイラ構成要素, <compiler> 要素"
  - "compiler 要素"
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;compiler&gt; 要素
言語プロバイダーのコンパイラ設定属性を指定します。  
  
## 構文  
  
```  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`compilerOptions`|省略可能な属性。<br /><br /> コンパイル用のその他のコンパイラ固有引数を指定します。  `compilerOptions` 属性の値については、通常、コンパイラのコンパイラ オプションのトピックで説明されています。  Visual Studio 2005 のドキュメントで「コンパイラ オプション」というキーワードを検索すると、コンパイラのオプションについての説明を見つけることができます。|  
|`extension`|必須の属性です。<br /><br /> 言語プロバイダーのソース ファイルで使用されるファイル名拡張子のセミコロン区切りのリストを指定します。  たとえば、".cs" とします。|  
|`language`|必須の属性です。<br /><br /> 言語プロバイダーでサポートされる言語名のセミコロン区切りのリストを指定します。  たとえば、"c\#;cs;csharp" とします。|  
|`type`|必須の属性です。<br /><br /> 言語プロバイダーの型名と、プロバイダーの実装が含まれているアセンブリの名前を指定します。  型名は、「[完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)」で定義されている要件を満たす必要があります。|  
|`warningLevel`|省略可能な属性。<br /><br /> コンパイラの既定の警告レベルを指定します。これにより、言語プロバイダーでエラーとして処理されるコンパイラの警告レベルが決定されます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<providerOption\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|言語プロバイダーのコンパイラ バージョン属性を指定します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|利用可能な言語プロバイダー用のコンパイラ構成設定を指定します。|  
|[\<compilers\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラの設定要素用のコンテナーです。0 個以上の `<compiler>` 要素が含まれます。|  
  
## 解説  
 各 `<compiler>` 要素では、特定の言語プロバイダー用のコンパイラ設定属性を指定します。  プロバイダーでは、特定の言語用に <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName> クラスを拡張します。`<compiler>` 要素では、言語プロバイダー用にコンパイラとコード ジェネレーターの設定を定義します。  
  
 .NET Framework では、マシン構成ファイル \(Machine.config\) にコンパイラの初期設定を定義します。  開発者やコンパイラの販売元では、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> 実装用に構成の設定を追加できます。  コンピューター上の言語プロバイダーおよびコンパイラの構成の設定をプログラムで列挙するには、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> メソッドを使用します。  
  
 アプリケーションまたは Web の構成ファイル内のコンパイラ要素によって、マシン構成ファイル内の設定を補足またはオーバーライドできます。  複数のプロバイダー実装で同じ言語名または同じファイル拡張子が設定されている場合は、最後に一致した設定で、その言語名またはファイル拡張子のそれまでの設定済みプロバイダーがオーバーライドされます。  
  
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
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## 参照  
 <xref:System.CodeDom.Compiler.CompilerInfo>   
 <xref:System.CodeDom.Compiler.CodeDomProvider>   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<compilers\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)   
 [完全修飾型名の指定](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)   
 [compilation の compilers の compiler 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)