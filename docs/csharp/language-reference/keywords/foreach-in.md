---
title: foreach、in (C# リファレンス)
ms.date: 10/11/2017
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: c0b1481988a2e3199fc6d06ca30cb5194ab2f44c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
---
# <a name="foreach-in-c-reference"></a>foreach、in (C# リファレンス)

`foreach` ステートメントは、<xref:System.Collections.IEnumerable?displayProperty=nameWithType> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> インターフェイスを実装する配列またはオブジェクト コレクションのそれぞれの要素に対して埋め込みステートメントを繰り返します。 [foreach ステートメント](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)は、コレクションを繰り返し処理して目的の情報を取得するために使用しますが、予期しない副作用を防ぐため、ソース コレクションに対する項目の追加または削除には使用しないでください。 ソース コレクションに対して項目を追加または削除する必要がある場合は、[for](for.md) ループを使います。
  
 埋め込みステートメントは、配列またはコレクション内の各要素に対して繰り返し実行されます。 コレクション内の全要素に対する繰り返しが完了すると、制御は、`foreach` ブロックに続く次のステートメントに移動します。
  
 `foreach` ブロック内の任意の位置で、[break](break.md) キーワードを使ってループから抜けることができます。または、[continue](continue.md) キーワードを使って、ループ内の次の反復処理にスキップできます。

 [goto](goto.md) ステートメント、[return](return.md) ステートメント、または [throw](throw.md) ステートメントを使用して `foreach` ループを抜けることもできます。

 `foreach` キーワードとコード例の詳細については、以下のトピックを参照してください。  

 [配列での foreach の使用](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [方法: foreach を使用してコレクション クラスにアクセスする](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a>例

次のコードは、3 つの例を示しています。

> [!TIP]
> 例を変更して構文の実験をしたり、自身のユース ケースにより近い異なる使用方法を試したりできます。 「実行」を押してコードを実行し、編集したら再び「実行」を押します。

-   整数の配列の内容を表示する一般的な `foreach` ループ

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   同じ処理を行う [for](../../../csharp/language-reference/keywords/for.md) ループ

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   配列内の要素数のカウントを保持する `foreach` ループ

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>参照  

[foreach ステートメント (C# 言語仕様)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)

[C# リファレンス](../index.md)

[C# プログラミング ガイド](../../programming-guide/index.md)

[C# のキーワード](index.md)

[繰り返しステートメント](iteration-statements.md)

[for](for.md)
