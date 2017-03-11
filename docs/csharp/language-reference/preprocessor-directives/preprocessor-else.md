---
title: "#else (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#else"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#else ディレクティブ [C#]"
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# #else (C# リファレンス)
`#else` を使用すると、複合条件付きディレクティブを作成できます。つまり、先行する [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ディレクティブ、または [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) ディレクティブ \(省略可能\) の式が `true` と評価されなかった場合に、コンパイラによって、`#else` とそれに続く `#endif` の間にあるすべてのコードが評価されます。  
  
## 解説  
 `#else` と、その次の [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) の間には、他のプリプロセッサ ディレクティブは指定できません。  `#else` の使用例については、「[\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)