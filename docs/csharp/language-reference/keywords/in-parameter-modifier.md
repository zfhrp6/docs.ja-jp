---
title: "in パラメーター修飾子 (C# リファレンス)"
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 035aac3e6b902f607e533b709713eb1d07c9774a
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="in-parameter-modifier-c-reference"></a>in パラメーター修飾子 (C# リファレンス)

`in` キーワードによって、参照により引数が渡されます。 [ref](ref.md) や [out](out-parameter-modifier.md) キーワードと似ています。ただし、`in` 引数を呼び出されたメソッドで変更することはできませんが、`ref` 引数は変更できます。また、`out` 引数は呼び出し元が変更する必要があり、これらの変更は呼び出し元コンテキストで監視可能です。

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

前の例は、`in` 修飾子が呼び出しサイトでは不要であることを示しています。 これはメソッド宣言でのみ必要です。

> [!NOTE] 
> `foreach` ステートメントの一部、または LINQ クエリの `join` 句の一部として、型パラメーターが反変であることを示すために `in` キーワードをジェネリック型パラメーターで使用することもできます。 これらのコンテキストでの `in` キーワードの使用の詳細については、これらすべての使用に関するリンクを提供する「[in](in.md)」を参照してください。
  
 `in` 引数として渡される変数は、メソッド呼び出しで渡される前に初期化する必要があります。 ただし、呼び出されたメソッドでは値の割り当てや、引数の変更を行うことはできません。  
  
 `in`、`ref`、`out`キーワードは実行時の動作が異なりますが、コンパイル時にメソッド シグネチャの一部とは見なされません。 したがって、唯一の違いが、1 つのメソッドは `ref` または `in` 引数を受け取り、もう一方のメソッドは `out` 引数を受け取ることである場合、メソッドはオーバーロードできません。 たとえば、次のコードはコンパイルされません。  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
`in` の有無に基づくオーバーロードは可能ですが、コンパイラの警告が生成されます。  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

呼び出し元メソッドでは値を変更できないため、プロパティまたは定数を `in` パラメーターとして渡すことができます。
  
次の種類のメソッドには、`in`、`ref`、`out` キーワードを使用することはできません。  
  
- [async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。  
  
- [yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。  

通常は、`in` 引数を宣言して、値で引数を渡すために必要なコピー操作を回避します。 これは、引数が構造体または構造体の配列である場合に最も有効です。

## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)
