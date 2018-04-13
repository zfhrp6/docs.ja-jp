---
title: / 演算子 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>/ 演算子 (C# リファレンス)
除算演算子 (`/`) は、1 つ目のオペランドを 2 つ目のオペランドで除算します。 すべての数値型には定義済みの除算演算子があります。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `/` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 `/` 演算子のオーバーロードは、[/= 演算子](division-assignment-operator.md)を暗黙的にオーバーロードします。  
  
 2 つの整数を除算した場合、結果は常に整数になります。 たとえば、7 / 3 の結果は 2 となります。 7 / 3 の余りを計算するには、剰余演算子 ([%](../../../csharp/language-reference/operators/modulus-operator.md)) を使用します。 商を有理数または分数として取得するには、被除数または除数の型を `float` または `double` にします。 除数または被除数を 10 進数として表現する場合は、次の例のように、小数点の右側に数字を配置することで、暗黙的に型を割り当てることができます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
