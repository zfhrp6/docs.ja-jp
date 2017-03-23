---
title: "コード (Visual Basic) 内の特殊文字 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
dev_langs:
- VB
helpviewer_keywords:
- special characters, in code
- parentheses, using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator
- concatenation operators, special characters in code
- concatenation operators, vs. addition operator
- '! operator'
- separators, using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator
- addition operator
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
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
ms.openlocfilehash: 6d4b6e74ef3dfab3a7174da07cff7100fa4b2a2f
ms.lasthandoff: 03/13/2017

---
# <a name="special-characters-in-code-visual-basic"></a>コード内の特殊文字 (Visual Basic)
場合がありますコードでは、アルファベットまたは数字ではない文字が特殊文字を使用する必要があります。 句読点と特殊文字に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字セットに、コンパイラやコンパイル済みプログラムを実行するタスクの定義をプログラム テキストの整理から、さまざまな用途があります。 実行するオペレーションを指定するのには使用されません。  
  
## <a name="parentheses"></a>かっこ  
 など、プロシージャを定義するときに、かっこを使用して、`Sub`または`Function`です。 すべてのプロシージャの引数リストをかっこで囲む必要があります。 複雑な式で演算子の優先順位の既定の順序を上書きするには、特に変数または引数を論理グループに配置することのかっこを使用します。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions&#11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 次のコードでは、値の実行`d`8.225 との値は、`e`は 3 です。 計算`d`の既定の優先順位を使用して`/`経由で`+`と同じ`d = b + (c / a)`します。 計算にかっこ`e`既定の優先順位をオーバーライドします。  
  
## <a name="separators"></a>[区切り記号]  
 区切り記号は、その名前が示す: コードのセクションを区切ります。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、区切り記号はコロン (`:`)。 別々 の行ではなく単一の行で複数のステートメントを追加する場合は、区切り記号を使用します。 領域を節約し、コードの読みやすさが向上します。 次の例は、コロンで区切られた&3; つのステートメントを示しています。  
  
 [!code-vb[VbVbcnConventions&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 詳細については、次を参照してください。[方法: 区切りとコード内でステートメントを組み合わせて](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)します。  
  
 コロン (`:`) 文字は、ステートメント ラベルを識別するためにも使用します。 詳細については、次を参照してください。[方法: ラベル ステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)します。  
  
## <a name="concatenation"></a>連結  
 使用して、`&`の演算子*連結*、または文字列を一緒にリンクします。 混同しないでください、`+`演算子で、数値を加算します。 使用する場合、`+`数値を操作するときに連結する演算子を正しくない結果を得ることができます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions&#13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 次のコードでは、値の実行`resultA`21.01 との値は、`resultB`は「10.0111」です。  
  
## <a name="member-access-operators"></a>メンバー アクセス演算子  
 型のメンバーにアクセスするには、ドットを使用 (`.`) または感嘆符 (`!`) 型名およびメンバー名の間の演算子です。  
  
### <a name="dot--operator"></a>ドット (.)演算子  
 使用して、`.`クラス、構造体、インターフェイス、または列挙体のメンバー アクセス演算子としての演算子です。 メンバーは、フィールド、プロパティ、イベント、またはメソッドにできます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>感嘆符 (!)演算子  
 使用して、`!`ディクショナリ アクセス演算子としてクラスまたはインターフェイスでのみ演算子。 クラスまたはインターフェイスが既定のプロパティを&1; つを受け付ける必要`String`引数。 直後の識別子、`!`演算子が文字列として既定のプロパティに渡される引数の値になります。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions&#15;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 3 つの出力行の`MsgBox`値を表示すべて`32856`です。 最初の行がプロパティには、従来のアクセスを使用して`index`、もう&1; つという事実を利用する`index`クラスの既定のプロパティは、`hasDefault`クラスへのアクセスのディクショナリを使用しています。  
  
 なおの&2; 番目のオペランド、`!`演算子は二重引用符で囲まれていない、有効な Visual Basic 識別子である必要があります (`" "`)。 つまり、リテラル文字列または文字列変数を使用することはできません。 次の行を変更し、最後、`MsgBox`ために、呼び出しがエラーを生成`"X"`囲まれた文字列リテラルでは。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  既定のコレクションへの参照を明示的にする必要があります。 具体的には、使用することはできません、`!`演算子を遅延バインディングされた変数にします。  
  
 `!`としても使用される文字、`Single`文字を入力します。  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
