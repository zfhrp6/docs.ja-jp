---
title: "?? 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a49d36b8580812c08e9ee080a9602d9fc2027ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>?? 演算子 (C# リファレンス)
`??` 演算子は、null 合体演算子と呼ばれます。  左側のオペランドが null 値でない場合には左側のオペランドを返し、null 値である場合には右側のオペランドを返します。  
  
## <a name="remarks"></a>コメント  
 null 許容型は、型のドメインの値を表すことができ、値は未定義でもかまいません (その場合、値は null になります)。 使用することができます、`??`適切な値 (右側のオペランド) を返す演算子の構文上の表現力左のオペランドが null 許容型の値が null が場合にします。 `??` 演算子を使用せずに、null 非許容値型に対して null 許容値型を割り当てると、コンパイル時にエラーが発生します。 null 許容値型が定義されていない場合にキャストを使用すると、`InvalidOperationException` 例外がスローされます。  
  
 詳細については、「[ull 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。  
  
 ?? の結果は、 たとえ両方の引数が定数であった場合でも、定数とは見なされません。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)  
 ['Lifted' の正確な意味](http://go.microsoft.com/fwlink/?LinkID=112382)
