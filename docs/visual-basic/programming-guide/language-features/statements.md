---
title: "Statements in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], declaring"
  - "colons (:)"
  - "constants, defining"
  - "underlines"
  - "constants, statements"
  - "blue underline"
  - "procedures, statements"
  - "variables [Visual Basic], assigning"
  - "line breaks, in code"
  - "executable statements"
  - "variables [Visual Basic], defining"
  - "statements [Visual Basic], about statements"
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Statements in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のステートメントは、完結した命令です。  ステートメントには、キーワード、演算子、変数、定数、および式を含めることができます。  各ステートメントは、次のカテゴリのいずれかに属します。  
  
-   **宣言ステートメント**。宣言ステートメントは、変数、定数、またはプロシージャの名前を指定します。一緒にデータ型を指定することもできます。  
  
-   **実行可能なステートメント**。実行可能なステートメントは、アクションを実行します。  メソッドまたは関数の呼び出しや、コード ブロックのループや分岐を行うことができます。  値や式を変数や定数に代入する**代入ステートメント**も実行可能なステートメントに含まれます。  
  
 このトピックでは、各カテゴリについて説明します。  また、複数のステートメントを 1 行に結合する方法、1 つのステートメントを複数行にわたって継続する方法について説明します。  
  
## 宣言ステートメント  
 プロシージャ、変数、プロパティ、配列、および定数に名前を付けて定義するには、宣言ステートメントを使います。  プログラミング要素を宣言するときには、データ型、アクセス レベル、スコープも宣言します。  詳細については、「[Declared Element Characteristics](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)」を参照してください。  
  
 次の例には、3 つの宣言が含まれています。  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_1.vb)]  
  
 最初の宣言は `Sub` ステートメントです。  `applyFormat` という名前のプロシージャが、対応する `End Sub` ステートメントと一緒に宣言されています。  また、`applyFormat` に `Public` が指定されています。これは、参照可能なすべてのコードに呼び出しが許可されることを意味します。  
  
 次に、`Const` ステートメントによって、定数 `limit` が宣言されています。この宣言では、データ型として整数 \(`Integer`\) が指定され、値として 33 が指定されています。  
  
 3 つ目の宣言である `Dim` ステートメントは、変数 `thisWidget` を宣言しています。  データ型にはオブジェクト \(具体的には `Widget` クラスから作成されるオブジェクト\) が指定されています。  変数はすべての基本データ型、または使用するアプリケーションに公開されているどのオブジェクト型でも宣言できます。  
  
### 初期値  
 宣言ステートメントを含むコードが実行されると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は宣言された要素に必要なメモリを確保します。  宣言された要素が値を保持する場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はそのデータ型の既定値で要素を初期化します。  詳細については、「[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)」の「動作」を参照してください。  
  
 宣言時に変数に初期値を代入することもできます。次に例を示します。  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_2.vb)]  
  
 オブジェクト変数の場合は、次のように [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) キーワードを使うと、変数を宣言するときにそのクラスのインスタンスを明示的に作成できます。  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_3.vb)]  
  
 宣言ステートメントに指定した初期値は、実行がその宣言ステートメントに到達するまで変数に代入されません。  それまでは、変数にそのデータ型の既定値が格納されます。  
  
## 実行可能なステートメント  
 実行可能なステートメントは、処理を実行します。  プロシージャを呼び出したり、コード内の別の場所に分岐したり、いくつかのステートメントをループ実行したり、式を評価したりします。  代入ステートメントは特殊な形の実行可能ステートメントです。  
  
 次の例では、`If...Then...Else` 制御構造を使用して、変数の値に基づいて異なるコード ブロックを実行します。  各コード ブロックの中では、`For...Next` ループを指定の回数だけ実行します。  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_4.vb)]  
  
 この例の `If` ステートメントは、`clockwise` パラメーターの値をチェックします。  値が `True` の場合は、`aWidget` の `spinClockwise` メソッドを呼び出します。  値が `False` の場合は、`aWidget` の `spinCounterClockwise` メソッドを呼び出します。  `If...Then...Else` 制御構造は `End If` で終わります。  
  
 各ブロック内の `For...Next` ループは、適切なメソッドを `revolutions` パラメーターの値の回数だけ呼び出します。  
  
## 代入ステートメント  
 代入ステートメントは代入演算を行います。つまり、次の例のように、代入演算子 \(`=`\) の右側の値を左側の要素に格納します。  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_5.vb)]  
  
 この例の代入ステートメントでは、42 というリテラル値を `v` 変数に格納しています。  
  
### 使用できるプログラミング要素  
 代入演算子の左側に指定するプログラミング要素は、値を受け取って格納できるものにする必要があります。  したがって、[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) ではない変数またはプロパティを指定するか、配列要素を指定します。  代入ステートメントのコンテキストでは、このような要素を*左辺値*、つまり "左側の値" と呼ぶことがあります。  
  
 代入演算子の右側の値は、式によって生成されます。この式は、リテラル、定数、変数、プロパティ、配列要素、他の式、関数呼び出しの任意の組み合わせによって構成されます。  次に例を示します。  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_6.vb)]  
  
 この例では、`y` 変数の値を `z` 変数の値に加算し、さらに `findResult` 関数の戻り値を加算しています。  その後、この式の合計値を `x` 変数に格納しています。  
  
### 代入ステートメントのデータ型  
 次の例に示すように、代入演算子では、数値だけでなく `String` 値も代入できます。  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_7.vb)]  
  
 また、次の例のように `Boolean` リテラルまたは `Boolean` 式を使用して、`Boolean` 値を代入することもできます。  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_8.vb)]  
  
 同様に、`Char`、`Date`、または `Object` データ型のプログラミング要素に適切な値を代入することができます。  また、オブジェクト インスタンスを、そのインスタンスの作成元になったクラスとして宣言された要素に代入することもできます。  
  
### 複合代入ステートメント  
 *複合代入ステートメント*は、まず式の演算を実行してから、その結果をプログラミング要素に代入します。  次の例では、このような演算子の 1 つである `+=` を使用しています。この演算子は、左側の変数の値に右側の式の値を加算します。  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_9.vb)]  
  
 この例では、`n` 変数の値に 1 を加算し、その新しい値を `n` 変数に格納します。  これは、次のステートメントを短縮したものと考えることができます。  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_10.vb)]  
  
 この種類の演算子を使うと、さまざまな複合代入演算を行うことができます。  このような演算子の一覧と、それぞれの詳細については、「[Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)」を参照してください。  
  
 既存の文字列の末尾に文字列を追加するには、次の例のように連結代入演算子 \(`&=`\) を使うと便利です。  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_11.vb)]  
  
### 代入ステートメントでの型変換  
 変数、プロパティ、または配列要素に代入する値は、代入先の要素に適したデータ型にする必要があります。  一般的には、代入先の要素と同じデータ型の値を生成するよう努力します。  しかし、型によっては代入時に別の型に変換できるものもあります。  
  
 データ型の変換の詳細については、「[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)」を参照してください。  簡単に説明すると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は特定の型の値を、拡大変換した他の任意の型へと自動的に変換します。  *拡大変換*は実行時に必ず成功する変換であり、データを一切失いません。  たとえば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は必要に応じて `Integer` 値を `Double` に変換します。`Integer` は `Double` へと拡大変換されるためです。  詳細については、「[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 *縮小変換* \(拡大変換を行わない変換\) は、実行時に失敗したりデータを失ったりする可能性があります。  縮小変換は型変換関数を使用して明示的に実行できます。また、`Option Strict Off` を設定するとすべての変換をコンパイラに暗黙的に実行させることができます。  詳細については、「[Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」を参照してください。  
  
## 複数のステートメントを 1 行に記述する方法  
 各ステートメントをコロン \(`:`\) で区切ると、1 行に複数のステートメントを記述できます。  次に例を示します。  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_12.vb)]  
  
 複数のステートメントを 1 行に記述すると便利な場合もありますが、コードが読みにくくなって管理がたいへんになります。  1 行に記述するステートメントは 1 つにすることをお勧めします。  
  
## 複数行にまたがるステートメント  
 ステートメントは、1 行に収まるのが普通ですが、長すぎて収まらない場合には、行連結シーケンスを使って次の行に続けることができます。行連結シーケンスは、空白とそれに続くアンダースコア \(`_`\)、さらにそれに続く復帰で構成されています。  次の例では、実行可能なステートメント `MsgBox` を 2 行にまたがって記述しています。  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_13.vb)]  
  
### 暗黙の行連結  
 多くの場合、アンダースコア \(\_\) 文字を使用しなくても、次の連続する行のステートメントを継続できます。  次のコード行のステートメントが暗黙的に継続される構文要素を次の表に示します。  
  
|||  
|-|-|  
|構文要素|例|  
|コンマ \(`,`\) の後。|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_14.vb)]|  
|左かっこ \(`(`\) の後、または右かっこ \(`)`\) の前。|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_15.vb)]|  
|左中かっこ \(`{`\) の後、または右中かっこ \(`}`\) の前。|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_16.vb)]<br /><br /> 詳細については、「[Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」または「[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。|  
|XML リテラル内の埋め込み式の開始記号 \(`<%=`\) の後、または埋め込み式の終了記号 \(`%>`\) の前。|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_17.vb)]<br /><br /> 詳細については、「[Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)」を参照してください。|  
|連結演算子 \(`&`\) の後。|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_18.vb)]<br /><br /> 詳細については、「[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。|  
|代入演算子 \(`=`、`&=`、`:=`、`+=`、`-=`、`*=`、`/=`、`\=`、`^=`、`<<=`、`>>=`\) の後。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_19.vb)]<br /><br /> 詳細については、「[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。|  
|式内の二項演算子 \(`+`、`-`、`/`、`*`、`Mod`、`<>`、`<`、`>`、`<=`、`>=`、`^`、`>>`、`<<`、`And`、`AndAlso`、`Or`、`OrElse`、`Like`、`Xor`\) の後。|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_20.vb)]<br /><br /> 詳細については、「[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。|  
|`Is` 演算子および `IsNot` 演算子の後。|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_21.vb)]<br /><br /> 詳細については、「[Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。|  
|メンバーの修飾子文字 \(`.`\) の後、メンバー名の前。  ただし、`With` ステートメントを使用する場合や型の初期化リストの値を指定する場合は、メンバーの修飾子文字の後に行連結文字 \(\_\) を含める必要があります。  `With` ステートメントやオブジェクト初期化リストを使用する場合は、代入演算子 \(`=` など\) の後で改行することをお勧めします。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_22.vb)]<br /><br /> 詳細については、「[With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)」または「[Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」を参照してください。|  
|XML 軸プロパティ修飾子 \(`.`、`.@`、`...`\) の後。  ただし、`With` キーワードを使用する場合は、メンバーの修飾子を指定する際に行連結文字 \(\_\) を含める必要があります。|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_23.vb)]<br /><br /> 詳細については、「[XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)」を参照してください。|  
|属性を指定する際の小なり記号 \(\<\) の後、または大なり記号 \(`>`\) の前。  また、属性を指定する際の大なり記号 \(`>`\) の後。  ただし、アセンブリ レベルまたはモジュール レベルの属性を指定する場合は、行連結文字 \(\_\) を含める必要があります。|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_24.vb)]<br /><br /> 詳細については、「[属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。|  
|クエリ演算子 \(`Aggregate`、`Distinct`、`From`、`Group By`、`Group Join`、`Join`、`Let`、`Order By`、`Select`、`Skip`、`Skip While`、`Take`、`Take While`、`Where`、`In`、`Into`、`On`、`Ascending`、および `Descending`\) の前後。  複数のキーワードで構成されるクエリ演算子 \(`Order By`、`Group Join`、`Take While`、および `Skip While`\) のキーワード間で改行することはできません。|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_25.vb)]<br /><br /> 詳細については、「[Queries](../../../visual-basic/language-reference/queries/queries.md)」を参照してください。|  
|`For Each` ステートメントの `In` キーワードの後。|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_26.vb)]<br /><br /> 詳細については、「[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)」を参照してください。|  
|コレクション初期化子の `From` キーワードの後。|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/statements_27.vb)]<br /><br /> 詳細については、「[Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。|  
  
## コメントの追加  
 ソース コードの意味は、記述した本人にとってさえ必ずしも自明であるとは限りません。  このため、ほとんどのプログラマは、たくさんのコメントを挿入してコードに注釈を付けています。  コード内のコメントには、後でそのコードを読んだり作業したりする人のために、プロシージャや特定の命令についての説明を記述できます。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はコンパイル時にコメントを無視するので、コンパイルされたコードがコメントの影響を受けることはありません。  
  
 コメント行の先頭には、アポストロフィ \(`'`\) または `REM` とそれに続く空白を指定します。  コメントはコード内のどこにでも追加できますが、文字列の中には指定できません。  ステートメントにコメントを付け加えるには、ステートメントの後にアポストロフィまたは `REM` を挿入し、続けてコメントを記述します。  この他、独立した行としてコメントを挿入することもできます。  具体的な例を次に示します。  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/statements_28.vb)]  
  
## コンパイル エラーの確認  
 入力したステートメントに構文エラーがあると、コード行の下に青い波線が表示されます。場合によっては、エラー メッセージも一緒に表示されます。  このような場合は、ステートメントの問題を見つけて修正する必要があります。エラーの内容は、タスク一覧や、エラー箇所の上にマウス ポインターを置くと表示されるエラー メッセージで確認できます。  コード内の構文エラーをすべて修正しないと、プログラムは正しくコンパイルされません。  
  
## 関連項目  
  
|||  
|-|-|  
|語句|定義|  
|[Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md)|`=`、`*=`、`&=` などの代入演算子について説明する言語リファレンス関連のトピックへのリンクが用意されています。|  
|[Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|要素と演算子を組み合わせて新しい値を作成する方法について説明します。|  
|[方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|単一のステートメントを複数行に分割する方法、および複数のステートメントを同じ行に配置する方法について説明します。|  
|[How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|コード行にラベル付けする方法について説明します。|