---
title: "C# 7.2 の新機能"
description: "C# 7.2 の新機能の概要。"
keywords: "C# 言語の設計, 7.2, Visual Studio 2017,"
author: billwagner
ms.author: wiwagn
ms.date: 08/16/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: cc861f186bea681bb32a2f8041a7155026679987
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="whats-new-in-c-72"></a>C# 7.2 の新機能

C# 7.2 は、便利な機能が多数追加された、もう 1 つのポイント リリースです。
このリリースのテーマの 1 つは、不要なコピーや割り当てを回避して、さまざまな値の型の操作をより効率的に行うことです。 

他の機能も、小さくても、あると助かる機能です。

C# 7.2 では[言語バージョンの選択](csharp-7-1.md#language-version-selection)の構成要素を使用して、コンパイラ言語バージョンを選択します。

このリリースの新しい言語機能は次のとおりです。

* [値の型による参照セマンティクス](#reference-semantics-with-value-types)
  - 参照セマンティクスを使用したさまざまな値の型の使用を有効にする、構文の機能強化の組み合わせ。
* [末尾以外の名前付き引数](#non-trailing-named-arguments)
  - 名前付き引数の後ろに位置引数を続けることができます。
* [数値リテラルでの先頭のアンダースコア (_)](#leading-underscores-in-numeric-literals)
  - 数値リテラルの印刷桁の前に先頭のアンダースコア(_) を含めることができるようになりました。
* [`private protected` アクセス修飾子](#private-protected)
  - `private protected` アクセス修飾子によって、同じアセンブリ内の派生クラスのアクセスが有効になります。

## <a name="reference-semantics-with-value-types"></a>値の型による参照セマンティクス

7.2 で導入された言語機能では、参照セマンティクスを使用しているときに、さまざまな値の型を使用できます。 これらは、参照型の使用に関連するメモリの割り当てを生じさせずに、値の型のコピーを最小限に抑えてパフォーマンスを改善するように設計されています。 次のような機能があります。

 - パラメーターの `in` 修飾子。引数が参照によって渡されるが、呼び出されたメソッドでは変更されないことを指定します。
 - メソッド戻りの `ref readonly` 修飾子。メソッドが参照によってその値を戻しますが、そのオブジェクトに対する書き込みを許可しないことを指定します。
 - `readonly struct` 宣言。変更不可の構造体で、そのメンバー メソッドの `in` パラメーターとして渡す必要があることを示します。
 - `ref struct` 宣言。構造体型がマネージ メモリに直接アクセスし、常にスタック割り当てが必要であることを示します。

これらすべての変更の詳細については、[参照セマンティクスを持つ値の型の使用](../reference-semantics-with-value-types.md)に関するページを参照してください。

## <a name="non-trailing-named-arguments"></a>末尾以外の名前付き引数

メソッド呼び出しで、位置引数の前に名前付き引数を使用できるようになりました。ただし、そのような名前付き引数が正しい位置にある場合です。 詳細については、「[名前付き引数と省略可能な引数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)」を参照してください。

## <a name="leading-underscores-in-numeric-literals"></a>数値リテラルでの先頭のアンダースコア (_)

C# 7.0 の桁区切り記号のサポートの実装では、`_` をリテラル値の最初の文字にすることができませんでした。 16 進とバイナリの数値リテラルの先頭に `_` を使用できるようになりました。 

例:

```csharp
int binaryValue = 0b_0101_0101;
```

## `private protected`

最後に、新しい複合アクセス修飾子: `private protected` は、同じアセンブリで宣言されているクラスまたは派生クラスを含むことでメンバーにアクセスできることを示しています。 `protected internal` は同じアセンブリの派生クラスまたはクラスによるアクセスを許可していますが、`private protected` は同じアセンブリで宣言された派生型へのアクセスを制限しています。

詳細については、言語リファレンスの[アクセス修飾子](../language-reference/keywords/access-modifiers.md)に関するページを参照してください。
