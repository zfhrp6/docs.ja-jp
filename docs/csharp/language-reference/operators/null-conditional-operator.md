---
title: "?? 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "??_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "?? 演算子 [C#]"
  - "合体演算子 [C#]"
  - "条件 AND 演算子 (&&) [C#]"
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# ?? 演算子 (C# リファレンス)
`??` 演算子は、null 合体演算子と呼ばれます。左側のオペランドが null 値でない場合には左側のオペランドを返し、null 値である場合には右側のオペランドを返します。  
  
## 解説  
 null 許容型は、型のドメインの値を表すことができ、値は未定義でもかまいません \(その場合、値は null になります\)。  `??` 演算子の構文を使用して、左側のオペランドが null 許容型でその値が null である場合に、適切な値 \(右側のオペランド\) を返すことができます。  `??` 演算子を使用せずに、null 非許容値型に対して null 許容値型を割り当てると、コンパイル時にエラーが発生します。  null 許容値型が定義されていない場合にキャストを使用すると、`InvalidOperationException` 例外がスローされます。  
  
 詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
 ?? 演算子の結果は、たとえ両方の引数が定数であった場合でも、定数とは見なされません。  
  
## 使用例  
 [!code-cs[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)   
 [What Exactly Does 'Lifted' mean? \('Lifted' の正確な意味\)](http://go.microsoft.com/fwlink/?LinkID=112382)