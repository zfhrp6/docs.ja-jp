---
title: ^= 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 571ef26eb188d9044ec8f6c8e6e4b490780f17a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603497"
---
# <a name="-operator-visual-basic"></a>^= 演算子 (Visual Basic)
変数または式のプロパティの値を生成し、結果を変数またはプロパティに代入します。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 必須。 任意の数値型の変数またはプロパティ。  
  
 `expression`  
 必須。 任意の数式。  
  
## <a name="remarks"></a>コメント  
 左側にある要素、`^=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。 変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
 `^=` (演算子の右側にある) の式の値の累乗演算子が変数または (演算子の左側にある) のプロパティの値にまずを発生させます。 演算子は、変数またはプロパティにし、その操作の結果を割り当てます。  
  
 Visual Basic での累乗を常に実行する、 [Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)です。 任意の異なる型のオペランドに変換`Double`、され、結果は常に`Double`です。  
  
 値`expression`、小数部は、負の値、またはその両方です。  
  
## <a name="overloading"></a>オーバーロード  
 [^ 演算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 オーバー ロード、`^`演算子の動作に影響、`^=`演算子。 コードで使用する場合`^=`クラスまたはオーバー ロードする構造体で`^`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`^=`いずれかの値を上げる演算子`Integer`変数の 2 つ目の変数と割り当て、その結果、最初の変数を電源にします。  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [^ 演算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
