---
title: "Yield ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 393a9f4de3e801aed5932aef0e2b13d76b003965
ms.lasthandoff: 03/13/2017

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
|`expression`|必須です。 反復子関数の型に暗黙的に変換される式または`Get`アクセサーを含む、`Yield`ステートメントです。|  
  
## <a name="remarks"></a>コメント  
 `Yield`ステートメントには、一度にコレクションの&1; つの要素が返されます。 `Yield`ステートメントが iterator 関数に含めまたは`Get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。  
  
 使用して反復子関数を使用する、[ごとにしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-each-next-statement.md)または LINQ クエリ。 各反復処理、`For Each`ループが反復子関数を呼び出します。 ときに、`Yield`ステートメントが iterator 関数に到達`expression`が返され、コードの現在位置が保持されます。 次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。  
  
 型から暗黙的な変換が存在する必要があります`expression`で、`Yield`ステートメント、反復子の戻り値の型。  
  
 使用することができます、`Exit Function`または`Return`ステートメント、反復を終了します。  
  
 「メリットをもたらす」予約語ではない、特別な意味で使用されている場合にのみ、`Iterator`関数または`Get`アクセサー。  
  
 反復子関数の詳細については、`Get`アクセサーを参照してください[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)します。  
  
## <a name="iterator-functions-and-get-accessors"></a>反復子関数と Get アクセサー  
 反復子関数の宣言または`Get`アクセサーは、次の要件を満たす必要があります。  
  
-   含めることは、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子です。  
  
-   戻り値の型である必要があります<xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
-   いずれかを持つできません`ByRef`パラメーター。  
  
 Iterator 関数は、イベント、コンス トラクター、静的コンス トラクターまたは静的のデストラクターで発生することはできません。  
  
 反復子関数では、匿名関数を指定できます。 詳細については、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」をご覧ください。  
  
## <a name="exception-handling"></a>例外処理  
 A`Yield`ステートメントは、内で使用できます、`Try`のブロック、[しようとしています.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 A`Try`がブロック、`Yield`ステートメントにはできます`Catch`ブロック、およびことができますが、`Finally`ブロックします。  
  
 A`Yield`ステートメント内で使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (iterator 関数) の外部で、例外がスロー、 `Catch` iterator 関数内のブロックは実行されませんが、`Finally`反復子関数でのブロックを実行します。 A`Catch`反復子関数の内側のブロックは、反復子関数内で発生する例外だけをキャッチします。  
  
## <a name="technical-implementation"></a>技術的な実装  
 次のコードを返します。、 `IEnumerable (Of String)` iterator 関数からの要素を反復処理し、`IEnumerable (Of String)`です。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 呼び出し`MyIteratorFunction`関数の本体は実行されません。 この呼び出しでは、`IEnumerable(Of String)` が `elements` 変数に返されます。  
  
 反復処理で、 `For Each` 、ループ、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッドが呼び出される`elements`</xref:System.Collections.IEnumerator.MoveNext%2A>。 この呼び出しでは、次の `MyIteratorFunction` ステートメントに到達するまで、`Yield` の本体が実行されます。 `Yield`ステートメントが返す文字列処理関数の値だけでなくを決定する、`element`ループの本体によって使用するための変数も、 <xref:System.Collections.Generic.IEnumerator%601.Current%2A>、要素のプロパティは、 `IEnumerable (Of String)`</xref:System.Collections.Generic.IEnumerator%601.Current%2A> 。  
  
 `For Each` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`Yield` ステートメントに到達したときに再度停止します。 `For Each`ループが完了するときに、反復子関数の末尾、または`Return`または`Exit Function`ステートメントに達するとします。  
  
## <a name="example"></a>例  
 次の例は、`Yield`ステートメント内にある、[にしています.次](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 各反復処理、[ごと](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント本体で`Main`への呼び出しを作成、`Power`に反復処理します。 Iterator 関数を呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の反復処理で行われます。  
  
 Iterator メソッドの戻り値の型は、 <xref:System.Collections.Generic.IEnumerable%601>、反復子インターフェイス型</xref:System.Collections.Generic.IEnumerable%601>。 Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。  
  
 [!code-vb[VbVbalrStatements #&98;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例は、反復子である `Get` アクセサーを示しています。 プロパティ宣言が含まれる、`Iterator`修飾子です。  
  
 [!code-vb[VbVbalrStatements&#99;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 その他の例を参照してください。[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[vs_dev11_long](../../../csharp/includes/vs_dev11_long_md.md)]  
  
## <a name="see-also"></a>関連項目  
 [反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)   
 [ステートメント](../../../visual-basic/language-reference/statements/index.md)
