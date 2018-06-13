---
title: AndAlso 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 549d14cc35d285ac2e4a02a37dd201cc669c5627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604082"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 演算子 (Visual Basic)
ショート サーキットの 2 つの式に対して論理積を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`result`|必須。 任意のブール型 (`Boolean`) の式を指定します。 結果は、`Boolean`の 2 つの式の比較の結果。|  
|`expression1`|必須。 任意のブール型 (`Boolean`) の式を指定します。|  
|`expression2`|必須。 任意のブール型 (`Boolean`) の式を指定します。|  
  
## <a name="remarks"></a>コメント  
 論理演算があると言われます*ショート サーキット*場合は、コンパイルされたコードが別の式の結果に応じて、1 つの式の評価をバイパスできます。 最初に評価される式の結果には、操作の最終的な結果が判断した場合必要はありませんを 2 番目の式を評価するため、最終的な結果を変更することはできません。 ショート サーキットによりでバイパスされる式が複雑な場合、またはプロシージャの呼び出しが含まれる場合、パフォーマンスが向上します。  
  
 場合に、両方の式が評価される`True`、`result`は`True`します。 次に示す方法`result`決定されます。  
  
|場合`expression1`は|および`expression2`は|値`result`は|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(評価されません)|`False`|  
  
## <a name="data-types"></a>データの種類  
 `AndAlso`に対してのみ演算子が定義されて、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)です。 各オペランドを必要に応じて変換`Boolean`での操作を実行して`Boolean`です。 数値型に結果を割り当てると、Visual Basic 変換から`Boolean`その型にします。 予期しない動作を引き起こすこれ可能性があります。 たとえば、`5 AndAlso 12`結果`–1`に変換される`Integer`です。  
  
## <a name="overloading"></a>オーバーロード  
 [And 演算子](../../../visual-basic/language-reference/operators/and-operator.md)と[IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドの型が含まれますクラスまたは構造体。 オーバー ロード、`And`と`IsFalse`演算子の動作に影響、`AndAlso`演算子。 コードで使用する場合`AndAlso`クラスまたはオーバー ロードする構造体で`And`と`IsFalse`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、 `AndAlso` 2 つの式に対して論理積を実行する演算子です。 結果は、`Boolean`全体結合された式かどうかを表す値は true です。 最初の式が場合`False`、2 つ目は評価されません。  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 前の例の結果を生成する`True`、 `False`、および`False`、それぞれします。 計算に`secondCheck`、1 つ目が既にあるために、2 番目の式は評価されません`False`です。 計算に 2 番目の式を評価するただし、`thirdCheck`です。  
  
## <a name="example"></a>例  
 次の例は、`Function`配列の要素間の特定の値を検索するプロシージャ。 配列が空の場合、または配列の長さを超えている場合、`While`ステートメントは、検索値に対して配列の要素をテストしません。  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [And 演算子](../../../visual-basic/language-reference/operators/and-operator.md)  
 [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
