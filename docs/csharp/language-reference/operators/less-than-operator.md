---
title: "&lt; 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 76d53d4c943c886f6b8c8a68e2b8bb12bc9a9d6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lt-operator-c-reference"></a>&lt; 演算子 (C# リファレンス)
すべての数値型と列挙型で "より小さい" 関係演算子 (`<`) が定義されます。これは、最初のオペランドが 2 番目のオペランドより小さい場合に `true` を返し、それ以外の場合、`false` を返します。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `<` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 `<` をオーバーロードする場合は、[>](../../../csharp/language-reference/operators/greater-than-operator.md) もオーバーロードする必要があります。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#24](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
