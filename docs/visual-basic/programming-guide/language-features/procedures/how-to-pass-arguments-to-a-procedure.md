---
title: '方法: プロシージャに引数を渡す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: f393f17f87c5920fb9bfa2a2097c09d48bebdc16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650593"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a>方法: プロシージャに引数を渡す (Visual Basic)
プロシージャを呼び出すときに、かっこ内に引数リストを持つプロシージャの名前に従います。 プロシージャに定義されたすべての必須パラメーターに対応する引数を指定して、引数を指定することができます必要に応じて、`Optional`パラメーター。 指定しない場合、`Optional`呼び出しのパラメーターは、任意の以降の引数を指定している場合、引数リスト内での位置をマークするコンマを含める必要があります。  
  
 引数を渡すデータ型の対応するパラメーターの場合と異なるよう意図して`Byte`に`String`、型チェック スイッチを設定することができます ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) に`Off`です。 場合`Option Strict`は`On`、いずれかを使用する必要がありますまたは明示的な変換キーワードの変換を拡大します。 詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)です。  
  
 詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)です。  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a>プロシージャに 1 つまたは複数の引数を渡す  
  
1.  呼び出し元のステートメントでは、次のプロシージャ名を括弧をします。  
  
2.  かっこの内側には、引数リストを格納します。 プロシージャに定義された各必須パラメーターの引数を含めるし、引数はコンマで区切ります。  
  
3.  それぞれの引数は、対応するパラメーターの型、プロシージャに変換できるデータ型に評価される有効な式を定義することを確認します。  
  
4.  パラメーターとして定義されている場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)、引数リストに含めるか、これを省略することができます。 を省略した場合、プロシージャは、そのパラメーターに定義された既定値を使用します。  
  
5.  引数を省略した場合、`Optional`パラメーターとパラメーター リストで別のパラメーター後に、引数リスト内の余分なコンマが省略された引数の代わりをマークすることができます。  
  
     次の例では、Visual Basic<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数。  
  
     [!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]  
  
     前の例では、必要な最初の引数を表示するメッセージ文字列を指定します。 省略可能な 2 番目のパラメーター、メッセージ ボックスに表示するボタンを指定する引数を省略します。 呼び出しは、値を指定していないため`MsgBox`既定値を使用して`MsgBoxStyle.OKOnly`、のみが表示されます、 **[ok]** ボタンをクリックします。  
  
     引数リスト内の 2 つ目のコンマは省略すると 2 番目の引数の位置をマークし、最後の文字列は省略可能な 3 番目のパラメーターに渡される`MsgBox`、これは、タイトル バーに表示されるテキストです。  
  
## <a name="see-also"></a>関連項目

 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : プロシージャにパラメーターを定義する](./how-to-define-a-parameter-for-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [再帰プロシージャ](./recursive-procedures.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)  
