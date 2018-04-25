---
title: stackalloc (C# リファレンス)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4cde254bb6a5601d10619c4a3bd2f00f1f146d3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# リファレンス)
`stackalloc` キーワードはアンセーフ コード コンテキストで使用され、スタックにメモリ ブロックを割り当てます。

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>コメント

このキーワードは、ローカル変数初期化子でのみ有効です。 次のコードはコンパイル エラーになります。

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

C# 7.3 以降では、`stackalloc` 配列に対して配列初期化子構文を使うことができます。 次のすべての宣言では、値が整数 `1`、`2`、`3` である 3 つの要素を含む配列が宣言されています。

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

ポインター型が使用されるため、`stackalloc` には [unsafe](unsafe.md) コンテキストが必要です。 詳しくは、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」をご覧ください。 

`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。

## <a name="examples"></a>使用例

次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。 それぞれの数値が、前の 2 つの数値の和になっています。 このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、 そのブロックのアドレスは `fib` ポインターに格納されます。 このメモリは、ガベージ コレクションの対象にはならないため、[fixed](fixed-statement.md) を使用して固定する必要はありません。 メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。 メソッドから制御が戻る前に、メモリを解放することはできません。

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

次の例では、整数の `stackalloc` 配列を、要素ごとに 1 ビットが設定されているビット マスクに初期化しています。 これは、C# 7.3 以降で使用可能な新しい初期化子の構文を示しています。

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>セキュリティ

アンセーフ コードは、セーフ コードほど安全ではありません。 ただし、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。 バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。

## <a name="c-language-specification"></a>C# 言語仕様
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>参照
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
