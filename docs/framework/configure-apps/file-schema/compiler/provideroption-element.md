---
title: "&lt;providerOption&gt; 要素 | Microsoft Docs"
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
  - "provideroption"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<provideroption> 要素"
  - "provideroption 要素"
  - "providerOptions"
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: 22
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 22
---
# &lt;providerOption&gt; 要素
言語プロバイダーのコンパイラ バージョン属性を指定します。  
  
## 構文  
  
```  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`name`|必須の属性です。<br /><br /> オプションの名前を指定します \(たとえば "CompilerVersion"\)。|  
|`value`|必須の属性です。<br /><br /> オプションの値を指定します \(たとえば "v3.5"\)。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|[\<system.codedom\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|利用可能な言語プロバイダー用のコンパイラ構成設定を指定します。|  
|[\<compilers\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラの設定要素用のコンテナーです。0 個以上の `<compiler>` 要素が含まれます。|  
|[\<compiler\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|言語プロバイダーのコンパイラ設定属性を指定します。|  
  
## 解説  
 .NET Framework Version 3.5 では、CodeDOM \(Code Document Object Model\) コード プロバイダーは、`<providerOption>` 要素を使用してプロバイダー固有のオプションをサポートできます。  
  
 .NET Framework 3.5 には、更新された .NET Framework 2.0 アセンブリと、新しい型を含む新しい Version 3.5 アセンブリが用意されています。  Microsoft C\# および Visual Basic のコード プロバイダーは .NET Framework 2.0 アセンブリに含まれますが、Version 3.5 のコンパイラをサポートするように更新されています。  既定では、更新されたコード プロバイダーは Version 2.0 のコンパイラ用のコードを生成します。  `<providerOption>` 要素を使用して、対象のコンパイラのバージョンを 3.5 に変更できます。  これを行うには、`name` 属性に "CompilerVersion" を指定し、`value` 属性に "v3.5" を指定します。  バージョン番号の前に小文字の "v" を指定する必要があります。  
  
 `<providerOption>` 要素を .NET Framework 2.0 の Machine.config ファイルまたはルートの Web.config ファイルに追加することで、バージョンの指定をグローバルにすることができます。  Machine.config ファイルで既定のコンパイラのバージョンを 3.5 に更新した場合は、アプリケーション構成ファイルで `<providerOption>` 要素を使用することにより、アプリケーションごとに 2.0 に戻すことができます。  
  
 CodeDOM コード プロバイダーの実装では、<xref:System.Collections.Generic.IDictionary%602> 型の `providerOptions` パラメーターを受け取るコンストラクターを用意することで、カスタム オプションを処理できます。  
  
## 使用例  
 C\# コード プロバイダーの Version 3.5 が使用されるように指定する方法の例を次に示します。  
  
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
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
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