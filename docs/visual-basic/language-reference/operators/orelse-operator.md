---
title: OrElse 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 1ee3c1a5b6089f44742281eb40e2a7e9cb3e2812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604823"
---
# <a name="orelse-operator-visual-basic"></a>OrElse 演算子 (Visual Basic)
ショート サーキットの 2 つの式の包括的論理和を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 任意のブール型 (`Boolean`) の式を指定します。  
  
 `expression1`  
 必須。 任意のブール型 (`Boolean`) の式を指定します。  
  
 `expression2`  
 必須。 任意のブール型 (`Boolean`) の式を指定します。  
  
## <a name="remarks"></a>コメント  
 論理演算があると言われます*ショート サーキット*場合は、コンパイルされたコードが別の式の結果に応じて、1 つの式の評価をバイパスできます。 最初に評価される式の結果には、操作の最終的な結果が判断した場合必要はありませんを 2 番目の式を評価するため、最終的な結果を変更することはできません。 ショート サーキットによりでバイパスされる式が複雑な場合、またはプロシージャの呼び出しが含まれる場合、パフォーマンスが向上します。  
  
 いずれかまたは両方の式に評価される場合`True`、`result`は`True`します。 次に示す方法`result`決定されます。  
  
|場合`expression1`は|および`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(評価されません)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>データの種類  
 `OrElse`に対してのみ演算子が定義されて、[ブールのデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)です。 各オペランドを必要に応じて変換`Boolean`での操作を実行して`Boolean`です。 数値型に結果を割り当てると、Visual Basic 変換から`Boolean`その型にします。 予期しない動作を引き起こすこれ可能性があります。 たとえば、`5 OrElse 12`結果`–1`に変換される`Integer`です。  
  
## <a name="overloading"></a>オーバーロード  
 [または演算子](../../../visual-basic/language-reference/operators/or-operator.md)と[IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドは、そのクラスの型を持つまたは構造体。 オーバー ロード、`Or`と`IsTrue`演算子の動作に影響、`OrElse`演算子。 コードで使用する場合`OrElse`クラスまたはオーバー ロードする構造体で`Or`と`IsTrue`、再定義された動作を確認してください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、 `OrElse` 2 つの式に対して論理和演算を実行する演算子です。 結果は、`Boolean`値を表す 2 つの式のいずれかが true であるかどうか。 最初の式が場合`True`、2 つ目は評価されません。  
  
 [!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]  
  
 前の例の結果を生成する`True`、 `True`、および`False`それぞれします。 計算に`firstCheck`、1 つ目が既にあるために、2 番目の式は評価されません`True`です。 計算に 2 番目の式を評価するただし、`secondCheck`です。  
  
## <a name="example"></a>例  
 次の例は、`If`しています.`Then` 2 つのプロシージャ呼び出しを含むステートメント。 最初の呼び出しが返された場合`True`、2 番目の手順は呼び出されません。 これは、ことが予期しない結果に 2 番目の手順は、コードのこのセクションの実行時に常に実行する重要なタスクを実行する場合。  
  
 [!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Or 演算子](../../../visual-basic/language-reference/operators/or-operator.md)  
 [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Visual Basic における論理/ビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
