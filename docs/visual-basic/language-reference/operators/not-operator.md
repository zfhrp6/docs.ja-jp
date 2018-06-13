---
title: Not 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 332cee57c8d25d7f51737e01e70ba515d50bd6e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604394"
---
# <a name="not-operator-visual-basic"></a>Not 演算子 (Visual Basic)
論理否定を実行、`Boolean`式、または数値式のビットごとの否定。  
  
## <a name="syntax"></a>構文  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`または数値式です。  
  
 `expression`  
 必須。 どの`Boolean`または数値式です。  
  
## <a name="remarks"></a>コメント  
 `Boolean`式では、次の表に示す方法`result`決定されます。  
  
|場合`expression`は|値`result`は|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 数値式の場合、`Not`演算子が任意の数値式のビット値を反転し、対応するにビットを設定`result`次の表のとおりです。  
  
|場合内のビット`expression`は|内のビット`result`は|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確に実行されるようにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 結果のデータ型は、ブール型の否定の`Boolean`します。 ビットごとの否定の結果のデータ型は、のと同じ`expression`です。 ただし、式が場合`Decimal`、結果は`Long`します。  
  
## <a name="overloading"></a>オーバーロード  
 `Not`演算子を指定できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できますその動作のオペランドは、そのクラスまたは構造体の型を持つときにすることを意味します。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Not`に対して論理否定演算を実行する演算子、`Boolean`式。 結果は、`Boolean`式の値の逆を表す値です。  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 前の例の結果を生成する`False`と`True`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Not`数値式のビットごとの論理否定演算を実行する演算子です。 結果のパターン内のビットは符号ビットを含めて、オペランドのパターンに対応するビットの逆に設定されます。  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 前の例では、それぞれ – 11、– 9、および – 7 の結果を生成します。  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
