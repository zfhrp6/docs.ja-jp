---
title: "方法: 演算子プロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 2403e7a8270c17a8db5417cd8394fd47c373d493
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>方法: 演算子プロシージャを呼び出す (Visual Basic)
演算子プロシージャを呼び出すには、式で演算子のシンボルを使用します。 場合、変換演算子を呼び出す、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)に値を別の&1; つのデータ型に変換します。  
  
 演算子プロシージャを明示的に呼び出す必要はありません。 同様に、演算子を使用する、または`CType`関数、代入ステートメント、または式、演算子を使用すると、通常は同じようにします。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]演算子プロシージャの呼び出しを使用します。  
  
 クラスまたは構造体で、演算子を定義することと呼ばれる*オーバー ロード*演算子。  
  
### <a name="to-call-an-operator-procedure"></a>演算子プロシージャを呼び出す  
  
1.  通常の方法で、式の中で演算子のシンボルを使用します。  
  
2.  オペランドのデータ型が適切な演算子の場合と、正しい順序であることを確認します。  
  
3.  演算子は、期待どおりに、式の値に作用します。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>変換演算子プロシージャを呼び出す  
  
1.  使用`CType`式の内部です。  
  
2.  オペランドのデータ型が適切な変換して、正しい順序であることを確認します。  
  
3.  `CType`変換演算子プロシージャの呼び出しを変換後の値を返します。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.TimeSpan>構造体、それらを加算、および&3; つ目の結果を格納<xref:System.TimeSpan>構造体</xref:System.TimeSpan></xref:System.TimeSpan>。 <xref:System.TimeSpan>構造体がいくつかの標準的な演算子をオーバー ロードする演算子プロシージャを定義します</xref:System.TimeSpan>。  
  
 [!code-vb[VbVbcnProcedures #&29;](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <xref:System.TimeSpan>、標準のオーバー ロード`+`演算子で、前の例では演算子プロシージャの値を計算するとき`combinedSpan`</xref:System.TimeSpan>。  
  
 メッセージ交換演算子プロシージャの呼び出しの例は、次を参照してください。[方法: クラスを定義演算子を使用して](./how-to-use-a-class-that-defines-operators.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 使用する演算子を定義、クラスまたは構造体を使用していることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)   
 [方法: 演算子を定義](./how-to-define-an-operator.md)   
 [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)   
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)   
 [拡大変換](../../../../visual-basic/language-reference/modifiers/widening.md)   
 [縮小変換](../../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [方法: 構造体を宣言](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
