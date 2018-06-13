---
title: If 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 192309a7ca728feb300e867bf2340e669e9da16c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603965"
---
# <a name="if-operator-visual-basic"></a>If 演算子 (Visual Basic)
ショート サーキット評価を条件に応じて 2 つの値を返しますを使用します。 `If`演算子は、3 つの引数、または 2 つの引数を指定して呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>演算子は、3 つの引数で呼び出された場合  
 ときに`If`が呼び出された 3 つの引数を使用すると、最初の引数としてキャスト可能な値に評価する必要があります、`Boolean`です。 ある`Boolean`が評価され、返されるその他の 2 つの引数の値が決定されます。 次のリストの適用される場合にのみ、`If`演算子が 3 つの引数を使用して呼び出されました。  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`argument1`|必須。 `Boolean`。 その他の引数を評価し、返すを決定します。|  
|`argument2`|必須。 `Object`。 評価されると返される場合`argument1`に評価される`True`です。|  
|`argument3`|必須。 `Object`。 評価されると返される場合`argument1`に評価`False`場合`argument1`は、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)です。|  
  
 `If`が 3 つの引数で呼び出される演算子の動作と同様に、`IIf`関数を使用する点を除いてショート サーキット評価します。 `IIf`関数評価は常に 3 つすべての引数の一方、`If`を 3 つの引数を持つ演算子が評価される 2 つのみです。 最初の`If`引数が評価され、結果としてキャスト、`Boolean`値、`True`または`False`です。 値が場合`True`、`argument2`が評価され、その値が返されますが、`argument3`は評価されません。 場合の値、`Boolean`式が`False`、`argument3`が評価され、その値が返されますが、`argument2`は評価されません。 次の例では、使用する`If`3 つの引数を使用する場合。  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 次の例は、の値を示しています。 ショート サーキット評価します。 例では、変数に分割する 2 つの試行を示しています。`number`変数によって`divisor`場合を除きます`divisor`は 0 です。 その場合は、0 を返す必要があるし、は行われません、実行時エラーになるため、除算を実行します。 `If`ショート サーキット評価の式の使用、2 番目または最初の引数の値に応じて、3 番目の引数のいずれかを評価します。 最初の引数が true の場合は、除数 0 ではないと 2 番目の引数を評価し、除算を実行しても安全です。 最初の引数が false の場合は、3 番目の引数のみが評価され、0 が返されます。 そのため、除数が 0 の場合は行われません、除算とエラーは発生しませんを実行します。 ただし、ため`IIf`使用しないショート サーキット評価、最初の引数が false の場合も、2 番目の引数が評価されます。 これにより、実行時に 0 除算エラーです。  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>演算子が 2 つの引数で呼び出された場合  
 1 番目の引数`If`を省略できます。 これにより、2 つの引数を使用して呼び出される演算子です。 次のリストの適用される場合にのみ、`If`演算子が 2 つの引数と呼ばれます。  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`argument2`|必須。 `Object`。 参照または null 許容型にする必要があります。 評価され、以外の値に評価された場合に返される`Nothing`です。|  
|`argument3`|必須。 `Object`。 評価されると返される場合`argument2`に評価される`Nothing`です。|  
  
 ときに、`Boolean`引数を省略すると、最初の引数が参照または null 許容型にする必要があります。 最初の引数が評価された場合`Nothing`、2 番目の引数の値が返されます。 それ以外の場合は、最初の引数の値が返されます。 次の例では、この評価のしくみを示しています。  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
