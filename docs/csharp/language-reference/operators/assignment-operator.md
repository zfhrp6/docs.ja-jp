---
title: "= 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>= 演算子 (C# リファレンス)
代入演算子 (`=`) では、右辺のオペランドの値が、左辺のオペランドで示された格納場所、プロパティ、またはインデクサーに格納され、その値が結果として返されます。 両側のオペランドは、同じ型である必要があります (または、右辺のオペランドが、左辺のオペランドの型に暗黙に変換できる必要があります)。  
  
## <a name="remarks"></a>コメント  
 代入演算子はオーバーロードできません。 ただし、暗黙の変換演算子を型に定義すると、その型で代入演算子を使用できるようになります。 詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
