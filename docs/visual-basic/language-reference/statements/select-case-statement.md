---
title: Select...Case ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 9d24b455d92cbd00b268df26283aab082b7703a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case ステートメント (Visual Basic)
式の値に応じて、ステートメントのいくつかのグループのいずれかを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`testexpression`|必須。 式。 基本データ型のいずれかに評価される必要があります (`Boolean`、 `Byte`、 `Char`、 `Date`、 `Double`、 `Decimal`、 `Integer`、 `Long`、 `Object`、 `SByte`、 `Short`、`Single`、 `String`、 `UInteger`、 `ULong`、および`UShort`)。|  
|`expressionlist`|必要な`Case`ステートメントです。 一致した値を表す式の句の一覧`testexpression`です。 複数の式の句は、コンマで区切られます。 それぞれの句は、次の形式のいずれかを実行できます。<br /><br /> -   *expression1* `To` *expression2*<br />-[ `Is` ] *comparisonoperator* *式*<br />-   *式*<br /><br /> 使用して、`To`一致の範囲の境界を指定するキーワードの値を`testexpression`です。 値`expression1`の値以下である必要があります`expression2`です。<br /><br /> 使用して、`Is`比較演算子でキーワード (`=`、 `<>`、 `<`、 `<=`、 `>`、または`>=`)、一致した値に制限を指定する`testexpression`です。 場合、`Is`キーワードが指定されていないが自動的にする前に挿入*comparisonoperator*です。<br /><br /> のみを指定するフォーム`expression`の特殊なケースとして扱われる、 `Is` where を形成*comparisonoperator*等号 (=) は、(`=`)。 このフォームの評価は`testexpression`  = `expression`です。<br /><br /> 内の式`expressionlist`はの型に暗黙的に変換できる任意のデータ型を指定できます`testexpression`と適切な`comparisonoperator`に使用されている 2 つの型が有効です。|  
|`statements`|任意。 1 つまたは複数のステートメント次`Case`実行されている場合`testexpression`で任意の句に一致する`expressionlist`です。|  
|`elsestatements`|任意。 1 つまたは複数のステートメント次`Case Else`実行されている場合`testexpression`で句と一致しません、`expressionlist`のいずれかの`Case`ステートメントです。|  
|`End Select`|定義を終了、`Select`しています.`Case`構築します。|  
  
## <a name="remarks"></a>コメント  
 場合`testexpression`と一致する`Case``expressionlist`句、その次のステートメント`Case`ステートメントは、次実行`Case`、 `Case Else`、または`End Select`ステートメントです。 次のステートメントのパスを制御し、`End Select`です。 場合`testexpression`と一致する、`expressionlist`うち 1 つ以上の句`Case`句、最初の一致の次のステートメントのみを実行します。  
  
 `Case Else`ステートメントを使用して導入、`elsestatements`間で一致するものが見つからない場合に実行する、`testexpression`と`expressionlist`の他の句`Case`ステートメントです。 必須ではありませんが、これをお勧めして、`Case Else`内のステートメント、`Select Case`構築処理に予期しない`testexpression`値。 ない場合は`Case``expressionlist`句に一致する`testexpression`がありません`Case Else`ステートメントでは、次のステートメントのコントロール パス`End Select`です。  
  
 複数の式または範囲を使用するには各`Case`句。 たとえば、次の行は有効です。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is`で使用されるキーワード、`Case`と`Case Else`ステートメントが同じではありません、 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)、オブジェクト参照の比較に使用されます。  
  
 範囲や文字の文字列の複数の式を指定することができます。 次の例では、 `Case` 「リンゴ」に等しい、アルファベット順に「ナット」と「スープ」の値であるかの現在の値とまったく同じ値を含む任意の文字列と一致する`testItem`です。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 設定は、`Option Compare`文字列比較に影響を与えることができます。 `Option Compare Text`、文字列「リンゴ」と「リンゴ」比較結果が等しいかどうかが`Option Compare Binary`、そうでないです。  
  
> [!NOTE]
>  A`Case`句を指定して複数のステートメントが動作と呼ばれる*ショート サーキット*です。 Visual Basic は左から右への句を評価し、1 つの場合との一致を生成します。 `testexpression`、残りの句は評価されません。 ショート サーキットのパフォーマンスが向上する、すべての式で必要とする場合、予期しない結果を生成できる`expressionlist`に評価されます。 ショート サーキットの詳細については、次を参照してください。[ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)です。  
  
 場合、コード内で、`Case`または`Case Else`ステートメント ブロックがブロック内のステートメントでそれ以上実行する必要はありませんを使用して、ブロックを終了できますが、`Exit Select`ステートメントです。 ステートメントに制御を直ちに移しますこの`End Select`です。  
  
 `Select Case` 構造を入れ子にすることができます。 入れ子になった`Select Case`構築の対応する必要がありますが`End Select`ステートメント内の 1 つに完全に含まする必要がありますと`Case`または`Case Else`、外側のステートメント ブロック`Select Case`構築の内部で入れ子にされています。  
  
## <a name="example"></a>例  
 次の例では、`Select Case`構造を使用して、変数の値に対応する行を書き込みます。`number`です。 2 番目`Case`ステートメントには、現在の値に一致する値が含まれています。 `number`"6、8、包括的"の間、ステートメントを書き込むため、実行します。  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
