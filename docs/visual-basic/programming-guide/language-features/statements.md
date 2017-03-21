---
title: "Visual Basic におけるステートメント |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:)
- constants, defining
- underlines
- constants, statements
- blue underline
- procedures, statements
- variables [Visual Basic], assigning
- line breaks, in code
- executable statements
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 001ea1cb5e651b95f808eefd47fd468f556550a1
ms.lasthandoff: 03/13/2017

---
# <a name="statements-in-visual-basic"></a>Visual Basic におけるステートメント
内のステートメント[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は完全な命令します。 これには、キーワード、演算子、変数、定数、および式を含めることができます。 各ステートメントは、次のカテゴリのいずれかに属します。  
  
-   **宣言ステートメント**変数、定数、またはプロシージャの名前し、データ型を指定することもできます。  
  
-   **実行可能なステートメント**、これが操作を開始します。 これらのステートメントは、メソッドまたは関数を呼び出すことができ、ループや分岐のコード ブロックすることができます。 実行可能なステートメントを含める**代入ステートメント**、値または式を代入する変数または定数。  
  
 このトピックでは、各カテゴリについて説明します。 また、このトピックは、1 行に複数のステートメントを結合する方法と、ステートメントを複数行にわたって継続する方法について説明します。  
  
## <a name="declaration-statements"></a>宣言ステートメント  
 名前を指定し、プロシージャ、変数、プロパティ、配列、および定数を定義するには、宣言のステートメントを使用します。 プログラミングの要素を宣言するときは、そのデータ型、アクセス レベル、およびスコープも定義できます。 詳細については、次を参照してください。[宣言された要素の特性](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)します。  
  
 次の例には、3 つの宣言が含まれています。  
  
 [!code-vb[VbVbalrStatements #&80;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 最初の宣言は、`Sub`ステートメントです。 そのに一致すると共に`End Sub`という名前のプロシージャ宣言ステートメント、`applyFormat`です。 指定`applyFormat`は`Public`、つまり、それを参照できるすべてのコードで呼び出すことができます。  
  
 2 番目の宣言は、`Const`定数を宣言するステートメント`limit`を指定して、`Integer`データ型と 33 の値。  
  
 3 番目の宣言は、`Dim`変数を宣言するステートメント`thisWidget`します。 データ型は、特定のオブジェクト、つまりからオブジェクトが作成される、`Widget`クラスです。 任意の基本データ型の場合に使用するアプリケーションで公開されているオブジェクトの種類の場合に変数を宣言することができます。  
  
### <a name="initial-values"></a>初期値  
 宣言ステートメントを含むコードを実行すると[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]は宣言された要素に必要なメモリを確保します。 要素には、値が含まれる場合[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]そのデータ型の既定値に初期化します。 詳細については、「動作」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
 次の例に示すように、その宣言の一部として変数に初期値を割り当てることができます。  
  
 [!code-vb[VbVbalrStatements #&81;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 使用して宣言するときに、明示的にそのクラスのインスタンスを作成する変数がオブジェクト変数の場合、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)キーワードとして次の例を示しています。  
  
 [!code-vb[VbVbalrStatements #&82;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 宣言ステートメントで指定した初期値が割り当てられていないことを変数にその宣言ステートメントに達するまでに注意してください。 それまでは、変数には、そのデータ型の既定値が含まれています。  
  
## <a name="executable-statements"></a>実行可能なステートメント  
 実行可能なステートメントでは、アクションを実行します。 手順については、いくつかのステートメントをループ処理、コードの別の場所に分岐を呼び出すしたり、式を評価することができます。 代入ステートメントは、実行可能なステートメントの特殊なケースです。  
  
 次の例では、`If...Then...Else`変数の値に基づくコードの別のブロックを実行する構造を制御します。 各コード ブロック内で、`For...Next`ループは、指定した回数だけを実行します。  
  
 [!code-vb[VbVbalrStatements&#83;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If`前の例ではステートメントのパラメーターの値をチェックする`clockwise`です。 値の場合`True`を呼び出す、`spinClockwise`メソッドの`aWidget`です。 値の場合`False`を呼び出す、`spinCounterClockwise`メソッドの`aWidget`です。 `If...Then...Else`制御構造がで終わる`End If`します。  
  
 `For...Next`各ブロック内でループ メソッドを呼び出して、適切な何度もの値と等しく、`revolutions`パラメーター。  
  
## <a name="assignment-statements"></a>代入ステートメント  
 代入ステートメントは、代入演算子の右側にある値を取得するので構成されている代入演算を実行 (`=`) し、次の例のように、左の要素に格納することです。  
  
 [!code-vb[VbVbalrStatements #&73;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 代入ステートメントが、変数のリテラル値 42 を格納する前の例で`v`します。  
  
### <a name="eligible-programming-elements"></a>使用できるプログラミング要素  
 代入演算子の左側にあるプログラミングの要素は、そのまま使用し、値を格納できる必要があります。 つまり、変数またはプロパティがある必要があります[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)、または配列の要素があります。 代入ステートメントのコンテキストでこのような要素とも呼ばれます、*左辺値*、「左辺値です」の。  
  
 代入演算子の右側にある値は、リテラル、定数、変数、プロパティ、配列の要素、その他の式、または関数呼び出しの任意の組み合わせから成る式によって生成されます。 次に例を示します。  
  
 [!code-vb[VbVbalrStatements #&74;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 上記の例では、変数に保持された値`y`変数に保持された値に`z`、関数への呼び出しによって返される値を追加および`findResult`です。 この式の合計値が変数に格納し、`x`です。  
  
### <a name="data-types-in-assignment-statements"></a>代入ステートメント内のデータ型  
 代入演算子も代入するだけでなく、数値`String`値は、次の例に示すようにします。  
  
 [!code-vb[VbVbalrStatements #&75;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 割り当てることも`Boolean`値のいずれかを使用して、`Boolean`リテラルまたは`Boolean`式で次の例を示しています。  
  
 [!code-vb[VbVbalrStatements #&76;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 同様のプログラミング要素への適切な値を割り当てることができます、 `Char`、 `Date`、または`Object`データ型。 そのインスタンスの作成元となるクラスを指定して宣言された要素をオブジェクトのインスタンスを割り当てることもできます。  
  
### <a name="compound-assignment-statements"></a>複合代入ステートメント  
 *複合代入ステートメント*まずプログラミング要素に割り当てる前に、式に対して操作を実行します。 次の例では、これらの演算子のいずれかを示しています`+=`右側の式の値によって、演算子の左側にある変数の値をインクリメントします。  
  
 [!code-vb[VbVbalrStatements #&77;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 前の例の値に 1 を加算する`n`でその新しい値を格納および`n`です。 短縮形である、次のステートメントに相当します。  
  
 [!code-vb[VbVbalrStatements #&78;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 この種類の演算子を使用して、さまざまな複合代入演算を実行できます。 これらの演算子とその詳細情報の一覧は、次を参照してください。[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)します。  
  
 連結代入演算子 (`&=`) の既存の最後に文字列を追加するために便利ですが、文字列を次の例に示すようにします。  
  
 [!code-vb[VbVbalrStatements #&79;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>代入ステートメントでは型変換  
 変数、プロパティ、または配列要素に割り当てる値は、代入先の要素に適切なデータ型でなければなりません。 一般に、目的の要素のと同じデータ型の値を生成しようとする必要があります。 ただし、一部の種類は、代入時に他の型に変換できます。  
  
 データ型の変換方法の詳細については、次を参照してください。 [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)します。 簡単に言えば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]拡大変換、他の種類を指定した型の値を自動的に変換します。 A*拡大変換*はそのいずれかが常に実行時に成功し、データが失われない。 たとえば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換、`Integer`値を`Double`該当する場合に、`Integer`に拡大変換`Double`します。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。  
  
 *縮小変換*(は、拡大しないもの) の実行時にエラーまたはデータ損失のリスクを実行します。 縮小変換を明示的に実行するには型変換関数を使用して、またはコンパイラに設定して、すべての変換を暗黙的に実行を行うことができます`Option Strict Off`します。 詳細については、次を参照してください。[暗黙的および明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)します。  
  
## <a name="putting-multiple-statements-on-one-line"></a>1 つの行に複数のステートメントを配置します。  
 複数のステートメントは、コロンで区切られた&1; 行に配置できます (`:`) 文字です。 次に例を示します。  
  
 [!code-vb[VbVbalrStatements #&70;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 ただし、場合によって不便なの構文には、この形式により、コードの読み取りおよびメンテナンスが困難です。 したがって、1 つのステートメントの行にしておくことをお勧めします。  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>複数の行にまたがるステートメント  
 ステートメントは、通常&1; つの行に収まるが長すぎるときに、後にアンダー スコア文字でスペースから成る行連結シーケンスを使用して次の行に続けることができます (`_`) 後にキャリッジ リターン。 次の例では、`MsgBox`実行可能なステートメントは&2; つの行を継続します。  
  
 [!code-vb[VbVbalrStatements #&71;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>暗黙的な行継続  
 多くの場合、アンダー スコア文字 (_) を使用せず、次の連続する行で、ステートメントを続行できます。 次の表には、次のコード行で、ステートメントが暗黙的に継続構文要素が一覧表示します。  
  
|構文要素|例|  
|---|---|  
|コンマの後 (`,`)。|[!code-vb[VbVbalrLineContinuation&#1;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|かっこの後 (`(`) または閉じかっこの前に、(`)`)。|[!code-vb[VbVbalrLineContinuation&#2;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|開いている中かっこの後 (`{`) または右中かっこの前に (`}`)。|[!code-vb[VbVbalrLineContinuation&#3;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)または[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)します。|  
|開いた後は、埋め込み式 (`<%=`) や組み込み式の終了前に (`%>`) XML リテラル内です。|[!code-vb[VbVbalrLineContinuation&4;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。|  
|連結演算子の後に (`&`)。|[!code-vb[VbVbcnConventions&#9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。|  
|After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation&#5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。|  
|After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.|[!code-vb[VbVbalrLineContinuation&#7;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。|  
|後に、`Is`と`IsNot`演算子。|[!code-vb[VbVbalrLineContinuation&#8;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。|  
|メンバー修飾子文字の後に (`.`) およびメンバー名の前にします。 ただし、次のメンバーの修飾子文字を使用しているときに行連結文字 (_) を含める必要があります、`With`ステートメントまたは型の初期化リストの値を指定します。 代入演算子の後で改行を検討してください (たとえば、 `=`) を使用する場合`With`ステートメントやオブジェクトの初期化リストです。|[!code-vb[VbVbalrLineContinuation&#5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> 詳細については、次を参照してください[としています.。ステートメントで終了して](../../../visual-basic/language-reference/statements/with-end-with-statement.md)または[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。|  
|XML 軸プロパティ修飾子後 (`.`または`.@`または`...`)。 使用しているときに、メンバーの修飾子を指定すると、行連結文字 (_) を含める必要がありますが、`With`キーワードです。|[!code-vb[VbVbalrLineContinuation&#9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> 詳細については、次を参照してください。 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)します。|  
|小後・不等号 (<) or="" before="" a="" greater-than="" sign=""></)>`>`) 属性を指定するとします。 値が高い後も-不等号 (`>`) 属性を指定するとします。 ただし、アセンブリ レベルまたはモジュール レベルの属性を指定する場合は、行連結文字 (_) を含める必要があります。|[!code-vb[VbVbalrLineContinuation&#10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> 詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)します。|  
|Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`). 複数のキーワードで構成されているクエリ演算子のキーワードの間に行を分割することはできません (`Order By`、 `Group Join`、 `Take While`、および`Skip While`)。|[!code-vb[VbVbalrLineContinuation&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> 詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/queries.md)します。|  
|後に、`In`のキーワード、`For Each`ステートメントです。|[!code-vb[VbVbalrLineContinuation&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> 詳細については、次を参照してください[ごとにしています.。次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。|  
|後に、`From`コレクション初期化子のキーワードです。|[!code-vb[VbVbalrLineContinuation&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> 詳細については、次を参照してください。[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)します。|  
  
## <a name="adding-comments"></a>コメントを追加します。  
 ソース コードは、常に自明ですが、それを記述したプログラマにすることもできません。 ために、コードを文書化をしたがって、ほとんどのプログラマください埋め込まれたコメントを多めに使用します。 コード内のコメントは、プロシージャ、または読み取り中または後で作業してすべてのユーザーが特定の命令に説明します。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイル時に、コメントを無視し、コンパイルされたコードには影響しません。  
  
 コメント行はアポストロフィで始まります (`'`) または`REM`後にスペースをします。 追加する任意の場所コードを除く文字列内にあります。 ステートメントにコメントを追加するには、アポストロフィを挿入または`REM`コメントに続くステートメントの後です。 コメントは、独自の個別の行に移動できます。 次の例は、これらの可能性を示しています。  
  
 [!code-vb[VbVbalrStatements #&72;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>コンパイル エラーをチェックします。  
 後のコード行を入力する場合は、青い波線 (エラー メッセージが表示されることにも)、行が表示されます、ステートメントに構文エラーがあります。 ステートメントの問題 (してタスク リストで検索して、またはエラーにマウス ポインターの上にカーソルを置くとエラー メッセージを読み取っています) は、修正してする必要があります。 コードですべての構文エラーを修正するまで、プログラムは正しくコンパイルは失敗します。  
  
## <a name="related-sections"></a>関連項目  
  
|用語|定義|  
|---|---|  
|[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|代入演算子をなどに記載されている言語のリファレンス ページへのリンク`=`、 `*=`、および`&=`です。|  
|[演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|新しい値を生成する演算子を使用して要素を結合する方法を示します。|  
|[方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|1 つのステートメントを複数の行に分割する方法と同じ行に複数のステートメントを配置する方法を示します。|  
|[方法 : ステートメントへのラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|コード行にラベルを付ける方法を示します。|
