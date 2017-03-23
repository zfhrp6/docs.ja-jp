---
title: "?: 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "?:_CSharpKeyword"
  - "?_CSharpKeyword"
  - ":_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "?: 演算子 [C#]"
  - "条件演算子 (?:) [C#]"
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# ?: 演算子 (C# リファレンス)
条件演算子 \(`?:`\) では、ブール式の値に応じて 2 つの値のいずれかが返されます。  条件演算子の構文は次のとおりです。  
  
```  
condition ? first_expression : second_expression;  
```  
  
## 解説  
 `condition` は、`true` または `false` に評価される必要があります。  `condition` が `true` の場合、`first_expression` が評価され、これが結果となります。  `condition` が `false` の場合、`second_expression` が評価され、これが結果となります。  2 つの式のどちらか一方だけが評価されます。  
  
 `first_expression` の型と `second_expression` の型とは、同じ型であるか、または一方の型から他方の型への暗黙の型変換が存在している必要があります。  
  
 `if-else` の構築が必要となる場面で条件演算子を使用すると、計算をより簡潔に表現できます。  たとえば、次のコードは、まず `if` ステートメントを使用し、次に条件演算子を使用して、整数を正または負に分類します。  
  
```  
  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
  
```  
  
 条件演算子の結合規則は右から左になります。  `a ? b : c ? d : e` という式は、`(a ? b : c) ? d : e` ではなく、`a ? b : (c ? d : e)` と評価されます。  
  
 条件演算子は、オーバーロードできません。  
  
## 使用例  
 [!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [if\-else](../../../csharp/language-reference/keywords/if-else.md)