---
title: ^ 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 426c3e9913dadda1091f4ba53c66c6b65e40e768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604446"
---
# <a name="-operator-visual-basic"></a>^ 演算子 (Visual Basic)
別の数値の累乗する数値を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>指定項目  
 `number`  
 必須。 任意の数式。  
  
 `exponent`  
 必須。 任意の数式。  
  
## <a name="result"></a>結果  
 結果は`number`の累乗`exponent`、として常に、`Double`値。  
  
## <a name="supported-types"></a>サポートされている型  
 `Double`。 任意の異なる型のオペランドに変換`Double`です。  
  
## <a name="remarks"></a>コメント  
 Visual Basic での累乗を常に実行する、 [Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)です。  
  
 値`exponent`、小数部は、負の値、またはその両方です。  
  
 1 つの式で複数の指数演算を実行すると、`^`としては、左から右に演算子が評価されます。  
  
> [!NOTE]
>  `^`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`^`べき乗の指数部の累乗にする演算子です。 最初のオペランドが 2 番目の累乗になります。  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 前の例では、次の結果が生成されます。  
  
 `exp1` 4 (2 乗) に設定されます。  
  
 `exp2` 19683 (3 乗、次にその値が 2 乗) に設定されます。  
  
 `exp3` -125 (-5 乗) に設定されます。  
  
 `exp4` 625 (4 乗-5) に設定されます。  
  
 `exp5` 2 (8 の立方根) に設定されます。  
  
 `exp6` 0.5 (1.0 8 の立方根で割った値) に設定されます。  
  
 上記の例の式のかっこの中の重要性に注意してください。 ため*演算子の優先順位*、Visual Basic は通常は、 `^` 、それ以外の前に、の演算子も、単項`–`演算子。 場合`exp4`と`exp6`が計算されたかっこがない場合、次の結果が生成されるとします。  
  
 `exp4 = -5 ^ 4` – (4 乗 5) として計算される-625 になります。  
  
 `exp6 = 8 ^ -1.0 / 3.0` (– 1 power または 0.125 8) として計算が 3.0 では 0.041666666666666666666666666666667 ことになりますで割った値します。  
  
## <a name="see-also"></a>関連項目  
 [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
