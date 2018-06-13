---
title: '&lt;&lt;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 559624f7097f90d374ee83e3c0a9ac97d9f93444
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600728"
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;= 演算子 (Visual Basic)
変数またはプロパティの値に対して算術左シフトを実行し、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 整数型の変数またはプロパティ (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 拡大変換をデータ型の数値式`Integer`です。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`<<=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
 `<<=`演算子は最初、変数またはプロパティの値に算術左シフトを実行します。 演算子は、その変数またはプロパティにし、その操作の結果を割り当てます。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。 算術左シフト、結果のデータ型の範囲を超えてシフトは破棄され、右側の空いたビット位置は 0 に設定されます。  
  
## <a name="overloading"></a>オーバーロード  
 [<< 演算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 オーバー ロード、`<<`演算子の動作に影響、`<<=`演算子。 コードで使用する場合`<<=`クラスまたはオーバー ロードする構造体で`<<`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`<<=`のビット パターンをシフトする演算子、`Integer`変数に指定された量と割り当ての結果で変数のままです。  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [<< 演算子](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
