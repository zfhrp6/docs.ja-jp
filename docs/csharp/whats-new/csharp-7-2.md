---
title: "7.2 c# の新機能"
description: "7.2 c# の新機能の概要。"
keywords: "C# 言語のデザイン、7.2、Visual Studio 2017、"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: a580a4a3a0a49e97ea8fb96699d1d978a9bc0a64
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="whats-new-in-c-72"></a>7.2 c# の新機能

C# 7.2 は、いくつかの便利な機能の追加をもう 1 つのポイント リリースです。
不要なコピーまたは割り当てを回避することで、値型より効率的にこのリリースの 1 つのテーマが扱うです。 

他の機能は、小さなが便利な機能です。

7.2 c# を使用して、[バージョンの言語の選択](csharp-7-1.md#language-version-selection)コンパイラ言語バージョンを選択する構成要素。

このリリースの新しい言語機能は次のとおりです。

* [値の型と参照セマンティクス](#reference-semantics-with-value-types)
  - 参照セマンティクスを使用して値型の使用を有効にする構文の機能強化の組み合わせ。
* [非末尾名前付き引数](#non-trailing-named-arguments)
  - 名前付き引数は、位置指定引数が続くことができます。
* [数値リテラルの先頭にアンダー スコア](#leading-underscores-in-numeric-literals)
  - 数値リテラルは、印刷桁の数字の前に先頭にアンダー スコアを保持できます。
* [`private protected`アクセス修飾子](#private-protected)
  - `private protected`アクセス修飾子、同じアセンブリ内の派生クラスのアクセスを有効にします。

## <a name="reference-semantics-with-value-types"></a>値の型と参照セマンティクス

7.2 で導入された機能の言語では、参照セマンティクスを使用しているときに、値の型を使用できます。 参照型の使用に関連付けられているメモリの割り当てを生じることがなくコピーの値の型を最小限に抑えることによってパフォーマンスを向上するためのものです。 機能は次のとおりです。

 - `in`でその引数が参照によって渡されますが、呼び出されたメソッドでは変更されませんを指定する、パラメーター修飾子。
 - `ref readonly`修飾子をメソッドが参照渡しでその値を返すが、そのオブジェクトへの書き込みを許可しないことを示すために、メソッドを返します。
 - `readonly struct`宣言、構造体は変更不可にしてとして渡す必要があることを示す、`in`そのメンバー メソッドのパラメーターです。
 - `ref struct`構造体型マネージ メモリに直接アクセスする必要があります常にスタック割り当てられることを示すために、宣言します。

詳細については、これらのすべての変更を読み取ることができる[参照セマンティクスを持つ値の型を使用して](../reference-semantics-with-value-types.md)です。

## <a name="non-trailing-named-arguments"></a>非末尾名前付き引数

メソッドの呼び出しは、適切な位置では、名前付き引数と位置指定引数の前に名前付き引数を使用してようになりました可能性があります。 詳細については、次を参照してください。[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)です。

## <a name="leading-underscores-in-numeric-literals"></a>数値リテラルの先頭にアンダー スコア

7.0 (C#) で桁区切り記号のサポートの実装を許可していない、`_`リテラル値の最初の文字であります。 16 進とバイナリの数値リテラルの開始可能性があります、`_`です。 

例:

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

最後に、新しい複合アクセス修飾子:`private protected`にメンバーは、同じアセンブリ内で宣言されている、派生クラスによってアクセス可能性があります。 中に`protected internal`派生クラスでは、同じアセンブリにクラスへのアクセス許可`private protected`同じアセンブリ内で宣言されている派生型へのアクセスを制限します。

詳細については、次を参照してください。[アクセス修飾子](../language-reference/keywords/access-modifiers.md)言語リファレンスでします。
