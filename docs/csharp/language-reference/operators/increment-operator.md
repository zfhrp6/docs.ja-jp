---
title: "++ 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>++ 演算子 (C# リファレンス)
インクリメント演算子 (`++`) は、オペランドを 1 ずつインクリメントします。 インクリメント演算子はそのオペランド ( `++variable` および `variable++`) の前後に指定できます。  
  
## <a name="remarks"></a>コメント  
 1 番目の形式は前置インクリメント演算です この演算の結果は、インクリメント後のオペランドの値になります。  
  
 2 番目の形式は後置インクリメント演算です。 この演算の結果は、インクリメント前のオペランドの値になります。  
  
 数値型と列挙型には事前定義のインクリメント演算子があります。 ユーザー定義型は `++` 演算子をオーバーロードできます。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## <a name="example"></a>例  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)
