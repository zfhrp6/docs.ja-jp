---
title: Visual Basic の論理演算子とビット処理演算子
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 371d28629b39fb2808ca018ea69da3306a31f50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656153"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic の論理演算子とビット処理演算子
論理演算子は、比較`Boolean`式と戻り値、`Boolean`結果。 `And`、 `Or`、 `AndAlso`、 `OrElse`、および`Xor`演算子は*バイナリ*中に、2 つのオペランドを受け取るため、`Not`演算子は*単項* 1 つのオペランドを受け取るためです。 整数値のビットごとの論理演算これらの演算子の一部も行えます。  
  
## <a name="unary-logical-operator"></a>単項論理演算子  
 [演算子ではなく](../../../../visual-basic/language-reference/operators/not-operator.md)論理実行*否定*上、`Boolean`式。 これには、論理的に反対のオペランドが生成されます。 式が評価された場合`True`、し`Not`を返します`False`以外の場合は、式に`False`、し、`Not`返します`True`です。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>二項論理演算子  
 [And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)論理実行*組み合わせて*2 つの`Boolean`式。 場合に、両方の式が評価される`True`、し、`And`返します`True`です。 少なくとも 1 つの式の評価された場合`False`、し`And`返します`False`です。  
  
 [または演算子](../../../../visual-basic/language-reference/operators/or-operator.md)論理実行*和*または*包含*2 つの`Boolean`式。 いずれかの式が評価された場合`True`、または両方を評価するため`True`、し、`Or`返します`True`です。 どちらの式に評価される場合`True`、`Or`返します`False`です。  
  
 [Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)論理実行*除外*2 つの`Boolean`式。 正確に 1 つの式が評価された場合`True`、両方ではなく、`Xor`返します`True`です。 両方の式が評価される場合`True`に評価される両方または`False`、`Xor`返します`False`です。  
  
 次の例を示しています、 `And`、 `Or`、および`Xor`演算子。  
  
 [!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>ショート サーキット論理操作  
 [AndAlso 演算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)とよく似ていますが、`And`演算子、2 つの論理積を実行するに`Boolean`式。 2 つの重要な違いは`AndAlso`の欠落を表す*ショート サーキット*動作します。 場合は最初の式で、`AndAlso`式に評価される`False`、最終結果を変更できないために、2 番目の式は評価されませんしと`AndAlso`を返します`False`です。  
  
 同様に、 [OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)2 つの論理和の短絡`Boolean`式。 場合は最初の式で、`OrElse`式に評価される`True`、最終結果を変更できないために、2 番目の式は評価されませんしと`OrElse`を返します`True`です。  
  
### <a name="short-circuiting-trade-offs"></a>ショート サーキットのトレードオフ  
 ショート サーキット論理演算の結果を変更することはできません、式を評価されないので、パフォーマンスを向上できます。 ただし、その式は、その他の操作を実行する場合は、これらの操作をスキップ ショート サーキットします。 たとえば、式への呼び出しが含まれている場合、`Function`プロシージャ、式がショート サーキットとに、追加のコードが含まれている場合に、プロシージャが呼び出されません、`Function`は実行されません。 そのため、この関数は、頻度が低い実行可能性があり、正しくテストいない可能性があります。 プログラム ロジックのコードに依存、または、`Function`です。  
  
 次の例は、違いを示しています。 `And`、 `Or`、および対応するショート サーキットします。  
  
 [!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 上記の例では、ことに注意して内の重要なコード`checkIfValid()`呼び出しがショート サーキットの場合は実行されません。 最初の`If`ステートメントの呼び出し`checkIfValid()`にもかかわらず`12 > 45`返します`False`ので、`And`ショート サーキットはありません。 2 番目`If`ステートメントは呼び出しません`checkIfValid()`ので、ときに`12 > 45`を返します`False`、 `AndAlso` short-circuits 2 番目の式。 3 番目`If`ステートメント呼び出し`checkIfValid()`にもかかわらず`12 < 45`を返します`True`ので、`Or`ショート サーキットはありません。 4 番目`If`ステートメント呼び出されません`checkIfValid()`ため、ときに`12 < 45`返します`True`、 `OrElse` short-circuits 2 番目の式。  
  
## <a name="bitwise-operations"></a>ビット処理演算  
 ビットごとの演算では、(基本 2) のバイナリ形式で 2 つの整数値を評価します。 対応する位置のビットを比較し、比較に基づいて値を割り当てます。 次の例を示しています、`And`演算子。  
  
 [!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 前の例の値を設定する`x`を 1 にします。 これは、次の理由で発生します。  
  
-   値はバイナリとして扱われます。  
  
     バイナリ形式の 3 011 を =  
  
     バイナリ形式の 5 101 を =  
  
-   `And`演算子は、一度に 1 つのバイナリ位置 (ビット) のバイナリ表現を比較します。 指定した位置にある両方のビットが 1 の場合は、1 は、結果の位置に配置されます。 どちらかのビットが 0 の場合、0 は、結果の位置に配置されます。 前の例ではこの êaƒnƒ。  
  
     011 (バイナリ形式で 3)  
  
     101 (バイナリ形式の 5)  
  
     001 (バイナリ形式の結果)  
  
-   結果は、10 進数として扱われます。 001 値は 1、バイナリ形式をこのため`x`= 1 です。  
  
 ビットごと`Or`操作似ていますが、ビットごとの一方または両方が 1 の場合、結果のビットを 1 が割り当てられます。 `Xor` 1 つの (両方ではなく)、比較するビットだけが 1 の場合は、1、結果のビットに割り当てられます。 `Not` 1 つのオペランドを受け取るし、符号ビットを含むすべてのビットを反転結果にその値を割り当てます。 これは、正の数値を署名のことを意味`Not`常に負の値を返しますと負の値、`Not`常に正の値または 0 の値を返します。  
  
 `AndAlso`と`OrElse`演算子はビットごとの演算をサポートしていません。  
  
> [!NOTE]
>  ビットごとの演算は、整数型でのみ実行できます。 ビットごとの演算は続行する前に、浮動小数点値を整数型に変換する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
