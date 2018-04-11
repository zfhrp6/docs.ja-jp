---
title: + 演算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>+ 演算子 (Visual Basic)
2 つの数値を加算または数値式の正の値を取得します。 2 つの文字列式を連結するも使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression1`|必須です。 任意の数値または文字列式です。|  
|`expression2`|いない限り、必須、`+`演算子が負の値を計算します。 任意の数値または文字列式です。|  
  
## <a name="result"></a>結果  
 場合`expression1`と`expression2`が両方とも数値、算術、合計になります。  
  
 場合`expression2`失われている、`+`演算子は、*単項*恒等演算子式の値は変わりません。 この意味で、操作ではのサインインを維持した`expression1`ので、結果は負の値が、場合`expression1`が負の値。  
  
 場合`expression1`と`expression2`、両方の文字列は、結果は、それらの値を連結します。  
  
 場合`expression1`と`expression2`が実行されるアクションが、型、内容、およびの設定に依存、混合型の[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。 詳細については、「解説」表を参照してください。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含むすべての数値型と`Decimal`、および`String`です。  
  
## <a name="remarks"></a>コメント  
 一般に、`+`可能であれば、算術加算を実行し、両方の式が文字列が場合にのみを連結します。  
  
 どちらの式の場合、 `Object`、Visual Basic は、次の操作を実行します。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|両方の式が数値データ型 (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`)|追加します。 結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。 「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。|  
|型の両方の式は、します。`String`|連結します。|  
|1 つの式は数値データ型で、もう一方の文字列|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。<br /><br /> 場合、`String`に変換できない`Double`、スロー、<xref:System.InvalidCastException>例外。|  
|1 つの式が数値データ型では、もう一方は[何も行われません](../../../visual-basic/language-reference/nothing.md)|追加すると`Nothing`値 0 にします。|  
|1 つの式は、文字列であり、もう一方は`Nothing`|連結`Nothing`として値を持つ""です。|  
  
 1 つの式がある場合、`Object`式では、Visual Basic は次の操作を実行します。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|`Object`式は数値の値を保持し、もう一方の数値データ型|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、しを追加します。|  
|`Object`式は数値の値を保持し、もう一方の型の`String`|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換、`String`に`Double`を追加します。<br /><br /> 場合、`String`に変換できない`Double`、スロー、<xref:System.InvalidCastException>例外。|  
|`Object`式が文字列を保持し、もう一方の数値データ型|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、文字列を暗黙的に変換`Object`に`Double`を追加します。<br /><br /> 場合、文字列`Object`に変換できません`Double`、スロー、<xref:System.InvalidCastException>例外。|  
|`Object`式が文字列を保持し、もう一方の型の`String`|場合`Option Strict`は`On`、コンパイラ エラーを生成します。<br /><br /> 場合`Option Strict`は`Off`、暗黙的に変換`Object`に`String`連結します。|  
  
 両方の式が場合`Object`式、Visual Basic は、次のアクション (`Option Strict Off`のみ)。  
  
|式のデータ型|コンパイラによる処理|  
|---|---|  
|両方`Object`式は数値を保持|追加します。|  
|両方`Object`型の式は、`String`|連結します。|  
|1 つ`Object`式は数値の値を保持し、文字列を保持して、他の|文字列に暗黙的に変換`Object`に`Double`を追加します。<br /><br /> 場合、文字列`Object`値を数値に変換することはできませんし、スロー、<xref:System.InvalidCastException>例外。|  
  
 いずれか`Object`式に評価される[何も](../../../visual-basic/language-reference/nothing.md)または<xref:System.DBNull>、`+`演算子として扱われます、`String`値は""です。  
  
> [!NOTE]
>  使用すると、`+`演算子ができないことがありますを追加または文字列の連結が発生するかどうかを判断します。 使用して、`&`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。  
  
## <a name="overloading"></a>オーバーロード  
 `+`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 次の例では、`+`番号を追加する演算子です。 オペランドが両方の数値の場合は、Visual Basic は、算術演算の結果を計算します。 算術演算の結果では、2 つのオペランドの合計を表します。  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 使用することも、`+`文字列を連結する演算子です。 オペランドが両方とも文字列である場合は、Visual Basic では、それらを連結します。 文字列連結の結果では、他の後に、2 つのオペランドの内容から成る 1 つの文字列を表します。  
  
 混合型のオペランドがある場合、結果の設定によって異なります、 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。 次の例は、結果を示しています。 ときに`Option Strict`は`On`します。  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 次の例は、結果を示しています。 ときに`Option Strict`は`Off`します。  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 あいまいさをなくすため、使用する必要があります、`&`演算子の代わりに`+`連結します。  
  
## <a name="see-also"></a>関連項目  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [連結演算子](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
