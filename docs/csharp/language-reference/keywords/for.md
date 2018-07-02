---
title: for (C# リファレンス)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208008"
---
# <a name="for-c-reference"></a>for (C# リファレンス)

`for` ステートメントでは、指定されたブール式が `true` と評価される間に、ステートメントまたはステートメント ブロックが実行されます。

`for` ステートメント ブロック内の任意の位置で、[break](break.md) ステートメントを使ってループから抜けることができます。または、[continue](continue.md) ステートメントを使って、ループ内の次の繰り返しにスキップできます。 また、[goto](goto.md)、[return](return.md)、[throw](throw.md) ステートメントのいずれかを使って `for` ループを終了することもできます。
  
## <a name="structure-of-the-for-statement"></a>`for` ステートメントの構造

`for` ステートメントには、*initializer*、*condition*、*iterator* のセクションが定義されています。
  
```csharp
for (initializer; condition; iterator)  
    body  
```

3 つのセクションはすべて省略可能です。 ループの本体は、ステートメントまたはステートメントのブロックのいずれかです。

次の例では、`for` ステートメントと定義されているすべてのセクションが示されています。

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a>*initializer* セクション

*initializer* セクション内のステートメントは、ループに入る前に 1 回だけ実行されます。 *initializer* セクションは、次のいずれかです。

- ローカル ループ変数の宣言と初期化。ループの外からアクセスすることはできません。

- 次に列挙した 0 個以上のステートメント式 (コンマ区切り)。

  - [代入](../operators/assignment-operator.md)ステートメント

  - メソッドの呼び出し  

  - 前置または後置の[インクリメント](../operators/increment-operator.md)式 (`++i`、`i++` など)  

  - 前置または後置の[デクリメント](../operators/decrement-operator.md)式 (`--i`、`i--` など)  

  - [new](new-operator.md) キーワードを使用したオブジェクト作成

  - [await](await.md) 式

上記の例の *initializer* セクションは、ローカル ループ変数 `i` を宣言して初期化します。

```csharp
int i = 0
```

### <a name="the-condition-section"></a>*condition* セクション

*condition* セクション (ある場合) は、ブール式にする必要があります。 式は各ループ イテレーションの前に評価されます。 *condition* セクションが存在しないか、ブール式が `true` に評価される場合、次のループ イテレーションが実行されます。そうでない場合は、ループが終了します。

上記の例の*condition* セクションでは、ローカル ループ変数の値に基づいて、ループが終了するかどうかを決定します。

```csharp
i < 5
```

### <a name="the-iterator-section"></a>*iterator* セクション

ループ本体の反復処理が終わるたびに実行される処理を *iterator* セクションで定義します。 *iterator* セクションには、次のステートメント式を 0 個以上、コンマで区切って記述します。  

- [代入](../operators/assignment-operator.md)ステートメント

- メソッドの呼び出し  

- 前置または後置の[インクリメント](../operators/increment-operator.md)式 (`++i`、`i++` など)  

- 前置または後置の[デクリメント](../operators/decrement-operator.md)式 (`--i`、`i--` など)  

- [new](new-operator.md) キーワードを使用したオブジェクト作成

- [await](await.md) 式

上記の例の *iterator* セクションでは、ローカルのループ変数をインクリメントします。

```csharp
i++
```

## <a name="examples"></a>使用例

次のコードは、`for` ステートメント セクションのやや特殊な使用例です。*initializer* セクションで外部ループ変数に値を代入し、*initializer* セクションと *iterator* セクションの両方でメソッドを呼び出しています。さらに、*iterator* セクションで 2 つの変数の値を変更しています。 **[実行]** を選択して、コード例を実行します。 その後に、コードを変更し、もう一度実行することができます。
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
次の例では、無限 `for` ループが定義されます。
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a>C# 言語仕様  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a>関連項目

[for ステートメント (C# 言語仕様)](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[C# リファレンス](../index.md)  
[C# プログラミング ガイド](../../programming-guide/index.md)  
[C# のキーワード](index.md)  
[foreach、in](foreach-in.md)  
[for ステートメント (C++)](/cpp/cpp/for-statement-cpp)  
[繰り返しステートメント](iteration-statements.md)
