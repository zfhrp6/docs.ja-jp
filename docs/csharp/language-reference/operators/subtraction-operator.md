---
title: '- 演算子 (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 315d8cf47cc0819e124c1c08546ede580918f328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a>- 演算子 (C# リファレンス)
`-` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。  
  
## <a name="remarks"></a>コメント  
 すべての数値型には、単項 `-` 演算子が事前定義されています。 数値型に対する単項 `-` 演算の結果は、オペランドの反転の数値となります。  
  
 最初のオペランドから 2 番目のオペランドを減算するために、すべての数値型と列挙型に 2 項 `-` 演算子が事前定義されています。  
  
 2 項 `-` 演算子はデリゲート型にも備わっており、その場合、デリゲートの削除が実行されます。  
  
 単項 `-` 演算子と 2 項 `-` 演算子は、ユーザー定義型でオーバーロードすることができます。 詳細については、「[operator (C# Reference) (operator (C# リファレンス))](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
