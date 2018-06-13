---
title: '% 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: b906feb22aaec97e58da562b615baae01f3e0719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271073"
---
# <a name="-operator-c-reference"></a>% 演算子 (C# リファレンス)
剰余演算子 (`%`) は、最初のオペランドを 2 番目のオペランドで除算した後の剰余を計算します。 すべての数値型には定義済みの剰余演算子があります。 
  
## <a name="remarks"></a>コメント  
 式 `a % b` は常に `(-b, b)` の範囲の値を返します。`b` または `-b` が返されることはありません。被除数の符号が保持されます。 整数除算の場合、剰余演算子はルール `a % b = a - (a / b) * b` を満たします。
  
 これを正規剰余と混同しないでください。正規剰余は同様のルールを満たしますが、切り捨て除算であり、`[0, b)` の範囲の値を返します。 C# には、正規剰余の演算子はありません。 ただし、動作は正の被除数と同じです。
  
 ユーザー定義型は `%` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>コメント  
 double 型に関連する丸めエラーに注意してください。  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
