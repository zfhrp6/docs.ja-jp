---
title: += 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: f12a0560d984f871110c02f1df2c2ec42b68809b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604017"
---
# <a name="-operator-visual-basic"></a>+= 演算子 (Visual Basic)
数値型の変数またはプロパティの値に数値式の値を追加し、結果を変数またはプロパティに代入します。 連結するためにも使用する、`String`式、`String`変数やプロパティと、割り当て、その結果を変数またはプロパティ。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値または`String`変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数値または`String`式。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`+=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
 `+=`演算子が変数またはプロパティの左側にするには、その右側の値を追加し、結果を変数またはプロパティの左側に代入します。 `+=`連結する演算子を使用することも、 `String` 、右辺の式、`String`変数またはプロパティに割り当て、その結果、変数を左、またはプロパティの左側にします。  
  
> [!NOTE]
>  使用すると、`+=`演算子ができないことがありますを追加または文字列の連結が発生するかどうかを判断します。 使用して、`&=`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。  
  
 この代入演算子は、拡大縮小ではなく変換のコンパイル環境で厳密なセマンティクスを適用する場合、暗黙的に実行します。 これらの変換の詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)です。 厳密なと制限の緩やかなセマンティクスの詳細については、次を参照してください。 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。  
  
 寛容が許可されている場合、`+=`演算子によって実行されるものと同じ文字列と数値の変換のさまざまなを暗黙的に実行する、`+`演算子。 これらの変換の詳細については、「 [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)です。  
  
## <a name="overloading"></a>オーバーロード  
 `+`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 オーバー ロード、`+`演算子の動作に影響、`+=`演算子。 コードで使用する場合`+=`クラスまたはオーバー ロードする構造体で`+`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`+=`と他の 1 つの変数の値を結合する演算子です。 最初の部分を使用して`+=`に 1 つの値を加算する数値変数を使用します。 2 番目の部分を使用して`+=`で`String`変数を別の 1 つの値を連結します。 どちらの場合は、結果は、最初の変数に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 値`num1`13、およびの値が、 `str1` 「103」になります。  
  
## <a name="see-also"></a>関連項目  
 [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
