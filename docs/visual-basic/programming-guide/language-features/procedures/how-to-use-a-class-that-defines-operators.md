---
title: '方法: 演算子を定義するクラスを使用する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 7e1d5698c1e83f0adf1be67245e0726aecaabdac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650606"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>方法: 演算子を定義するクラスを使用する (Visual Basic)
クラスまたは独自の演算子を定義する構造体を使用している場合は、Visual Basic からこれらの演算子を表示できます。  
  
 クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。  
  
## <a name="example"></a>例  
 次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、SQL 文字列と Visual Basic の文字列間で双方向でします。 使用して`CType(` *SQL 文字列式*、 `String)` SQL 文字列を文字列に変換する Visual Basic、および`CType(` *Visual Basic の文字列式*、 <xref:System.Data.SqlTypes.SqlString> `)`に逆方向に変換します。  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <xref:System.Data.SqlTypes.SqlString>変換演算子を定義する構造体 ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`です。 割り当てるステートメントを`title`に`jobTitle`では、最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数呼び出しで、2 つ目は使用します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 使用する演算子を定義クラスまたは構造体を使用していることを確認します。 クラスまたは構造体の定義がすべての演算子はオーバー ロード可能なこととは限りません。 利用可能な演算子の一覧は、次を参照してください。 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)です。  
  
 含める、適切な`Imports`、ソース ファイルの先頭に、SQL 文字列の文 (ここでは<xref:System.Data.SqlTypes>)。  
  
 プロジェクトには、System.Data、および System.XML への参照をいる必要があります。  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : 演算子を定義する](./how-to-define-an-operator.md)  
 [方法 : 変換演算子を定義する](./how-to-define-a-conversion-operator.md)  
 [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
