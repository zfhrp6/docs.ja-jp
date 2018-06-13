---
title: '&gt;&gt;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604108"
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= 演算子 (Visual Basic)
変数またはプロパティの値に対して算術右シフトを実行し、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 整数型の変数またはプロパティ (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 拡大変換をデータ型の数値式`Integer`です。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`>>=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
 `>>=`演算子は最初、変数またはプロパティの値に算術右シフトを実行します。 演算子は、変数またはプロパティにし、その操作の結果を割り当てます。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。 算術右シフトの右端のビット位置を超えてシフトは破棄され、最上位ビットは左側にある空いたビット位置に反映されます。 つまり、`variableorproperty`負の値を持つ、空いた位置は 1 つに設定します。 場合`variableorproperty`が正の値か、空いた位置を 0 に設定されて、データ型が符号なしの型の場合は、します。  
  
## <a name="overloading"></a>オーバーロード  
 [>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 オーバー ロード、`>>`演算子の動作に影響、`>>=`演算子。 コードで使用する場合`>>=`クラスまたはオーバー ロードする構造体で`>>`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`>>=`のビット パターンをシフトする演算子、`Integer`変数指定の量と割り当てを変数に結果を右。  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
