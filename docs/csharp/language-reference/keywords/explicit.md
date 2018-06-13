---
title: explicit (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216478"
---
# <a name="explicit-c-reference"></a>explicit (C# リファレンス)
`explicit` キーワードは、キャストを使用して呼び出す必要があるユーザー定義型変換演算子を宣言します。 たとえば、次の演算子は摂氏というクラスを華氏というクラスに変換します。  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 この変換演算子は、次のように呼び出すことができます。  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 変換演算子は、ソースの型をターゲットの型に変換します。 変換演算子はソースの型によって提供されます。 暗黙的な変換とは異なり、変換演算子はキャストを使用して明示的に呼び出す必要があります。 変換操作によって例外が発生したり、情報が失われる可能性がある場合は、その操作を `explicit` としてマークする必要があります。 これにより、予期しない結果をもたらす可能性がある変換操作がコンパイラによって暗黙的に呼び出されるのを防止できます。  
  
 キャストを省略すると、コンパイル時エラー CS0266 が返されます。  
  
 詳しくは、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコードは、`Fahrenheit` クラスと `Celsius` クラスを提供する場合の例です。これらの各クラスは、他方のクラスへの明示的な変換演算子を提供します。  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>例  
 次のコードは、単一の 10 進数を表す構造体 (`Digit`) を定義する場合の例です。 `byte` を `Digit` に変換するための演算子が定義されていますが、すべてのバイトを `Digit` に変換できるとは限らないため、変換を explicit にしています。  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)  
 [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Chained user-defined explicit conversions in C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/) (C# でのユーザー定義の明示的変換の連結)
