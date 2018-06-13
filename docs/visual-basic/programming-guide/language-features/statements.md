---
title: Visual Basic におけるステートメント
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: 9953fb949c58c074169596dcf48b6df5e7b8f0af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655722"
---
# <a name="statements-in-visual-basic"></a>Visual Basic におけるステートメント
Visual Basic でのステートメントは、完全な命令です。 これは、キーワード、演算子、変数、定数、および式に含めることができます。 各ステートメントは、次のカテゴリのいずれかに属します。  
  
-   **宣言ステートメント**変数、定数、またはプロシージャの名前し、データ型を指定することもできます。  
  
-   **実行可能なステートメント**操作を開始します。 これらのステートメントは、メソッドまたは関数を呼び出すことができ、ループや分岐のコード ブロックすることができます。 実行可能なステートメントを含める**代入ステートメント**、変数または定数に値または式に代入します。  
  
 このトピックでは、各カテゴリについて説明します。 また、このトピックは、1 行に複数のステートメントを結合する方法と、ステートメントを複数の行にわたって継続する方法について説明します。  
  
## <a name="declaration-statements"></a>宣言ステートメント  
 名前を指定し、プロシージャ、変数、プロパティ、配列、および定数を定義するには、宣言ステートメントを使用します。 プログラミング要素を宣言する場合は、そのデータ型、アクセス レベルおよびスコープも定義できます。 詳細については、次を参照してください。[宣言された要素の特性](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)です。  
  
 次の例には、3 つの宣言が含まれています。  
  
 [!code-vb[VbVbalrStatements#80](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 最初の宣言は、`Sub`ステートメントです。 その照合と共に`End Sub`という名前のプロシージャ宣言ステートメントでは、`applyFormat`です。 指定`applyFormat`は`Public`、つまり、これを参照できる任意のコードで呼び出すことができます。  
  
 2 番目の宣言は、`Const`ステートメントでは、定数を宣言する`limit`を指定して、`Integer`データ型と 33 の値。  
  
 3 番目の宣言は、`Dim`ステートメントでは、変数を宣言する`thisWidget`です。 データ型は、特定のオブジェクト、つまりから、オブジェクトが作成された、`Widget`クラスです。 任意の基本データ型またはそれを使用しているアプリケーションで公開されているオブジェクトの種類の変数を宣言することができます。  
  
### <a name="initial-values"></a>初期値  
 宣言ステートメントを含むコードを実行すると、Visual Basic は、宣言された要素に必要なメモリを予約します。 要素には、値が含まれる、Visual Basic によりそのデータ型の既定値に初期化します。 詳細については、「動作」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
 次の例に示すように、その宣言の一部として変数に初期値を割り当てることができます。  
  
 [!code-vb[VbVbalrStatements#81](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 使用して宣言するときに、明示的にそのクラスのインスタンスを作成する、変数がオブジェクト変数である場合、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)キーワードとして次の例を示しています。  
  
 [!code-vb[VbVbalrStatements#82](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 宣言ステートメントで指定した初期値が割り当てられていないことを変数にその宣言ステートメントに到達するまでに注意してください。 それまでは、変数には、そのデータ型の既定値が含まれています。  
  
## <a name="executable-statements"></a>実行可能なステートメント  
 実行可能なステートメントでは、アクションを実行します。 プロシージャ コードでは、いくつかのステートメントをループの別の場所に分岐を呼び出すしたり、式を評価することができます。 代入ステートメントは、実行可能なステートメントの特殊なケースです。  
  
 次の例では、`If...Then...Else`制御構造を異なる変数の値に基づくコード ブロックを実行します。 各コード ブロック内で、`For...Next`ループが、指定した回数だけを実行します。  
  
 [!code-vb[VbVbalrStatements#83](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 `If`ステートメント前の例では、パラメーターの値をチェック`clockwise`です。 値が場合`True`、呼び出し、`spinClockwise`メソッドの`aWidget`します。 値が場合`False`、呼び出し、`spinCounterClockwise`メソッドの`aWidget`します。 `If...Then...Else`制御構造が終わります`End If`です。  
  
 `For...Next`ループの各ブロック内でメソッドを呼び出して適切な回数の値と等しい、`revolutions`パラメーター。  
  
## <a name="assignment-statements"></a>代入ステートメント  
 代入ステートメントが、代入演算子の右側にある値を取得するので構成された代入演算を実行 (`=`) 次の例のように、左の要素に格納するとします。  
  
 [!code-vb[VbVbalrStatements#73](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 代入ステートメントが変数にリテラル値 42 を格納する前の例で`v`です。  
  
### <a name="eligible-programming-elements"></a>使用できるプログラミング要素  
 代入演算子の左側にある、このプログラミング要素は、そのまま使用し、値を格納できる必要があります。 つまり、変数またはプロパティではない必要があります[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)、か、または配列の要素がある必要があります。 代入ステートメントのコンテキストでこのような要素と呼ぶことが、*左辺値*、「左の値」  
  
 代入演算子の右側にある値は、リテラル、定数、変数、プロパティ、配列の要素、その他の式、または関数の呼び出しの任意の組み合わせで構成できる式によって生成されます。 次に例を示します。  
  
 [!code-vb[VbVbalrStatements#74](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 上記の例では、変数に保持されている値`y`変数に保持されている値に`z`、関数の呼び出しによって返される値を追加および`findResult`です。 この式の合計値が変数に格納し、`x`です。  
  
### <a name="data-types-in-assignment-statements"></a>代入ステートメント内のデータ型  
 数値の値に加え、代入演算子は割り当てることができますも`String`値は、次の例に示すようにします。  
  
 [!code-vb[VbVbalrStatements#75](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 割り当てることもできます`Boolean`値のいずれかを使用して、`Boolean`リテラルまたは`Boolean`式として次の例を示しています。  
  
 [!code-vb[VbVbalrStatements#76](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 同様のプログラミング要素への適切な値を割り当てることができます、 `Char`、 `Date`、または`Object`データ型。 そのインスタンスの作成元のクラスを指定して宣言された要素をオブジェクト インスタンスを割り当てることもできます。  
  
### <a name="compound-assignment-statements"></a>複合代入ステートメント  
 *複合代入ステートメント*まずプログラミング要素に割り当てる前に、式に対して操作を実行します。 次の例は、これらの演算子のいずれかを示します`+=`右側の式の値によって、演算子の左側にある変数の値をインクリメントします。  
  
 [!code-vb[VbVbalrStatements#77](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 前の例に 1 の値を加算`n`でその新しい値を格納して`n`です。 短縮形は、次のステートメントのと同じ。  
  
 [!code-vb[VbVbalrStatements#78](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 この型の演算子を使用して、さまざまな複合代入演算を実行できます。 これらの演算子とその詳細情報の一覧は、次を参照してください。[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)です。  
  
 連結代入演算子 (`&=`) の既存の末尾に文字列を追加するために便利ですが、文字列を次の例に示すようにします。  
  
 [!code-vb[VbVbalrStatements#79](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>代入ステートメントでは型変換  
 変数、プロパティ、または配列要素に代入する値は、移行先の要素に適切なデータ型でなければなりません。 一般に、目的の要素のと同じデータ型の値を生成しようとする必要があります。 ただし、一部の型は、代入時に他の型に変換できます。  
  
 データ型の間で変換する方法の詳細については、次を参照してください。 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)です。 簡単に説明すると、Visual Basic に自動的に変換指定された型の値、拡大変換とその他の種類します。 A*拡大変換*はで常に実行時に成功し、データが失われない。 たとえば、Visual Basic の変換、`Integer`値を`Double`適切な場合、ため`Integer`に拡大変換`Double`です。 詳細については、「 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 *縮小変換*、実行時にエラーやデータ損失のリスクを実行 (拡大変換がないもの)。 縮小変換を明示的に実行するには型変換関数を使用して、またはコンパイラに設定してすべての変換を暗黙的に実行を指示する`Option Strict Off`です。 詳細については、次を参照してください。[暗黙的および明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)です。  
  
## <a name="putting-multiple-statements-on-one-line"></a>1 つの行に複数のステートメントを適用します。  
 コロンで区切られた 1 行に複数のステートメントを持つことができます (`:`) 文字です。 次に例を示します。  
  
 [!code-vb[VbVbalrStatements#70](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 場合によっては便利な場合の構文には、この形式により、コードの読み取りおよびメンテナンス ハードです。 したがって、1 つのステートメントを行を保持することをお勧めします。  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>複数の行にまたがるステートメント  
 ステートメントは、通常、1 行に収まるが長すぎるときにスペースとアンダー スコア文字で構成される行連結シーケンスを使用して次の行に続けることができます (`_`) 後にキャリッジ リターン。 次の例で、 `MsgBox` 2 行にまたがって実行可能なステートメントが続きます。  
  
 [!code-vb[VbVbalrStatements#71](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>暗黙的な行の連結  
 多くの場合、アンダー スコア文字 (_) を使用せず、次の連続する行に、ステートメントを続行できます。 次の表には、次のコード行で、ステートメントが暗黙的に継続される構文要素が一覧表示します。  
  
|構文要素|例|  
|---|---|  
|コンマの後 (`,`)。|[!code-vb[VbVbalrLineContinuation#1](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|始めかっこの後に (`(`) または閉じかっこの前に、(`)`)。|[!code-vb[VbVbalrLineContinuation#2](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|開いている中かっこの後に (`{`) や右中かっこの前に (`}`)。|[!code-vb[VbVbalrLineContinuation#3](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)または[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)です。|  
|埋め込み式を開いた後 (`<%=`) または埋め込み式の終わりの前に (`%>`)、XML リテラル内で。|[!code-vb[VbVbalrLineContinuation#4](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> 詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。|  
|連結演算子の後に (`&`)。|[!code-vb[VbVbcnConventions#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)です。|  
|代入演算子の後に (`=`、 `&=`、 `:=`、 `+=`、 `-=`、 `*=`、 `/=`、 `\=`、 `^=`、 `<<=`、 `>>=`)。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)です。|  
|二項演算子の後に (`+`、 `-`、 `/`、 `*`、 `Mod`、 `<>`、 `<`、 `>`、 `<=`、 `>=`、 `^`、 `>>`、`<<`、 `And`、 `AndAlso`、 `Or`、 `OrElse`、 `Like`、 `Xor`) 式の中。|[!code-vb[VbVbalrLineContinuation#7](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)です。|  
|後に、`Is`と`IsNot`演算子。|[!code-vb[VbVbalrLineContinuation#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> 詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)です。|  
|メンバー修飾子文字の後 (`.`) およびメンバー名の前にします。 ただし、次のメンバーの修飾子文字を使用しているときに行連結文字 (_) を含める必要があります、`With`ステートメントまたは型の初期化リスト内の値を指定します。 代入演算子の後で改行を検討してください (たとえば、 `=`) を使用する場合`With`ステートメントやオブジェクト初期化リスト。|[!code-vb[VbVbalrLineContinuation#5](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> 詳細については、次を参照してください[としています...ステートメントで終了して](../../../visual-basic/language-reference/statements/with-end-with-statement.md)または[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)です。|  
|XML 軸プロパティ修飾子後 (`.`または`.@`または`...`)。 ただし、する必要があります行連結文字 (_) を使用しているときにメンバー修飾子を指定するときに、`With`キーワード。|[!code-vb[VbVbalrLineContinuation#9](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> 詳細については、次を参照してください。 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)です。|  
|小後-不等号 (<)、または前に、大きい-不等号 (`>`) 属性を指定するとします。 大きい後も、不等号 (`>`) 属性を指定するとします。 ただし、アセンブリ レベルまたはモジュール レベルの属性を指定する場合は、行連結文字 (_) を含める必要があります。|[!code-vb[VbVbalrLineContinuation#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> 詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)です。|  
|クエリ演算子の前後に (`Aggregate`、 `Distinct`、 `From`、 `Group By`、 `Group Join`、 `Join`、 `Let`、 `Order By`、 `Select`、 `Skip`、 `Skip While`、 `Take`、 `Take While`、 `Where`、 `In`、 `Into`、 `On`、 `Ascending`、および`Descending`)。 複数のキーワードで構成されているクエリ演算子のキーワードの間に線を中断することはできません (`Order By`、 `Group Join`、 `Take While`、および`Skip While`)。|[!code-vb[VbVbalrLineContinuation#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> 詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/queries.md)です。|  
|後に、`In`キーワード、`For Each`ステートメントです。|[!code-vb[VbVbalrLineContinuation#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> 詳細については、次を参照してください[ごとにしています...次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。|  
|後に、`From`コレクション初期化子内のキーワードです。|[!code-vb[VbVbalrLineContinuation#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> 詳細については、「[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。|  
  
## <a name="adding-comments"></a>コメントを追加します。  
 ソース コードは自明ですが、それを記述したプログラマにも常にします。 そのコードを文書化するには、したがって、ほとんどのプログラマください埋め込みコメント多めに使用します。 コード内のコメントは、プロシージャまたは特定の命令を読み取り、または後で作業してすべてのユーザーに説明します。 Visual Basic はコンパイル時に、コメントを無視し、コンパイルされたコードには影響しません。  
  
 コメント行アポストロフィで始まります (`'`) または`REM`空白が続きます。 追加する任意の場所コードを除く文字列内にあります。 ステートメントにコメントを追加するには、アポストロフィを挿入または`REM`コメントを続けて、ステートメントの後にします。 コメントは、独自の別々 の行に移動できます。 次の例では、これらの可能性を示します。  
  
 [!code-vb[VbVbalrStatements#72](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>コンパイル エラーをチェックします。  
 後のコード行を入力すると、行は、表示されます (エラー メッセージが表示されることも) 青色の波下線付きステートメントに構文エラーがします。 (タスクの一覧で検索して、かして、エラーにマウス ポインターの上にマウスをエラー メッセージを読み取って) ステートメントの問題が何を確認し、修正する必要があります。 すべての構文エラーを修正したコードで、まで正しくコンパイルするプログラムは失敗します。  
  
## <a name="related-sections"></a>関連項目  
  
|用語|定義|  
|---|---|  
|[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|代入演算子をカバーするなどの言語リファレンス ページへのリンクを提供`=`、 `*=`、および`&=`です。|  
|[演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|新しい値を生成する演算子を含む要素を結合する方法を示します。|  
|[方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|複数の行に単一のステートメントを分割する方法と同じ行に複数のステートメントを配置する方法を示します。|  
|[方法 : ステートメントへのラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|コードの行のラベルを付ける方法を示します。|
