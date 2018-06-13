---
title: '- 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604316"
---
# <a name="--operator-visual-basic"></a>- 演算子 (Visual Basic)
2 つの数値式または数値式の負の値の差を返します。  
  
## <a name="syntax"></a>構文  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須。 任意の数式。  
  
 `expression2`  
 いない限り、必須、`–`演算子が負の値を計算します。 任意の数式。  
  
## <a name="result"></a>結果  
 結果の違いは、`expression1`と`expression2`、またはの負数化された値`expression1`です。  
  
 結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。 これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。  
  
## <a name="remarks"></a>コメント  
 最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*2 つの数値式の違いを減算演算子。  
  
 2 番目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値の否定演算子。 符号を反転することの否定は、この意味で`expression1`結果が正の値になるよう場合`expression1`が負の値。  
  
 いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は 0 として処理します。  
  
> [!NOTE]
>  `–`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、その再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`–`演算子を計算し、2 つの数値の差を返すし、数値を否定します。  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 次のこれらのステートメントの実行`binaryResult`124.45 が含まれていますと`unaryResult`–334.90 が含まれています。  
  
## <a name="see-also"></a>関連項目  
 [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
