---
title: "ポインター比較 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ポインター [C#], 比較"
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ポインター比較 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の演算子を適用すると、あらゆる型のポインターを比較できます。  
  
 **\=\=   \!\=   \<   \>   \<\=   \>\=**  
  
 比較演算子は、2 つのオペランドのアドレスを符号なし整数として比較します。  
  
## 使用例  
 [!CODE [csProgGuidePointers#16](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#16)]  
  
 [!CODE [csProgGuidePointers#17](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#17)]  
  
## 出力例  
 `True`  
  
 `False`  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)