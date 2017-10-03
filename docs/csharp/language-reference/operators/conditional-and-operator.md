---
title: "&amp;&amp; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1da61947cbc85e5b3045513e99e013d1e4fae4b3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; 演算子 (C# リファレンス)
条件 AND 演算子 (`&&`) では `bool` オペランドの論理 AND が実行されますが、2 番目のオペランドは必要な場合にのみ評価されます。  
  
## <a name="remarks"></a>コメント  
 次の演算は、  
  
```  
x && y  
```  
  
 次の演算に対応しています。  
  
```  
x & y  
```  
  
 ただし `x` が `false` の場合は、AND 演算の結果は `y` の値に関係なく `false` となるため、`y` は評価されません。 これは、"ショートサーキット" 評価と呼ばれます。  
  
 条件 AND 演算子はオーバーロードできませんが、通常の論理演算子、[true](../../../csharp/language-reference/keywords/true.md) 演算子、[false](../../../csharp/language-reference/keywords/false.md) 演算子のオーバーロードは、条件論理演算子の制約付きのオーバーロードとも見なされます。  
  
## <a name="example"></a>例  
 次の例では、2 番目の `if` ステートメントの条件式で最初のオペランドのみが評価されます。これは、このオペランドが `false` を返すからです。  
  
 [!code-cs[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

