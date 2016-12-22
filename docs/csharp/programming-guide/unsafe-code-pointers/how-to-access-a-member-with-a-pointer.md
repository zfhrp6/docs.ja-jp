---
title: "方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド) | Microsoft Docs"
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
  - "ポインター [C#], メンバー アクセス"
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

unsafe コンテキストで宣言された構造体のメンバーにアクセスするには、次の例に示すように、メンバー アクセス演算子を使用できます。`p` は、メンバー `x` を含む[構造体](../../../csharp/language-reference/keywords/struct.md)のポインターになります。  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## 使用例  
 次の例では、`x` と `y` の 2 つの座標を含む[構造体](../../../csharp/language-reference/keywords/struct.md)である `CoOrds` を宣言し、インスタンス化します。  `->` メンバー アクセス演算子と、`home` インスタンスへのポインターを使用して、`x` と `y` に値を代入します。  
  
> [!NOTE]
>  式 `p->x` と式 `(*p).x` は等価であり、どちらの式を使用しても同じ結果が得られます。  
  
 [!CODE [csProgGuidePointers#9](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#9)]  
  
 [!CODE [csProgGuidePointers#10](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#10)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)   
 [型](../../../csharp/language-reference/keywords/types.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)