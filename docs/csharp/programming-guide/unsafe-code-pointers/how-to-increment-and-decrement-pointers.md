---
title: "方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド) | Microsoft Docs"
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
  - "ポインター式 [C#], インクリメントとデクリメント"
  - "ポインター [C#], インクリメントとデクリメント"
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

pointer\-type\* 型のポインターの位置を [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) に従って変更するには、インクリメント演算子 `++` またはデクリメント演算子 `--` を使用します。  インクリメント式とデクリメント式には、次の書式を使用します。  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 インクリメント演算子とデクリメント演算子は、`void*` 以外のすべての型のポインターに適用できます。  
  
 `pointer-type` 型のポインターにインクリメント演算子を適用すると、ポインター変数に格納されているアドレスに [sizeof](../../../csharp/language-reference/keywords/sizeof.md) \(`pointer-type`\) が加算されます。  
  
 また、`pointer-type` 型のポインターにデクリメント演算子を適用すると、ポインター変数に格納されているアドレスから `sizeof` \(`pointer-type`\) が減算されます。  
  
 演算がポインターのドメインをオーバーフローしても例外は生成されません。どのような結果が生じるかは実装によって異なります。  
  
## 使用例  
 次の例では、ポインターを `int` のサイズだけインクリメントして、配列をステップ実行します。  ステップごとに、配列要素のアドレスと内容を表示します。  
  
 [!CODE [csProgGuidePointers#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#3)]  
  
 [!CODE [csProgGuidePointers#13](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuidePointers#13)]  
  
  **Value:0 @ Address:12860272**  
**Value:1 @ Address:12860276**  
**Value:2 @ Address:12860280**  
**Value:3 @ Address:12860284**  
**Value:4 @ Address:12860288**   
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