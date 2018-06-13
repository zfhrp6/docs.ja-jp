---
title: '方法: 演算子プロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649969"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>方法: 演算子プロシージャを呼び出す (Visual Basic)
演算子プロシージャを呼び出すには、式で演算子のシンボルを使用します。 場合は、変換演算子を呼び出す、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)に値を別の 1 つのデータ型に変換します。  
  
 演算子プロシージャを明示的に呼び出すことはありません。 同様に、演算子を使用する、または`CType`関数、代入ステートメントまたは式、演算子を通常使用するのと同様にします。 Visual Basic では、演算子プロシージャ呼び出しを行います。  
  
 クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。  
  
### <a name="to-call-an-operator-procedure"></a>演算子プロシージャを呼び出しています  
  
1.  通常の方法で、式で演算子のシンボルを使用します。  
  
2.  オペランドのデータ型が演算子の場合、正しい順序では適切であることを確認します。  
  
3.  演算子は、期待どおりに、式の値に作用します。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>変換演算子プロシージャを呼び出しています  
  
1.  使用して`CType`式の内部です。  
  
2.  オペランドのデータ型は、変換して、正しい順序で適切なことを確認します。  
  
3.  `CType` 変換演算子プロシージャの呼び出しを変換後の値を返します。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.TimeSpan>構造体を加算してを 3 つ目の結果を格納<xref:System.TimeSpan>構造体。 <xref:System.TimeSpan>構造体は、いくつかの標準的な演算子をオーバー ロードする演算子プロシージャを定義します。  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <xref:System.TimeSpan>標準をオーバー ロード`+`演算子を前の例では演算子プロシージャの値を計算するとき`combinedSpan`です。  
  
 メッセージ交換演算子プロシージャの呼び出しの例は、次を参照してください。[する方法: クラスにその定義の演算子を使用して](./how-to-use-a-class-that-defines-operators.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 使用する演算子を定義クラスまたは構造体を使用していることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : 演算子を定義する](./how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](./how-to-define-a-conversion-operator.md)  
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
