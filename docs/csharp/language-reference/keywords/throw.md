---
title: "throw (C# リファレンス)"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 81117b1419c2a9c3babd6a7429052e2b23e08a70
ms.openlocfilehash: 77f44a43b80c4cf1f12baadaaf6861b3b53244d9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/25/2017

---
# <a name="throw-c-reference"></a>throw (C# リファレンス)
プログラムの実行中に例外が発生したことを通知します。  
  
## <a name="remarks"></a>コメント

`throw` の構文は次のとおりです。

```csharp
throw [e]
```
ここで `e` は <xref:System.Exception?displayProperty=nameWithType> から派生したクラスのインスタンスです。 次の例では、`GetNumber` という名前のメソッドに渡された引数が内部配列の有効なインデックスに対応していない場合に、`throw` ステートメントを使用して @System.IndexOutOfRangeException をスローします。

[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

その後、メソッドの呼び出し元が `try-catch` ブロックまたは `try-catch-finally` ブロックを使用して、スローされた例外を処理します。 次の例では、`GetNumber` メソッドによってスローされた例外を処理します。

[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>例外の再スロー

`throw` を `catch` ブロックで使用すると、`catch` ブロックで処理された例外を再スローすることもできます。  この場合、`throw` は例外オペランドを使用しません。 これは、メソッドが呼び出し元から他のライブラリ メソッドに引数を渡し、そのライブラリ メソッドが、呼び出し元に渡す必要がある例外をスローするときに最も役立ちます。 たとえば、次の例では、初期化されていない文字列の最初の文字を取得しようとしたときにスローされた @System.NullReferenceException を再スローします。 

[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> `catch` ブロックで `throw e` 構文を使用すると、呼び出し元に渡す新しい例外をインスタンス化することもできます。 この場合、@System.Exception.Stacktrace プロパティから使用できる、元の例外のスタック トレースが保持されません。
 
## <a name="the-throw-expression"></a>`throw` 式

C# 7 以降、`throw` は、式およびステートメントとして使用できます。 これにより、以前サポートされていなかったコンテキストでの例外のスローが可能になります。 次の設定があります。

- [条件演算子](../operators/conditional-operator.md)。 次の例では、`throw` 式を使用して、メソッドに空の文字列配列が渡された場合に @System.ArgumentException をスローします。 C# 7 より前では、このロジックが `if`/`else` ステートメントで使用されている必要があります。

   [!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [ull 合体演算子](../operators/null-conditional-operator.md)。 次の例では、null 合体演算子と共に `throw` 式を使用して、`Name` プロパティに割り当てられた文字列が `null` の場合に例外をスローします。
 
   [!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- 式形式の[ラムダ](../../lambda-expressions.md)またはメソッド。 次の例では、@System.DateTime 値への変換がサポートされていないため @System.InvalidCastException をスローする、式形式のメソッドを示しています。
 
   [!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [C++ の try、catch、および throw ステートメント](../../../csharp/language-reference/keywords/try-catch.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [方法: 例外を明示的にスローする](https://msdn.microsoft.com/library/xhcbs8fz)

