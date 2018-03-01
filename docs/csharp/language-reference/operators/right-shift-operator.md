---
title: "&gt;&gt; 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; 演算子 (C# リファレンス)
右シフト演算子 (`>>`) は、最初のオペランドを 2 番目のオペランドで指定されたビット数だけ右にシフトします。  
  
## <a name="remarks"></a>コメント  
 最初のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [uint](../../../csharp/language-reference/keywords/uint.md) (32 ビット値) である場合、シフト数は、2 番目のオペランド (2 番目のオペランドと 0x1f) の下位 5 ビットで指定されます。  
  
 最初のオペランドが [long](../../../csharp/language-reference/keywords/long.md) または [ulong](../../../csharp/language-reference/keywords/ulong.md) (64 ビット値) である場合、シフト数は、2 番目のオペランド (2 番目のオペランドと 0x3f) の下位 6 ビットで指定されます。  
  
 最初のオペランドが [int](../../../csharp/language-reference/keywords/int.md) または [long](../../../csharp/language-reference/keywords/long.md) である場合、右シフトは算術演算シフトになります (空の上位ビットが符号ビットに設定されます)。 最初のオペランドの型が [uint](../../../csharp/language-reference/keywords/uint.md) または [ulong](../../../csharp/language-reference/keywords/ulong.md) である場合、右シフトは論理シフトになります (上位ビットはゼロで埋められます)。  
  
 ユーザー定義型は、`>>` 演算子をオーバーロードすることができます。最初のオペランドの型は、ユーザー定義型である必要があり、2 番目のオペランドの型は [int](../../../csharp/language-reference/keywords/int.md) でなければなりません。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
