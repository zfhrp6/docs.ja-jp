---
title: '&lt;&lt; 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: bdec015309526aeac2499bc7b459b6ccab6f1e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604459"
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt; 演算子 (Visual Basic)
ビット パターンに対して算術左シフトを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 整数値。 ビット パターンのシフトの結果。 データ型はのと同じ`pattern`です。  
  
 `pattern`  
 必須。 整数の数値式です。 シフトするビット パターンです。 データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 数値式です。 ビット パターンをシフトするビット数。 データ型にする必要があります`Integer`に拡大変換または`Integer`です。  
  
## <a name="remarks"></a>コメント  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。 算術左シフト、結果のデータ型の範囲を超えてシフトは破棄され、右側の空いたビット位置は 0 に設定されます。  
  
 Visual Basic は、シフトの結果を保持できる以上のビット数を防ぐためには、値をマスク`amount`のデータ型に対応するサイズ マスクを持つ`pattern`します。 これらの値のバイナリとシフト数が使用されます。 サイズのマスクは次のとおりです。  
  
|データ型 `pattern`|サイズのマスク (10 進数)|サイズのマスク (16 進数)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|(&AMP; A) H00000007|  
|`Short`, `UShort`|16|(&AMP; A) H0000000F|  
|`Integer`, `UInteger`|31|(&AMP; A) H0000001F|  
|`Long`, `ULong`|63|(&AMP; A) H0000003F|  
  
 場合`amount`の値は 0 が`result`の値と同一では、`pattern`です。 場合`amount`は負の値は符号なしの値として解釈され、適切なサイズ マスクとマスクします。  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
> [!NOTE]
>  `<<`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合、再定義された動作を理解していることを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`<<`整数値の算術左シフトを実行する演算子です。 結果は、常に同じデータ移動されている式の型を持ちます。  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 前の例の結果は次のとおりです。  
  
-   `result1` 192 (0000 0000 1100 0000)。  
  
-   `result2` 3072 (0000 1100 0000 0000)。  
  
-   `result3` -32768 (1000 0000 0000 0000)。  
  
-   `result4` 384 (0000 0001 1000 0000) は、します。  
  
-   `result5` 0 (シフト 15 桁) です。  
  
 Shift キーを押し、金額`result4`17 として計算されますが 1 に等しいと 15 です。  
  
## <a name="see-also"></a>関連項目  
 [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<<= 演算子](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
