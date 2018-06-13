---
title: Yield ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: f938ad29df54ade6722f3de33e931c851ade8c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604870"
---
# <a name="yield-statement-visual-basic"></a>Yield ステートメント (Visual Basic)
コレクションの次の要素を送信、`For Each...Next`ステートメントです。  
  
## <a name="syntax"></a>構文  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|用語|定義|  
|---|---|  
|`expression`|必須。 反復子関数の型に暗黙的に変換される式または`Get`アクセサーが含まれている`Yield`ステートメントです。|  
  
## <a name="remarks"></a>コメント  
 `Yield`ステートメントは、一度にコレクションの 1 つの要素を返します。 `Yield`ステートメントが iterator 関数に含まれるまたは`Get`アクセサーをコレクションに対するカスタム イテレーションを実行します。  
  
 使用して反復子関数を使用する、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)または LINQ クエリを実行します。 各反復処理、`For Each`ループが反復子関数を呼び出します。 ときに、`Yield`ステートメントが iterator 関数に到達`expression`が返されたコードの現在の場所が保持されます。 次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。  
  
 型からの暗黙的な変換が存在する必要があります`expression`で、`Yield`ステートメント、反復子の戻り値の型をします。  
  
 使用することができます、`Exit Function`または`Return`ステートメント、反復を終了します。  
  
 「生成」予約語ではないあり、特別な意味で使用されている場合にのみ、`Iterator`関数または`Get`アクセサー。  
  
 反復子関数の詳細については、`Get`アクセサーを参照してください[反復子](../../programming-guide/concepts/iterators.md)です。  
  
## <a name="iterator-functions-and-get-accessors"></a>反復子関数と Get アクセサー  
 反復子関数の宣言または`Get`アクセサーは、次の要件を満たす必要があります。  
  
-   含める必要があります、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子です。  
  
-   戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。  
  
-   これには指定できません`ByRef`パラメーター。  
  
 Iterator 関数は、イベント、コンス トラクター、静的コンス トラクターまたは静的のデストラクターで発生することはできません。  
  
 Iterator 関数では、匿名の関数を指定できます。 詳細については、「 [反復子](../../programming-guide/concepts/iterators.md)」を参照してください。  
  
## <a name="exception-handling"></a>例外処理  
 A`Yield`内のステートメントに含めることができます、`Try`のブロック、[を再試行してください.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。 A`Try`を持つブロック、`Yield`ステートメントが持つことができます`Catch`をブロックしてができます、`Finally`ブロックします。  
  
 A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (関数の外側で、反復子)、例外がスロー、 `Catch` iterator 関数内のブロックが実行されていないが、 `Finally` iterator 関数内のブロックを実行します。 A`Catch`反復子関数の内側のブロックは、iterator 関数内で発生する例外のみをキャッチします。  
  
## <a name="technical-implementation"></a>技術的な実装  
 次のコードを返します、 `IEnumerable (Of String)` iterator 関数からの要素を反復処理し、`IEnumerable (Of String)`です。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 呼び出し`MyIteratorFunction`関数の本体は実行されません。 この呼び出しでは、`IEnumerable(Of String)` が `elements` 変数に返されます。  
  
 `For Each` ループの反復処理では、<xref:System.Collections.IEnumerator.MoveNext%2A> について `elements` メソッドが呼び出されます。 この呼び出しでは、次の `MyIteratorFunction` ステートメントに到達するまで、`Yield` の本体が実行されます。 `Yield`ステートメントの値だけでなくを決定する式が返されます、`element`ループの本体によって消費の変数も、<xref:System.Collections.Generic.IEnumerator%601.Current%2A>要素のプロパティは、`IEnumerable (Of String)`です。  
  
 `For Each` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`Yield` ステートメントに到達したときに再度停止します。 `For Each`ループが完了するときに、反復子関数の末尾または`Return`または`Exit Function`ステートメントが到達します。  
  
## <a name="example"></a>例  
 次の例は、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 各反復処理、[各](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント本体で`Main`への呼び出しを作成、 `Power` iterator 関数。 Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。  
  
 Iterator メソッドの戻り値の型は<xref:System.Collections.Generic.IEnumerable%601>、反復子インターフェイス型です。 Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例は、反復子である `Get` アクセサーを示しています。 プロパティ宣言が含まれる、`Iterator`修飾子です。  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 その他の例では、次を参照してください。[反復子](../../programming-guide/concepts/iterators.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ステートメント](../../../visual-basic/language-reference/statements/index.md)
