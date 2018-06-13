---
title: And 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: e14dfd8ba200598084cad04d1faa05f3561f8dab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604643"
---
# <a name="and-operator-visual-basic"></a>And 演算子 (Visual Basic)
2 つの論理積`Boolean`式、または 2 つの数値式に対してビットごとの積。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`または数値式です。 ブール値の比較の`result`は 2 つの論理積`Boolean`値。 ビットごとの演算`result`は、次の 2 つの数値のビット パターンのビットごとの積を表す数値を指定します。  
  
 `expression1`  
 必須。 どの`Boolean`または数値式です。  
  
 `expression2`  
 必須。 どの`Boolean`または数値式です。  
  
## <a name="remarks"></a>コメント  
 ブール値の比較の`result`は`True`場合にのみ、両方`expression1`と`expression2`に評価される`True`です。 次に示す方法`result`決定されます。  
  
|場合`expression1`は|および`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール値の比較で、`And`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)実行*ショート サーキット*、つまりを`expression1`は`False`、し、`expression2`は評価されません。  
  
 数値の値に適用されるときに、`And`演算子が 2 つの数値式で同じ位置にビットのビットごとの比較を実行し、対応するにビットを設定`result`次の表のとおりです。  
  
|場合内のビット`expression1`は|でビット`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  論理演算子およびビット演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確な結果のようにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`と 0 を`False`) し、ビットごとの演算を実行します。  
  
 ブール値の比較結果のデータ型は`Boolean`します。 ビットごとの比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。  
  
> [!NOTE]
>  `And`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、 `And` 2 つの式に対して論理積を実行する演算子です。 結果は、`Boolean`が両方の式かどうかを表す値`True`です。  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 前の例の結果を生成する`True`と`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`And`オペレーターが 2 つの数値式のビットごとの論理積を実行します。 結果のパターン内のビットは、オペランドの対応するビットは次の両方 1 に設定する場合に設定されます。  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 前の例では、それぞれ 8、2、および 0 の場合の結果を生成します。  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
