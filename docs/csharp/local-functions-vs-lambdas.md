---
title: "ローカル関数とラムダ式の比較"
description: "ローカル関数がラムダ式よりも適した選択肢となり得る理由について。"
keywords: "C#, .NET, .NET Core, 最新の機能, 新機能, ローカル関数, ラムダ式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: 366d7465433f2786960e22418b8aa46ba10e1fd1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/16/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>ローカル関数とラムダ式の比較

一見したところ、[ローカル関数](programming-guide/classes-and-structs/local-functions.md)と[ラムダ式](lambda-expressions.md)は、非常に似ています。
ローカル関数は、必要に応じてより使いやすく、単純なソリューションにすることができます。

階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。 まずは、ローカル関数を使用するバージョンです。

[!code-csharp(../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "ローカル関数を使用する再帰的階乗、")[LocalFunctionFactorial]]

ラムダ式を使用するバージョンの実装と比較します。

[!code-csharp(../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "ラムダ式を使用する再帰的階乗、")[26_LambdaFactorial]]

最初に、ラムダ式は、デリゲートをインスタンス化して、そのデリゲートを呼び出すことで実装されます。 ローカル関数は、メソッド呼び出しとして実装されます。
ラムダ式に必要なインスタンス化では、余分なメモリの割り当てが必要となり、タイム クリティカルなコード パスに影響を与えるパフォーマンス因子となる可能性があります。
ローカル関数では、このオーバーヘッドは発生しません。 上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。

この再帰メソッドは十分に単純で、ローカル関数がコンパイラによって生成された名前のプライベート メソッドとして実装されます。 他のプライベート メソッドとの唯一の違いは、外側の関数内に意味的な範囲が指定されていることです。

第 2 に、ローカル関数は、定義の前でも呼び出すことができます。 ラムダ式は、定義の前に宣言する必要があります。 つまり、先に示したように、ローカル関数は再帰的なアルゴリズムで使いやすくなります。

ラムダ式を使用したバージョンでは、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があります。 その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。
再帰的なアルゴリズムの作成は、ローカル関数を使用する方が簡単です。

第 3 に、ラムダ式の場合、コンパイラで匿名クラスとそのクラスのインスタンスを作成し、クロージャによってキャプチャされたすべての変数を常に格納する必要があります。 次の非同期の例について考えます。

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "ラムダ式を使用するメソッドを返すタスク、")]

このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。 ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。 その場合、割り当てが少なくなります。

> [!NOTE]
> このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。 ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。 ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "ローカル関数を持つメソッドを返すタスク")]

この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。

ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。
ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。

