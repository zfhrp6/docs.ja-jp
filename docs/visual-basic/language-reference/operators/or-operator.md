---
title: Or 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 9e02f619a81ee3c15321dfd44963c1a7d29843ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604771"
---
# <a name="or-operator-visual-basic"></a>Or 演算子 (Visual Basic)
2 つの論理和を求めます`Boolean`式、または 2 つの数値式のビットごとの論理和です。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`または数値式です。 `Boolean`比較、`result`は 2 つの包括的論理和`Boolean`値。 ビットごとの演算`result`は、次の 2 つの数値のビット パターンの包括的論理和を表す数値を指定します。  
  
 `expression1`  
 必須。 どの`Boolean`または数値式です。  
  
 `expression2`  
 必須。 どの`Boolean`または数値式です。  
  
## <a name="remarks"></a>コメント  
 `Boolean`比較、`result`は`False`場合にのみ、両方`expression1`と`expression2`に評価される`False`です。 次に示す方法`result`決定されます。  
  
|場合`expression1`は|および`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  `Boolean` 、比較、`Or`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)実行*ショート サーキット*、つまりを`expression1`は`True`、し、`expression2`は評価されません。  
  
 ビットごとの演算、`Or`演算子が 2 つの数値式で同じ位置にビットのビットごとの比較を実行し、対応するにビットを設定`result`次の表のとおりです。  
  
|場合内のビット`expression1`は|でビット`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確に実行されるようにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`と 0 を`False`) し、ビットごとの演算を実行します。  
  
 `Boolean` 、比較結果のデータ型は`Boolean`します。 ビットごとの比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。  
  
## <a name="overloading"></a>オーバーロード  
 `Or`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Or`オペレーターが 2 つの式の包括的論理和を実行します。 結果は、`Boolean`を表す値が 2 つの式のいずれかのかどうか`True`です。  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 前の例の結果を生成する`True`、 `True`、および`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Or`オペレーターが 2 つの数値式のビットごとの包括的論理和を実行します。 結果のパターン内のビットは、オペランドの対応するビットのいずれか 1 に設定されている場合に設定されます。  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 前の例では、それぞれ 10、14、14 の結果を生成します。  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
