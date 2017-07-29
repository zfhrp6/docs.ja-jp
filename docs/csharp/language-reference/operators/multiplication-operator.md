---
title: "* 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
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
ms.openlocfilehash: 165ca8f797eb8d03ae1dec8c0ec5e1f4b31cb050
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>* 演算子 (C# リファレンス)
そのオペランドの積を計算する乗算演算子 (`*`)。  また、ポインターへの読み書きを可能にする逆参照演算子。  
  
## <a name="remarks"></a>コメント  
 すべての数値型には定義済みの乗算演算子があります。  
  
 `*` 演算子は、ポインターの種類の宣言、およびポインターの逆参照にも使用されます。 この演算子は、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードの使用によって示され、[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを必要とする、unsafe コンテキストでのみ使用できます。  逆参照演算子は、間接演算子とも呼ばれます。  
  
 ユーザー定義型は二項 `*` 演算子をオーバーロードできます (「[演算子](../../../csharp/language-reference/keywords/operator.md)」を参照)。 二項演算子をオーバーロードすると、対応する代入演算子がある場合、これも暗黙的にオーバーロードされます。  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>例  
 [!code-cs[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [C# 演算子](../../../csharp/language-reference/operators/index.md)

