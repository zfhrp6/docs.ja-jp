---
title: "^= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^=_CSharpKeyword
helpviewer_keywords: ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>^= 演算子 (C# リファレンス)
排他的 OR 代入演算子。  
  
## <a name="remarks"></a>コメント  
 次のような形式の式があります。  
  
```  
x ^= y  
```  
  
 これが次のように評価されます。  
  
```  
x = x ^ y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)は整数オペランドにビット演算排他的 OR 操作を実行し、[ブール](../../../csharp/language-reference/keywords/bool.md) オペランドに論理的 OR 操作を実行します。  
  
 ^= 演算子は直接オーバーロードできませんが、ユーザー定義型は [^ 演算子](../../../csharp/language-reference/operators/xor-operator.md)をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
