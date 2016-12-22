---
title: "#pragma (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma ディレクティブ [C#]"
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #pragma (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

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
 [C\# プリプロセッサ ディレクティブ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\#pragma 警告](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [\#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)