---
title: "方法:&2; つのオブジェクトが (Visual Basic) の場合と同じであるかどうかを判断する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3a853d9f958829eeb0fb42ecbcdae7ba912c89ed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>方法:&2; つのオブジェクトが同一であるかどうか判別する (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、2 つの変数参照が同一と見なされます、ポインターが同じ場合、つまり、両方の変数がメモリ内の同じクラス インスタンスを指している場合。 たとえば、Windows フォーム アプリケーションでは、場合を判断する比較するかどうか、現在のインスタンス (`Me`) など、特定のインスタンスと同じ`Form2`します。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ポインターを比較する&2; つの演算子を提供します。 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)返します`True`場合は、オブジェクトが同一で、および[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)を返します`True`されていない場合。  
  
## <a name="determining-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを判断します。  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを判断するには  
  
1.  セットアップ、 `Boolean`&2; つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`Is`演算子のオペランドとして&2; つのオブジェクトを指定しています。  
  
     `Is`返します`True`オブジェクトが同じクラスのインスタンスを指している場合。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同一でないかどうかを判断します。  
 2 つのオブジェクトが同一で可能でありを結合する厄介なアクションの実行することが必要`Not`と`Is`、たとえば`If Not obj1 Is obj2`です。 このようなケースで使用できます、`IsNot`演算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同一でないかどうかを判断するには  
  
1.  セットアップ、 `Boolean`&2; つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`IsNot`演算子のオペランドとして&2; つのオブジェクトを指定しています。  
  
     `IsNot`返します`True`場合は、オブジェクトが同じクラスのインスタンスを指すようにします。  
  
## <a name="example"></a>例  
 次の例では、組の`Object`変数を同じクラスのインスタンスを指しているかを参照してください。  
  
 [!code-vb[VbVbalrKeywords&#14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 前の例では、次の出力が表示されます。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [方法:&2; つのオブジェクトが関連するかどうかを判別します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
