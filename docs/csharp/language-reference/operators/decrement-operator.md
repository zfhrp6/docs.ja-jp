---
title: "-- 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a>-- 演算子 (C# リファレンス)
デクリメント演算子 (`--`) は、オペランドを 1 ずつデクリメントします。 デクリメント演算子はそのオペランド ( `--variable` および `variable--`) の前後に指定できます。 1 番目の形式は前置デクリメント演算です。 この演算の結果は、デクリメント "後" のオペランドの値になります。 2 番目の形式は後置デクリメント演算です。 この演算の結果は、デクリメント "前" のオペランドの値になります。  
  
## <a name="remarks"></a>コメント  
 数値型と列挙型には事前定義のデクリメント演算子があります。  
  
 ユーザー定義型は `--` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

