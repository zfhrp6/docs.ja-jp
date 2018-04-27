---
title: '方法: 2 つのオブジェクトが同一であるかどうか判別する (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 266e878e7f5fa8deb1c8cd91795af8d63ded0177
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>方法: 2 つのオブジェクトが同一であるかどうか判別する (Visual Basic)
Visual basic で 2 つの変数参照が同一と見なされます、ポインターが同じ場合、つまり、両方の変数がメモリ内で同じクラスのインスタンスを指している場合。 たとえば、Windows フォーム アプリケーションでは、場合を決定するを比較するかどうか、現在のインスタンス (`Me`) など、特定のインスタンスと同じ`Form2`です。  
  
 Visual Basic では、ポインターを比較する 2 つの演算子を提供します。 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)を返します`True`オブジェクトが一致する場合、 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)返します`True`されていない場合。  
  
## <a name="determining-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを決定します。  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを決定するには  
  
1.  セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`Is`演算子のオペランドとして 2 つのオブジェクト。  
  
     `Is` 返します`True`場合は、オブジェクトが、同じクラスのインスタンスをポイントします。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同じでないかどうかを決定します。  
 2 つのオブジェクトが同一でないと結合するメッセージが不適切であることができる場合、操作を実行することもあります`Not`と`Is`、たとえば`If Not obj1 Is obj2`します。 このようなケースで使用できます、`IsNot`演算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同一でないかどうかを確認  
  
1.  セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`IsNot`演算子のオペランドとして 2 つのオブジェクト。  
  
     `IsNot` 返します`True`オブジェクトは、同じクラスのインスタンスを指していない場合。  
  
## <a name="example"></a>例  
 次の例の組み合わせをテストする`Object`変数を同じクラスのインスタンスを指しているかを参照してください。  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 前の例では、次の出力が表示されます。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>関連項目  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
