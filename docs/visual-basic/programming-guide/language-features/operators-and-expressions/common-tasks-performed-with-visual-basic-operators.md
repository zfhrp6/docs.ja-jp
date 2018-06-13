---
title: Visual Basic の演算子で実行される一般的なタスク
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], logical
- operators [Visual Basic], string concatenation
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- operators [Visual Basic], arithmetic
- operators [Visual Basic], string comparison
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- operators [Visual Basic], comparison
- operators [Visual Basic], short-circuiting logical
ms.assetid: d181afe5-fafa-460f-a13b-81203f6f4587
ms.openlocfilehash: ab0b7e7c35992908aeaac14053665ff84719f1fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654727"
---
# <a name="common-tasks-performed-with-visual-basic-operators"></a>Visual Basic の演算子で実行される一般的なタスク
演算子と呼ばれる 1 つまたは複数の式に関連する多くの一般的なタスクを実行する*オペランド*です。  
  
## <a name="arithmetic-and-bit-shift-tasks"></a>算術演算子とビット シフトのタスク  
 次の表は、使用可能な算術演算子とビット シフト操作をまとめたものです。  
  
|終了|解決方法については、|  
|---|---|  
|別の 1 つの数値を追加します。|[+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)|  
|別の 1 つの数値を減算します。|[-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|数値の符号を反転します。|[-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)|  
|別の 1 つの数値を乗算します。|[* 演算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)|  
|1 つの数値を別に分割します。|[/演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)|  
|1 (剰余) することがなくで除算して数値の商を見つける|[\ 演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)|  
|数値の値が除算 (商) することがなく 1 つの残りの部分を検索します。|[Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)|  
|別の電源を 1 つの数値を発生させる|[^ 演算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)|  
|数値の値のビット パターンを左にシフトします。|[<\< 演算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)|  
|数値の値のビット パターンを右にシフトします。|[>> 演算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)|  
  
## <a name="comparison-tasks"></a>比較演算子  
 次の表は、使用可能な比較操作をまとめたものです。  
  
|終了|解決方法については、|  
|---|---|  
|2 つの値が等しいかどうかの判断します。|`=` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|2 つの値が等しくないかどうかを決定します。|`<>` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|1 つの値が他よりも小さいかどうかを判断します。|`<` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|1 つの値が他よりも大きいかどうかを判断します。|`>` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|1 つの値が別に少ないかどうかを判断します。|`<=` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|1 つの値がより大きいかに等しいかどうかを判断します。|`>=` 演算子 ([Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md))|  
|2 つのオブジェクト変数が同じオブジェクト インスタンスを参照しているかどうかを決定します。|[Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)|  
|2 つのオブジェクト変数が別のオブジェクト インスタンスを参照しているかどうかを決定します。|[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)|  
|オブジェクトが特定の種類がかどうかを判断します。|[TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)|  
  
## <a name="concatenation-tasks"></a>連結演算子  
 次の表は、使用可能な連結演算をまとめたものです。  
  
|終了|解決方法については、|  
|---|---|  
|複数の文字列を 1 つの文字列に結合します。|`&` 演算子 ([Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md))|  
|数値の値を文字列値との結合します。|`+` 演算子 ([Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md))|  
  
## <a name="logical-and-bitwise-tasks"></a>論理/ビットごとのタスク  
 次の表は、使用可能な論理/ビット処理操作をまとめたものです。  
  
|終了|解決方法については、|  
|---|---|  
|ブール値で論理否定演算を実行します。|[Not 演算子](../../../../visual-basic/language-reference/operators/not-operator.md)|  
|2 つのブール値の論理積します。|[And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|2 つのブール値に対する包括的論理和を実行します。|[Or 演算子](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|2 つのブール値に対する排他的論理和演算を実行します。|[Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|2 つのブール値に対するショート サーキット論理積を実行します。|[AndAlso 演算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)|  
|2 つのブール値に対するショート サーキットの包括的論理和を実行します。|[OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)|  
|2 つの整数値のビットごとの論理積を実行します。|[And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)|  
|2 つの整数値のビットごとの包括的論理和を実行します。|[Or 演算子](../../../../visual-basic/language-reference/operators/or-operator.md)|  
|2 つの整数値のビットごとの排他的論理和演算を実行します。|[Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)|  
|整数値のビットごとの論理否定演算を実行します|[Not 演算子](../../../../visual-basic/language-reference/operators/not-operator.md)|  
  
## <a name="see-also"></a>関連項目  
 [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [機能別の演算子一覧](../../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
