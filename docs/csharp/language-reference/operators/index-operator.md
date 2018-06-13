---
title: '[] 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286030"
---
# <a name="-operator-c-reference"></a>[] 演算子 (C# リファレンス)
角かっこ (`[]`) は、配列、インデクサー、属性に使用されます。 また、ポインターと共に使用することもできます。  
  
## <a name="remarks"></a>コメント  
 配列型は、型の後に `[]` が続きます。  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 配列の要素にアクセスするには、次のように、目的の要素のインデックスを角かっこで囲みます。  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 配列のインデックスが範囲外の場合は、例外がスローされます。  
  
 配列インデックス演算子は、オーバーロードできません。ただし、型はインデクサーと、1 つ以上のパラメーターを受け取るプロパティを定義できます。 インデクサーのパラメーターは配列のインデックスと同じように角かっこで囲みますが、整数でなければならない配列のインデックスとは異なり、インデクサーのパラメーターは任意の型として宣言することができます。  
  
 たとえば、.NET Framework では、任意の型のキーと値を関連付ける `Hashtable` 型を定義しています。  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 角かっこは、[属性](../../../csharp/programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 角かっこを使用して、ポインターにインデックスを作成することができます。  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 境界のチェックは行われません。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [配列](../../../csharp/programming-guide/arrays/index.md)  
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
