---
title: "~ 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: c7245700f78ff52a98c499d895c7eb2f95efe5b6
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="-operator-c-reference"></a>~ 演算子 (C# リファレンス)
`~` 演算子は、ビット単位の補数演算をオペランドに実行します。これにより、各ビットが反転します。 ビット単位の補数演算は [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) に事前定義されています。  
  
> [!NOTE]
>  `~` シンボルもファイナライザーの宣言に使用されます。 詳細については、「[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md)」 (ファイナライザー) を参照してください。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `~` 演算子をオーバーロードできます。 詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)   
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)
