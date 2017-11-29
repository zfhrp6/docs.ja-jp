---
title: "Mod 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5464b57c993e5703c09529b527a7bc714e045870
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mod-operator-visual-basic"></a>Mod 演算子 (Visual Basic)
2 つの数値を除算し、残りの部分のみを返します。  
  
## <a name="syntax"></a>構文  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>指定項目  
 `number1`  
 必須です。 任意の数式。  
  
 `number2`  
 必須です。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。 これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。  
  
## <a name="result"></a>結果  
 結果の後に残りの部分は、`number1`で割った値`number2`です。 たとえば、式`14 Mod 4`2 に評価します。  
  
## <a name="remarks"></a>コメント  
 いずれか`number1`または`number2`浮動小数点値は、浮動小数点除算の剰余が返されます。 結果のデータ型のデータ型で除算に起因するすべての値を保持できる最小のデータ型は、`number1`と`number2`です。  
  
 場合`number1`または`number2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
 関連する演算子を以下に示します。  
  
-   [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)除算の商の整数を返します。 たとえば、式`14 \ 4`3 に評価します。  
  
-   [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)浮動小数点数として、残りの部分を含む、完全商を返します。 たとえば、式`14 / 4`3.5 に評価します。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`number2`の動作は 0 に評価される、`Mod`演算子はオペランドのデータ型によって異なります。 整数の除算をスロー、<xref:System.DivideByZeroException>例外。 浮動小数点除算返します<xref:System.Double.NaN>です。  
  
## <a name="equivalent-formula"></a>同等の数式  
 式`a Mod b`は次の式のいずれかに相当します。  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>浮動小数点は誤差  
 浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに注意してください。 これにより予期しない結果を比較値などの特定の操作から、`Mod`演算子。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。  
  
## <a name="overloading"></a>オーバーロード  
 `Mod`演算子*オーバー ロードされた*、つまり、クラスまたは構造体が、動作を再定義できます。 コードが適用される場合`Mod`クラスまたはそのようなオーバー ロードを含む構造体のインスタンスをする、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Mod`操作を 2 つの数値を除算し、残りの部分のみを返します。 どちらかの数値が浮動小数点数の場合は、結果は、残りの部分を表す浮動小数点数です。  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、浮動小数点のオペランドの不正確さの可能性を示します。 オペランドは、最初のステートメントで`Double`0.2、無限に繰り返されるバイナリ分数 0.20000000000000001 として格納されている値とします。 2 番目のステートメントでは、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`は正確に表現します。  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
