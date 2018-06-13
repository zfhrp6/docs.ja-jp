---
title: Xor 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 34d317da5d85127e371c2df7229e0f0873972f50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604797"
---
# <a name="xor-operator-visual-basic"></a>Xor 演算子 (Visual Basic)
2 つの論理和を求めます`Boolean`式、または 2 つの数値式の和を求めます。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`または数値型の変数です。 ブール値の比較の`result`は 2 つの論理和 (排他的論理和)`Boolean`値。 ビットごとの演算`result`は、ビット処理排他的論理和) 2 つの数値のビット パターンを表す数値。  
  
 `expression1`  
 必須。 どの`Boolean`または数値式です。  
  
 `expression2`  
 必須。 どの`Boolean`または数値式です。  
  
## <a name="remarks"></a>コメント  
 ブール値の比較の`result`は`True`場合にだけ、ただ 1 つの`expression1`と`expression2`に評価される`True`です。 つまり、場合にのみ`expression1`と`expression2`評価に反対`Boolean`値。 次に示す方法`result`決定されます。  
  
|場合`expression1`は|および`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール値の比較で、`Xor`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 相当するショート サーキットはありません`Xor`結果は常に両方のオペランドに依存するため、します。 *ショート サーキット*論理演算子を参照してください[AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)と[OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)です。  
  
 ビットごとの演算、`Xor`演算子が 2 つの数値式で同じ位置にビットのビットごとの比較を実行し、対応するにビットを設定`result`次の表のとおりです。  
  
|場合内のビット`expression1`は|でビット`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位が低いため、ビットごとの演算が正確に実行されるようにかっこで囲む必要があります。  
  
 たとえば、5 `Xor` 3 は 6 です。 これが理由を確認するため、101 と 011 のバイナリ表現に 5 と 3 に変換します。 101 Xor 011 があること、110 6 の 10 進数のバイナリ表現を決定するのに、前の表を使用しています。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`数値を指定する式 (– 1`True`と 0 を`False`) し、ビットごとの演算を実行します。  
  
 `Boolean` 、比較結果のデータ型は`Boolean`します。 ビットごとの比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「リレーショナルとビットごとの比較」表を参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。  
  
## <a name="overloading"></a>オーバーロード  
 `Xor`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、 `Xor` 2 つの式に対して論理和 (排他的論理和) を実行する演算子です。 結果は、`Boolean`が式の 1 つだけかどうかを表す値`True`です。  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 前の例の結果を生成する`False`、 `True`、および`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Xor`オペレーターが 2 つの数値式のビットごとの排他的論理和 (排他的論理和) を実行します。 結果のパターン内のビットはただ 1 つのオペランドの対応するビットを 1 に設定されている場合に設定されます。  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 前の例では、2、12、および 14 の結果をそれぞれ生成されます。  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
