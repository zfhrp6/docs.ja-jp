---
title: '* 演算子 (C# リファレンス)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>* 演算子 (C# リファレンス)
乗算演算子 (`*`) は、そのオペランドの積を計算します。 すべての数値型には定義済みの乗算演算子があります。  

また、`*` はポインターへの読み書きを可能にする逆参照演算子としても機能します。
  
## <a name="remarks"></a>コメント  
 `*` 演算子は、ポインターの種類の宣言、およびポインターの逆参照にも使用されます。 この演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードの使用によって示され、[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを必要とする、unsafe コンテキストでのみ使用できます。  逆参照演算子は、間接演算子とも呼ばれます。  
  
 ユーザー定義型は二項 `*` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
