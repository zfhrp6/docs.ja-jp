---
title: コード内の特殊文字 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 932b38d97b36292e66bfad91a9a3799459d3b73c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654357"
---
# <a name="special-characters-in-code-visual-basic"></a>コード内の特殊文字 (Visual Basic)
場合によってアルファベットまたは数字ではない文字がコードでは、特殊文字を使用する必要があります。 区切り記号と Visual Basic の文字セット内の特殊文字は、コンパイラやコンパイル済みプログラムを実行するタスクの定義をプログラム テキストの整理から、さまざまな用途があります。 実行するオペレーションを指定するのには使用されません。  
  
## <a name="parentheses"></a>かっこ  
 など、プロシージャを定義するときに、かっこを使用して、`Sub`または`Function`です。 すべてのプロシージャの引数リストをかっこで囲む必要があります。 また、複雑な式で演算子の優先順位の既定の順序を上書きするには、特に論理グループは、変数または引数を格納するためかっこを使用します。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 次のコードでは、値の実行`d`8.225 しの値は、`e`は 3 です。 計算`d`の既定の優先順位を使用して`/`経由で`+`と同等です`d = b + (c / a)`です。 計算にかっこ`e`既定の優先順位をオーバーライドします。  
  
## <a name="separators"></a>[区切り記号]  
 区切り記号は、その名前が示す: コードのセクションを区切ります。 Visual basic での区切り記号はコロン (`:`)。 別々 の行ではなく 1 つの行に複数のステートメントを追加する場合は、区切り記号を使用します。 これにより、領域を節約し、コードの読みやすさを向上させます。 次の例は、コロンで区切られた 3 つのステートメントを示しています。  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 詳細については、次を参照してください。[する方法: 中断、コード内でステートメントを組み合わせて](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)です。  
  
 コロン (`:`) 文字は、ステートメント ラベルの指定にも使用します。 詳細については、次を参照してください。[する方法: ラベル ステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)です。  
  
## <a name="concatenation"></a>連結  
 使用して、`&`演算子*連結*、または文字列を一緒にリンクします。 混同しないでください、`+`演算子で、数値を一緒に追加します。 使用する場合、`+`数値を操作するときに連結する演算子が正しくない結果を取得することができます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 次のコードでは、値の実行`resultA`21.01 しの値は、 `resultB` 「10.0111」がします。  
  
## <a name="member-access-operators"></a>メンバー アクセス演算子  
 型のメンバーにアクセスするには、ドットを使用 (`.`) または感嘆符 (`!`) 型名およびメンバー名の間に演算子。  
  
### <a name="dot--operator"></a>ドット (.)演算子  
 使用して、`.`クラス、構造体、インターフェイス、または列挙体で演算子メンバー アクセス演算子として。 メンバーは、フィールド、プロパティ、イベント、またはメソッドにできます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>感嘆符 (!)演算子  
 使用して、`!`ディクショナリ アクセス演算子としての演算子では、クラスまたはインターフェイスのみです。 クラスまたはインターフェイスが既定のプロパティを 1 つを受け付ける必要`String`引数。 直後の識別子、`!`演算子、文字列として既定のプロパティに渡される引数の値になります。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 3 つの出力行の`MsgBox`値を表示すべて`32856`です。 最初の行がプロパティには、従来のアクセスを使用して`index`、2 つ目という事実を利用する`index`クラスの既定のプロパティは、 `hasDefault`、し、3 番目のクラスへのアクセスのディクショナリを使用しています。  
  
 なおの 2 番目のオペランド、`!`演算子は二重引用符で囲まれていない、有効な Visual Basic 識別子である必要があります (`" "`)。 つまり、リテラル文字列または文字列変数を使用することはできません。 次の行を最後の変更、`MsgBox`ための呼び出しにエラーが生成されます`"X"`にかっこで囲んだ文字列リテラルがします。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  既定のコレクションへの参照を明示的にする必要があります。 具体的には、使用することはできません、`!`演算子で遅延バインディングされた変数です。  
  
 `!`文字としても使用される、`Single`文字を入力します。  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
