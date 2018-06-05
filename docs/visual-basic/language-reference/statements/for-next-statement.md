---
title: For...Next ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 8c54189499b7d5b52cf93b4a0ae6cc47356bf57e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605330"
---
# <a name="fornext-statement-visual-basic"></a>For...Next ステートメント (Visual Basic)
ステートメントのグループを指定した回数だけ繰り返されます。  
  
## <a name="syntax"></a>構文  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>指定項目  
  
|パーツ|説明|  
|----------|-----------------|  
|`counter`|必要な`For`ステートメントです。 数値型の変数です。 ループの制御変数。 詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。|  
|`datatype`|任意。 データ型`counter`です。 詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。|  
|`start`|必須。 数値式です。 `counter` の初期値になります。|  
|`end`|必須。 数値式です。 最終値`counter`です。|  
|`step`|任意。 数値式です。 量`counter`ループのたびにインクリメントされます。|  
|`statements`|任意。 1 つまたは複数のステートメントの間で`For`と`Next`一定の回数を実行します。|  
|`Continue For`|任意。 次のループ反復に制御を転送します。|  
|`Exit For`|任意。 うちの制御を転送、`For`ループします。|  
|`Next`|必須。 定義を終了、`For`ループします。|  
  
> [!NOTE]
>  `To`キーワードは、カウンターの範囲を指定する次のステートメントで使用します。 このキーワードを使用することも、[を選択しています.ステートメントの case](../../../visual-basic/language-reference/statements/select-case-statement.md)および配列の宣言。 配列の宣言の詳細については、次を参照してください。 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
## <a name="simple-examples"></a>簡単な例  
 使用する、`For`しています.`Next`ステートメントのセットに指定された回数だけを繰り返し使用するときにします。  
  
 次の例で、`index`変数が 1 の値から開始して、終了の値の後に、ループの反復するたびにインクリメントされます`index`5 に到達します。  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 次の例で、`number`変数が 2 から開始され、終了の値の後に、ループの反復ごとに 0.25 で高い縮小効果が`number`0 に到達します。 `Step`の引数`-.25`ループの反復ごとに 0.25 で値が減少します。  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  A[中.While ステートメント終了](../../../visual-basic/language-reference/statements/while-end-while-statement.md)または[操作を行います.Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)しないわかっている場合に事前に、ループでステートメントを実行する回数をうまく動作します。 ただし、特定回数、ループを実行しようとする`For`しています.`Next`ループをお勧めします。 ループを最初に入力したときに、イテレーションの数を決定します。  
  
## <a name="nesting-loops"></a>ループの入れ子  
 入れ子にすることができます`For`別内で 1 つのループを記述することによってループします。 次の例で入れ子になった`For`しています.`Next`異なるステップ値を持つ構造体。 外側のループでは、ループのイテレーションごとに文字列を作成します。 内部では、ループのイテレーションごとにループ カウンター変数をデクリメントをループします。  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 ループを入れ子にする場合は、各ループが一意な必要があります`counter`変数。  
  
 互いにさまざまな種類の制御構造を入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)です。  
  
## <a name="exit-for-and-continue-for"></a>終了し、続行  
 `Exit For`ステートメントがすぐに終了させる、`For`しています.`Next` これに続くステートメントにループと転送の制御、`Next`ステートメントです。  
  
 `Continue For`ステートメントに制御を移しますすぐに、ループの次の反復処理します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)です。  
  
 次の例では、使用、`Continue For`と`Exit For`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 任意の数を配置する`Exit For`内のステートメント、`For`しています.`Next` ループします。 使用すると内で入れ子になった`For`しています.`Next` ループ、`Exit For`最も内側のループを終了し、入れ子の上位のレベルに制御を移します。  
  
 `Exit For` いくつかの条件を評価した後は、よく使用 (たとえば、 `If`.`Then`...`Else`構造体)。 使用することができます`Exit For`次の条件。  
  
-   反復処理を続行するは、不要なまたは不可能です。 値が間違っているか、終了要求は、この状態になる可能性があります。  
  
-   A`Try`しています.`Catch`...`Finally`ステートメントは、例外をキャッチします。 使用する場合があります`Exit For`の最後に、`Finally`ブロックします。  
  
-   これは、大規模なまたは無限も可能回数だけ実行できるループ、無限ループがあります。 このような条件を検出した場合を使用できます`Exit For`ループをエスケープするためにします。 詳細については、次を参照してください[操作を行います...ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。  
  
## <a name="technical-implementation"></a>技術的な実装  
 ときに、`For`しています.`Next`ループが開始、Visual Basic の評価`start`、 `end`、および`step`です。 Visual Basic では、この時間とし、割り当てにのみこれらの値を評価`start`に`counter`です。 ステートメントの前にブロックが実行される Visual Basic 比較`counter`に`end`です。 場合`counter`よりも大きいは既に、`end`値 (より小さい場合、または`step`が負の値)、`For`終了をループし、これに続くステートメントにパスを制御、`Next`ステートメントです。 それ以外の場合、ステートメント ブロックが実行されます。  
  
 Visual Basic が発生するたびに、`Next`ステートメントでは、インクリメント`counter`によって`step`を返すと、`For`ステートメントです。 もう一度比較`counter`に`end`、もう一度、ブロックが実行か、結果に応じて、ループを終了するとします。 までこの処理を続けます`counter`渡します`end`または`Exit For`ステートメントが見つかりました。  
  
 まで、ループが停止しない`counter`経過`end`です。 場合`counter`と等しい`end`ループを続行します。 ブロックを実行するかどうかを判断する比較では、 `counter`  <=  `end`場合`step`が正の値と`counter`  >=  `end`場合`step`が負の値。  
  
 値を変更する場合`counter`ループ内は、コードを読み取りやデバッグが困難にする可能性があります。 値を変更する`start`、 `end`、または`step`ループが最初に入力されたときに決定されたイテレーション値には影響しません。  
  
 ループを入れ子にする場合、コンパイラはエラーが発生するか、`Next`する前に外部の入れ子レベルのステートメント、`Next`内部レベルのステートメント。 ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複`counter`ですべて`Next`ステートメントです。  
  
### <a name="step-argument"></a>Step  
 値`step`正または負の値を指定できます。 このパラメーターは、次の表に従ってループ処理を決定します。  
  
|**ステップ値**|**場合に、ループが実行されます。**|  
|--------------------|--------------------------|  
|正またはゼロ|`counter` <= `end`|  
|負|`counter` >= `end`|  
  
 既定値の`step`は 1 です。  
  
###  <a name="BKMK_Counter"></a> カウンターの引数  
 次の表に示すかどうか`counter`全体を対象とする新しいローカル変数を定義`For…Next`ループします。 この決定によって異なるかどうか`datatype`が存在かどうかおよび`counter`は既に定義されています。  
  
|`datatype`存在しますか?|`counter`既に定義されていますか。|結果 (かどうか`counter`全体を対象とする新しいローカル変数を定義`For...Next`ループ)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|×|[はい]|いいえ、ため`counter`は既に定義されています。 場合のスコープ`counter`コンパイル警告が発生した、プロシージャに対してローカルにないです。|  
|×|×|はい。 データ型から推論されます、 `start`、 `end`、および`step`式。 型の推定については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。|  
|[はい]|[はい]|場合に限り、[はい]、既存の`counter`プロシージャの外部から変数を定義します。 その変数は別に維持します。 場合、既存のスコープ`counter`変数は、プロシージャに対してローカルに、コンパイル時エラーが発生します。|  
|[はい]|×|はい。|  
  
 データ型`counter`イテレーションでは、次の種類のいずれかを指定する必要がありますの種類を決定します。  
  
-   A `Byte`、 `SByte`、 `UShort`、 `Short`、 `UInteger`、 `Integer`、 `ULong`、 `Long`、 `Decimal`、 `Single`、または`Double`です。  
  
-   使用して宣言された列挙型、 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。  
  
-   `Object`。  
  
-   型`T`、次の演算子を持つ場所`B`型で使用できるは、`Boolean`式。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 必要に応じて指定することができます、`counter`に変数が、`Next`ステートメントです。 入れ子にしていない場合は特に、この構文は、プログラムの読みやすさを向上`For`ループします。 対応する表示される変数を指定する必要があります`For`ステートメントです。  
  
 `start`、 `end`、および`step`の型に拡大する任意のデータ型に式が評価される`counter`です。 ユーザー定義型を使用する場合`counter`を定義する必要があります、`CType`変換演算子の型に変換する`start`、 `end`、または`step`の型に`counter`です。  
  
## <a name="example"></a>例  
 次の例では、ジェネリック リストからすべての要素を削除します。 代わりに、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の例に示す、`For`しています.`Next`降順に反復処理するステートメント。 この例は、ためにこの手法を使用して、`removeAt`メソッドが低いインデックス値を持つ削除された要素の後に要素をによりします。  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## <a name="example"></a>例  
 次の例を使用して宣言されている列挙型を反復処理する[Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)です。  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例では、ステートメントのパラメーターが演算子のオーバー ロードを持つクラスを使用して、 `+`、 `-`、 `>=`、および`<=`演算子。  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic.List%601>  
 [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [コレクション](../../programming-guide/concepts/collections.md)
