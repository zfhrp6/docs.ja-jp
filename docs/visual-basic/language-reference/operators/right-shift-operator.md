---
title: '&gt;&gt; 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 9bb8e82b3f5451417fe1867d08b7601ee1acb036
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605408"
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt; 演算子 (Visual Basic)
ビット パターンに対して算術右シフトを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 整数値。 ビット パターンのシフトの結果。 データ型はのと同じ`pattern`です。  
  
 `pattern`  
 必須。 整数の数値式です。 シフトするビット パターンです。 データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 数値式です。 ビット パターンをシフトするビット数。 データ型にする必要があります`Integer`に拡大変換または`Integer`です。  
  
## <a name="remarks"></a>コメント  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。 算術右シフトの右端のビット位置を超えてシフトは破棄され、左端 (符号) のビットが左側にある空いたビット位置に反映されます。 つまり、`pattern`負の値を持つ、空いた位置は、いずれかに設定されます。 それ以外の場合 0 に設定されます。  
  
 なおデータ型`Byte`、 `UShort`、 `UInteger`、および`ULong`に反映されるまでの符号ビットがないように、符号がないです。 場合`pattern`の任意の符号なし型、空いた位置は常に 0 に設定します。  
  
 Visual Basic マスクの値を防ぐには、結果が保持できるよりも多くのビット シフト、`amount`のデータ型に対応するサイズ マスクを持つ`pattern`します。 これらの値のバイナリとシフト数が使用されます。 サイズのマスクは次のとおりです。  
  
|データ型 `pattern`|サイズのマスク (10 進数)|サイズのマスク (16 進数)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|(&AMP; A) H00000007|  
|`Short`, `UShort`|16|(&AMP; A) H0000000F|  
|`Integer`, `UInteger`|31|(&AMP; A) H0000001F|  
|`Long`, `ULong`|63|(&AMP; A) H0000003F|  
  
 場合`amount`の値は 0 が`result`の値と同一では、`pattern`です。 場合`amount`は負の値は符号なしの値として解釈され、適切なサイズ マスクとマスクします。  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
## <a name="overloading"></a>オーバーロード  
 `>>`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`>>`整数値に対して算術右シフトを実行する演算子です。 結果は、常に同じデータ移動されている式の型を持ちます。  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 前の例の結果は次のとおりです。  
  
-   `result1` 2560 (0000 1010 0000 0000)。  
  
-   `result2` 160 (0000 0000 1010 0000)。  
  
-   `result3` 2 (0000 0000 0000 0010) です。  
  
-   `result4` 640 (0000 0010 1000 0000)。  
  
-   `result5` 0 (シフト 15 桁) です。  
  
 Shift キーを押し、金額`result4`18 として計算されますが 2 と等しいと 15 です。  
  
 次の例では、負の値に算術シフトを示します。  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 前の例の結果は次のとおりです。  
  
-   `negresult1` -512 (1111 1110 0000 0000) は、します。  
  
-   `negresult2` -1 (符号ビットが反映されますです)。  
  
## <a name="see-also"></a>関連項目  
 [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>>= 演算子](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
