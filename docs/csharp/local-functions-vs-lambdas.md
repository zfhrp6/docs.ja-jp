---
title: "ローカル関数とラムダ式の比較"
description: "ローカル関数がラムダ式よりも適した選択肢となり得る理由"
keywords: "C#, .NET, .NET Core, 最新の機能, 新機能, ローカル関数, ラムダ式"
author: BillWagner
ms.author: wiwagn
ms.date: 10/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bba2a8d183f928e298c452f6ec132f3eb9dffbd3
ms.lasthandoff: 03/13/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>ローカル関数とラムダ式の比較

一部のユース ケースでは、ローカル関数を作成しなくても、ラムダ式を作成して、使用できる場合があります。 次の非同期メソッドの例は、まさにそのような例です。

[!code-csharp(../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "ラムダ式を使用するメソッドを返すタスク、 ")[TaskLambdaExample]]

しかし、ラムダ式を定義して呼び出す代わりに、ローカル関数を使用する方が望ましい理由がいくつかあります。

第 1 に、ラムダ式の場合、コンパイラで匿名クラスとそのクラスのインスタンスを作成し、クロージャによってキャプチャされたすべての変数を格納する必要があります。 このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。 

第 2 に、ラムダ式は、デリゲートをインスタンス化して、そのデリゲートを呼び出すことで実装されます。 ローカル関数は、メソッド呼び出しとして実装されます。
ラムダ式に必要なインスタンス化では、余分なメモリの割り当てが必要となり、タイム クリティカルなコード パスに影響を与えるパフォーマンス因子となる可能性があります。
ローカル関数では、このオーバーヘッドは発生しません。

第 3 に、ローカル関数は、定義の前でも呼び出すことができます。 ラムダ式は、定義の前に宣言する必要があります。 つまり、ローカル関数は再帰的なアルゴリズムで使いやすくなります。

[!code-csharp(../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "ローカル関数を使用する再帰的階乗、")[LocalFunctionFactorial]]

ラムダ式を使用するバージョンの実装と比較します。

[!code-csharp(../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "ラムダ式を使用する再帰的階乗、")[26_LambdaFactorial]]

ラムダ式を使用したバージョンでは、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があります。 その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。
再帰的なアルゴリズムの作成は、ローカル関数を使用する方が簡単です。 

ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。
ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。


