---
title: "/= 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5e105bf11f5413d77d62be4177ed22ba420312c3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>/= 演算子 (C# リファレンス)
除算代入演算子です。  
  
## <a name="remarks"></a>コメント  
 次のような `/=` 代入演算子を使用する式があるとします  
  
```  
x /= y  
```  
  
 上記の式は、次の式と同じです。  
  
```  
x = x / y  
```  
  
 ただし、`x` が評価されるのは 1 回だけです。 [/ 演算子](../../../csharp/language-reference/operators/division-operator.md)は、数値型の除算のために事前定義されています。  
  
 `/=` 演算子は直接オーバーロードできませんが、ユーザー定義型では [/ 演算子](../../../csharp/language-reference/operators/division-operator.md)をオーバーロードできます。(「[演算子](../../../csharp/language-reference/keywords/operator.md)」参照)。 すべての複合代入演算子において、二項演算子をオーバーロードすると、同等の複合代入が暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

