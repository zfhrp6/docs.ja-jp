---
title: '\ 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604238"
---
# <a name="-operator-visual-basic"></a>\ 演算子 (Visual Basic)
2 つの数値を除算し、整数の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須。 任意の数式。  
  
 `expression2`  
 必須。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含むすべての数値型と`Decimal`です。  
  
## <a name="result"></a>結果  
 結果は整数の商`expression1`で割った値`expression2`、小数部分を破棄し、整数部分のみを保持します。 これは呼ば*切り捨て*です。  
  
 結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。  
  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)小数部分の残りの部分を保持するフルの商を返します。  
  
## <a name="remarks"></a>コメント  
 除算を実行する前に、Visual Basic に任意の浮動小数点の数値式の変換を試みます`Long`です。 場合`Option Strict`は`On`、コンパイラ エラーが発生します。 場合`Option Strict`は`Off`、<xref:System.OverflowException>値の範囲外の場合は、 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)です。 変換`Long`対象にも*銀行型丸め*です。 詳細についてを参照してください「小数部分」[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)です。  
  
 場合`expression1`または`expression2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`expression2`を 0 に評価される、`\`演算子をスロー、<xref:System.DivideByZeroException>例外。 これは、すべての数値データ型のオペランドの場合は true です。  
  
> [!NOTE]
>  `\`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`\`整数除算を実行する演算子です。 結果は、破棄された後に 2 つのオペランドの商の整数を表す整数です。  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 前の例の式では、2、3、33、および、~ 22 日の値をそれぞれ返します。  
  
## <a name="see-also"></a>関連項目  
 [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
