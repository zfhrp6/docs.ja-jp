---
title: /= 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604095"
---
# <a name="-operator-visual-basic"></a>/= 演算子 (Visual Basic)
変数またはプロパティの値式の値で除算し、浮動小数点の結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値型の変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数式。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`/=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
 `/=`最初は、変数または (演算子の左側にある) のプロパティの値が演算子によって (演算子の右側にある) の式の値で除算します。 演算子は、変数やプロパティにし、その操作の浮動小数点の結果を割り当てます。  
  
 このステートメントは、代入、`Double`を変数または左側のプロパティの値。 場合`Option Strict`は`On`、`variableorproperty`する必要があります、`Double`です。 場合`Option Strict`は`Off`、Visual Basic の暗黙的な変換を実行およびを結果として得られる値を割り当てます`variableorproperty`、実行時に可能性のあるエラーとします。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。  
  
## <a name="overloading"></a>オーバーロード  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 オーバー ロード、`/`演算子の動作に影響、`/=`演算子。 コードで使用する場合`/=`クラスまたはオーバー ロードする構造体で`/`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`/=`演算子を 1 つに分割`Integer`変数の 2 番目と割り当て、最初の変数への商。  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
