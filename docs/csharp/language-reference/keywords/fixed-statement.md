---
title: fixed ステートメント (C# リファレンス)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e26e7e7f15dd48cf029d5f67bf5ef0de3e19b7bb
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="fixed-statement-c-reference"></a>fixed ステートメント (C# リファレンス)

`fixed` ステートメントは、移動可能な変数がガベージ コレクターにより再配置されることを防ぎます。 `fixed` ステートメントは、[unsafe](unsafe.md) コンテキストでのみ許可されます。 `fixed` は、[固定サイズ バッファー](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)の作成にも使うことができます。

`fixed` ステートメントは、マネージ変数へのポインターを設定し、ステートメントの実行中にその変数を "固定" します。 移動可能なマネージド変数へのポインターは、`fixed` コンテキストでのみ有効です。 `fixed` コンテキストがない場合、ガベージ コレクションによって変数が予期せず再配置される可能性があります。 C# コンパイラでは、`fixed` ステートメントでマネージ変数へのポインターを割り当てることだけができます。

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

配列、文字列、固定サイズ バッファー、または変数のアドレスを使って、ポインターを初期化できます。 次の例では、変数のアドレス、配列、および文字列の使い方を示します。 固定サイズ バッファーについて詳しくは、「[固定サイズ バッファー](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)」をご覧ください。

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

C# 7.3 以降では、`fixed` ステートメントは、配列、文字列、固定サイズ バッファー、非マネージ型変数以外の型でも動作します。 `DangerousGetPinnableReference` という名前のメソッドを実装する型はピン留めできます。 `DangerousGetPinnableReference` は `ref` 変数を非マネージ型変数に返す必要があります。 詳しくは、「[ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)」を参照してください。 .NET Core 2.0 で導入された .NET 型 <xref:System.Span%601?displayProperty=nameWithType> と <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> はこのパターンを活用し、ピン留めできます。 以下の例を参照してください。

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

このパターンに参加する必要のある型を作成する場合は、パターンの実装の例について、「<xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType>」を参照してください。

複数のポインターは、すべて同じ型の場合、1 つのステートメントで初期化できます。

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

異なる型のポインターを初期化するには、次の例で示すように、`fixed` ステートメントを入れ子にします。

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

ステートメント内のコードの実行が済むと、固定された変数は固定を解除されて、ガベージ コレクションの対象になります。 そのため、`fixed` ステートメントの外側ではこれらの変数を参照しないでください。 `fixed` ステートメントで宣言された変数は、そのステートメントにスコープされるので、この処理が簡単になります。

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

`fixed` ステートメントで初期化されたポインターは読み取り専用変数です。 ポインター値を変更するには、2 つ目のポインター変数を宣言し、それを変更する必要があります。 `fixed` ステートメントで宣言された変数は変更できません。

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


unsafe モードでは、スタック上のメモリを割り当てることができ、スタックはガベージ コレクションの対象にならないので、固定する必要はありません。 詳しくは、「[stackalloc](stackalloc.md)」をご覧ください。

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>C# 言語仕様

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>参照

 [C# リファレンス](../index.md)  
 [C# プログラミング ガイド](../../programming-guide/index.md)  
 [C# のキーワード](index.md)  
 [unsafe](unsafe.md)  
 [固定サイズ バッファー](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
