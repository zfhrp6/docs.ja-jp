---
title: "Select...Case Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Select"
  - "vb.Case"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Case statement"
  - "Select...Case statements"
  - "conditional statements, Select Case"
  - "control flow, branching"
  - "Else keyword [Visual Basic], in Select...Case statements"
  - "execution, conditional"
  - "To keyword, in Select...Case statements"
  - "Select Case statement, Select...Case"
  - "Select statement, Select...Case"
  - "Is operator [Visual Basic], in Select...Case statements"
  - "branching, conditional"
  - "Case Else statement, Select...Case"
  - "End keyword, Select Case statements"
  - "Case statement, Select...Case"
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Select...Case Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

条件式の値に従って、複数のステートメント ブロックのいずれかを実行させるフロー制御ステートメントです。  
  
## 構文  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`testexpression`|必ず指定します。  式を指定します。  式の結果は、`Boolean`、`Byte`、`Char`、`Date`、`Double`、`Decimal`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、`UShort` など、基本データ型のいずれかである必要があります。|  
|`expressionlist`|`Case` ステートメント内に必ず指定します。  `testexpression` と照合する値を表す式の句のリストを指定します。  複数の式の句を指定する場合は、コンマ \(,\) で区切ります。  それぞれの句は、次のいずれかの形式をとることができます。<br /><br /> -   *expression1* `To` *expression2*<br />-   \[ `Is` \] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> `testexpression` に一致する値の範囲の境界を指定するには、`To` キーワードを使用します。  `expression1` の値は、`expression2` の値以下である必要があります。<br /><br /> `Is` キーワードを比較演算子 \(`=`、`<>`、`<`、`<=`、`>`、`>=`\) と一緒に使用すると、`testexpression` と照合する値に制限を指定できます。  キーワード `Is` は、指定しなくても *comparisonoperator* の前に自動的に挿入されます。<br /><br /> `expression` だけを指定する形式は、*comparisonoperator* を等号 \(`=`\) とする、特殊な `Is` 形式として処理されます。  この形式は `testexpression` \= `expression` として評価されます。<br /><br /> `expressionlist` 内の式は任意のデータ型をとることができます。ただし、そのデータ型は、引数 `testexpression` のデータ型に暗黙的に変換可能であり、適用される `comparisonoperator` がその 2 つの型で有効である必要があります。|  
|`statements`|省略可能です。  `testexpression` が `expressionlist` 内のいずれかの句に一致する場合に実行される 1 つ以上のステートメントを `Case` の後に指定します。|  
|`elsestatements`|省略可能です。  `testexpression` がどの `Case` ステートメントの `expressionlist` 内にある、どの句とも一致しない場合に実行される 1 つ以上のステートメントを `Case Else` の後に指定します。|  
|`End Select`|`Select`...`Case` 構造の定義を終了します。|  
  
## 解説  
 `testexpression` がいずれかの `Case` `expressionlist` 句と一致する場合は、その `Case` ステートメントの後から、次の `Case`、`Case Else`、または `End Select` ステートメントまでのステートメントが実行されます。  ブロックの実行が終わると、制御は `End Select` ステートメントの次のステートメントに移ります。  `testexpression` が 2 つ以上の `Case` 句の `expressionlist` 句に一致する場合は、最初に一致した句の後のステートメントだけが実行されます。  
  
 `Case Else` は、他のどの `Case` ステートメントの `testexpression` 句と `expressionlist` 句の間にも、一致する句が見つからない場合に実行する `elsestatements` を定義する際に使用します。  必須ではありませんが、予測できない `testexpression` 値を処理するために、`Select Case` 構造に `Case Else` ステートメントを記述することをお勧めします。  `testexpression` に一致する `Case` `expressionlist` 句が 1 つもなく、`Case Else` ステートメントもない場合、制御は `End Select` の次のステートメントに渡されます。  
  
 `Case` 句には複数の式や範囲を指定できます。  たとえば、次の行は有効なステートメントです。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Case` ステートメントと `Case Else` ステートメントに使用する `Is` キーワードは、オブジェクト参照を比較するために使う [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md) と同じではありません。  
  
 文字列の範囲や複数の文字列式を指定することもできます。  次の例では、`Case` は "apples" とまったく等しい文字列、アルファベット順で "nuts" と "soup" の間の値を持つ文字列、または現在の `testItem` の値とまったく同じ値を格納する文字列と一致します。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 文字列の比較は、`Option Compare` の設定の影響を受けることがあります。  `Option Compare Text` が設定されている場合は、"Apples" と "apples" の比較は等しくなりますが、`Option Compare Binary` が設定されている場合は等しくなりません。  
  
> [!NOTE]
>  複数の句が定義された `Case` ステートメントは、*ショートサーキット* と呼ばれる動作を起こすことがあります。  Visual Basic は句を左から右の順に評価し、いずれか 1 つが `testexpression` と一致した場合、残りの句は評価されません。  ショートサーキットはパフォーマンスを向上させますが、`expressionlist` 内のすべての式が評価されるという前提で定義すると、予期しない結果になる可能性があります。  ショートサーキットの詳細については、「[Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)」を参照してください。  
  
 `Case` または `Case Else` のステートメント ブロック内のコードが、そのブロック内のステートメントを実行する必要がなくなった場合は、`Exit Select` ステートメントを使用してブロックを終了できます。  制御は、直ちに `End Select` の次のステートメントに移ります。  
  
 `Select Case` は入れ子構造にできます。  入れ子にされた各 `Select Case` には、対応する `End Select` ステートメントが必要です。また、外側の `Select Case` の単一の `Case` または `Case Else` のステートメント ブロックの内側に、完全に含まれている必要があります。  
  
## 使用例  
 `Select Case` 構造を使用して、変数 `number` の値に対応する行を書き込む例を次に示します。  2 番目の `Case` ステートメントに `number` の現在の値に一致する値が含まれるため、"Between 6 and 8, inclusive" を書き込むステートメントが実行されます。  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)