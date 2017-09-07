---
title: "方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
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
ms.openlocfilehash: c5daa8525f45c123dabb0f59dfd29385b9e50354
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド)
オブジェクトはポリモーフィックであるため、基本クラス型の変数で派生型を保持できます。 派生型のメソッドにアクセスするには、値をキャストして派生型に戻す必要があります。 このような場合に単純にキャストを実行すると、<xref:System.InvalidCastException> がスローされるリスクが生じます。 このため、C# には、[is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が用意されています。 これらの演算子を使用すると、例外がスローされることなくキャストが成功するかどうかをテストできます。 通常は、`as` 演算子の方が、キャストが正しく実行できる場合はキャスト値を実際に返すため、より効率的です。 `is` 演算子はブール値のみを返します。 したがって、オブジェクトの型の確認のみ行い、キャストは行う必要がない場合に使用できます。  
  
## <a name="example"></a>例  
 `is` 演算子と `as` 演算子を使用して、例外がスローされるリスクを回避しながら、参照型を別の参照型にキャストする方法を次の例に示します。 この例では、null 許容値型で `as` 演算子を使用する方法も示します。  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [型](../../../csharp/programming-guide/types/index.md)   
 [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Null 許容型](../../../csharp/programming-guide/nullable-types/index.md)

