---
title: "ローカル関数とラムダ式の比較"
description: "ローカル関数がラムダ式よりも適した選択肢となり得る理由について。"
keywords: "C#, .NET, .NET Core, 最新の機能, 新機能, ローカル関数, ラムダ式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.openlocfilehash: 20312b58a24dc991791edad4bb92d3a8ca6d501a
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="local-functions-compared-to-lambda-expressions"></a>ラムダ式と比較して、ローカル関数

一見したところ、[ローカル関数](programming-guide/classes-and-structs/local-functions.md)と[ラムダ式](lambda-expressions.md)は、非常に似ています。 多くの場合は、ラムダ式とローカル関数を使用して、選択は、スタイルと各ユーザーの好みの問題です。 ただし、どちらか一方を認識しておく必要がありますを使用する実際の相違があります。

階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。 まずは、ローカル関数を使用するバージョンです。

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "Recursive factorial using local function")]

ラムダ式を使用するバージョンの実装と比較します。

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "Recursive factorial using lambda expressions")]

ローカルの関数名であります。 ラムダ式には、匿名メソッド、変数に割り当てられている`Func`または`Action`型です。 ローカル関数を宣言するときに、引数の型と戻り値の型には、関数の宣言の一部です。 ラムダの本体の一部ではなく式では、引数の型と戻り値の型は、ラムダ式の変数の型宣言の一部です。 これら 2 つの違いは、わかりやすいコードがあります。

ローカル関数は、ラムダ式よりも確実な割り当てのルールを設定します。 ローカル関数宣言は、スコープ内にある任意のコードの場所から参照できます。 ラムダ式は、アクセス (したりできる、ラムダ式を参照している delgate を通じて呼び出されます。) 前に、デリゲート変数に割り当てる必要があります。ラムダ式を使用したバージョンでは、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があります。 その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。
これらの相違点は、再帰的なアルゴリズムは簡単にローカル関数を使用して作成することを意味します。 宣言し、それ自体を呼び出すローカル関数を定義できます。 ラムダ式は、宣言、および同じラムダ式を参照する本文に再割り当てできるようにするには、既定値を割り当てる必要があります。

確実な代入規則では、ローカル関数またはラムダ epression によってキャプチャされたすべての変数にも影響します。 ローカル関数とラムダ式の規則の両方、キャプチャされた変数は間違いなく割り当てられている時点でローカル関数またはラムダ式をデリゲートに変換するときを要求します。 違いは、宣言する場合、ラムダ式をデリゲートに変換されます。 ローカル関数は、代理人として使用する場合にのみ、デリゲートに変換されます。 ローカル関数宣言をのみ、メソッドのように呼び出すことによって参照する場合は、デリゲートに変換されません。 その規則では、その外側のスコープ内の任意の便利な場所でローカル関数を宣言することができます。 すべての return ステートメントの後に、親メソッドの末尾にローカル関数を宣言する通常はします。

3 番目に、コンパイラを確実に外側のスコープでキャプチャされた変数を代入するローカル関数を有効にする静的な分析を実行できます。 次の例について考えます。

```csharp
bool M()
{
    int y;
    Local();
    return y;

    void Local() => y = 0;
}
```

コンパイラが判別されること`Local`確実割り当てます`y`呼び出されたときにします。 `Local`前に呼び出されます、`return`ステートメントでは、 `y` definitiely はで割り当てられている、`return`ステートメントです。

その分析を有効にする分析では、4 番目の相違点を使用できます。
使用によってローカル関数は常にラムダ式用に必要なヒープ割り当てを回避できます。 ローカル関数は、デリゲートに変換されていない場合、その他の形式のラムダまたはデリゲートに変換されるローカル関数によってキャプチャされるローカル関数によってキャプチャされる変数のいずれも、コンパイラは、ヒープ割り当てを回避できます。 

次の非同期の例について考えます。

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "Task returning method with lambda expression")]

このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。 ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。 その構造体の型は、ローカル関数への参照によって渡されます。 この実装の違いが、割り当てに保存されます。

ラムダ式のために必要なインスタンス化では、余分なメモリの割り当ては、タイム クリティカルなコード パスでのパフォーマンス要因となる可能性がありますを意味します。
ローカル関数では、このオーバーヘッドは発生しません。 上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。

> [!NOTE]
> このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。 ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。 ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。 `yield return`ステートメントがラムダ式で許可されていません。

ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。
ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。
