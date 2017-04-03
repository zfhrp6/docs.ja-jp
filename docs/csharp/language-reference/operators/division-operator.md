---
title: "/ 演算子 (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 21
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 387be8c240001557722b4a30b785637c72c9be37
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-c-reference"></a>/ 演算子 (C# リファレンス)
除算演算子 (`/`) は、1 つ目のオペランドを 2 つ目のオペランドで除算します。 すべての数値型には定義済みの除算演算子があります。  
  
## <a name="remarks"></a>コメント  
 ユーザー定義型は `/` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 `/` 演算子のオーバーロードは、[/= 演算子](division-assignment-operator.md)を暗黙的にオーバーロードします。  
  
 2 つの整数を除算した場合、結果は常に整数になります。 たとえば、7 / 3 の結果は 2 となります。 7 / 3 の余りを計算するには、剰余演算子 ([%](../../../csharp/language-reference/operators/modulus-operator.md)) を使用します。 商を有理数または分数として取得するには、被除数または除数の型を `float` または `double` にします。 除数または被除数を 10 進数として表現する場合は、次の例のように、小数点の右側に数字を配置することで、暗黙的に型を割り当てることができます。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

