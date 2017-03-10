---
title: "/target:module (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/target:module"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-target compiler options [C#], /target:module"
  - "target compiler options [C#], /target:module"
  - "/target compiler options [C#], /target:module"
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /target:module (C# Compiler Options)
このオプションは、コンパイルでアセンブリ マニフェストを生成しない場合に使用します。  
  
## 構文  
  
```  
/target:module  
```  
  
## 解説  
 既定でに、このオプションを使用してコンパイルされた出力 .netmodule ファイル拡張子が付きます。  
  
 アセンブリ マニフェストを持たないファイルは、.NET Framework 共通言語ランタイムで読み込むことができません。  ただし、アセンブリ マニフェストを持たないファイルは、[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) を使用してアセンブリのアセンブリ マニフェストに組み込むことができます。  
  
 1 回のコンパイルで複数のモジュールが作成される場合、あるモジュールの [internal](../../../csharp/language-reference/keywords/internal.md) 型をコンパイル中の他のモジュールで利用できます。  あるモジュールのコードが別のモジュールの `internal` 型を参照する場合は、**\/addmodule** を使用して両方のモジュールを 1 つのアセンブリ マニフェストに組み込む必要があります。  
  
 Visual Studio 開発環境では、モジュールの作成はサポートされていません。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、`in.netmodule` を作成するには、次のコードを使用します。  
  
```  
csc /target:module in.cs  
```  
  
## 参照  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)