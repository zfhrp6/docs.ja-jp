---
title: "コンパイラおよび言語プロバイダー設定のスキーマ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
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
  - "コンパイラ構成要素"
  - "コンパイラ構成要素, スキーマ"
  - "コンパイラ構成設定"
  - "コンパイラ構成設定, スキーマ"
  - "構成スキーマ [.NET Framework], コンパイラ設定"
  - "構成の設定 [.NET Framework], コンパイラ"
  - "言語プロバイダー"
  - "言語プロバイダー, 設定スキーマ"
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# コンパイラおよび言語プロバイダー設定のスキーマ
コンパイラおよび言語プロバイダー設定では、利用可能な言語プロバイダー用のコンパイラの設定要素を指定します。  各コンパイラ設定要素では、コード プロバイダーの型名、コンパイラ パラメーター、サポートされる言語名、およびサポートされるファイル拡張子を指定します。  
  
 .NET Framework では、マシン構成ファイル \(Machine.config\) にコンパイラの初期設定を定義します。  開発者やコンパイラの販売元では、新しい <xref:System.CodeDom.Compiler.CodeDomProvider> 実装用に構成の設定を追加できます。  コンピューター上の言語プロバイダーおよびコンパイラの構成の設定をプログラムで列挙するには、<xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=fullName> メソッドを使用します。  
  
 [\<configuration\> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|要素|説明|  
|--------|--------|  
|[\<system.codedom\>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|利用可能な言語プロバイダー用のコンパイラ構成設定を指定します。|  
|[\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|コンパイラの設定要素のコンテナー; [\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) 内に含まれています。また、より多くの要素を示します。|  
|[\<コンパイラ\>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|言語プロバイダーのコンパイラ設定属性を指定します。|  
  
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
 [\<compiler\> 要素](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)