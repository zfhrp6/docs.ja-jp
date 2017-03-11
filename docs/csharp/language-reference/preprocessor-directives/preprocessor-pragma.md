---
title: "#pragma (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma ディレクティブ [C#]"
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# #pragma (C# リファレンス)
`#pragma` は、このキーワードが含まれているファイルのコンパイルについて、特殊な命令をコンパイラに指示します。  命令はコンパイラでサポートされる必要があります。  つまり、`#pragma` を使用してカスタム プリプロセッサ命令を作成することはできません。  Microsoft C\# コンパイラは、次の 2 つの `#pragma` 命令をサポートします。  
  
 [\#pragma 警告](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [\#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## 構文  
  
```  
#pragma pragma-name pragma-arguments  
```  
  
#### パラメーター  
 `pragma-name`  
 認識されるプラグマの名前。  
  
 `pragma-arguments`  
 プラグマ固有の引数。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [\#pragma 警告](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [\#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)