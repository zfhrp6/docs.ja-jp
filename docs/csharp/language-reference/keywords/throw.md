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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 955f6d87614e0b452ace162e79e34aec9decad54
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="throw-c-reference"></a><span data-ttu-id="368e8-102">throw (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="368e8-102">throw (C# Reference)</span></span>
<span data-ttu-id="368e8-103">プログラムの実行中に例外が発生したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="368e8-103">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="368e8-104">コメント</span><span class="sxs-lookup"><span data-stu-id="368e8-104">Remarks</span></span>

<span data-ttu-id="368e8-105">`throw` の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="368e8-105">The syntax of `throw` is:</span></span>

```csharp
throw [e]
```
<span data-ttu-id="368e8-106">ここで `e` は <xref:System.Exception?displayProperty=fullName> から派生したクラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="368e8-106">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=fullName>.</span></span> <span data-ttu-id="368e8-107">次の例では、`GetNumber` という名前のメソッドに渡された引数が内部配列の有効なインデックスに対応していない場合に、`throw` ステートメントを使用して @System.IndexOutOfRangeException をスローします。</span><span class="sxs-lookup"><span data-stu-id="368e8-107">The following example uses the `throw` statement to throw an @System.IndexOutOfRangeException if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

<span data-ttu-id="368e8-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="368e8-108">[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]</span></span>  

<span data-ttu-id="368e8-109">その後、メソッドの呼び出し元が `try-catch` ブロックまたは `try-catch-finally` ブロックを使用して、スローされた例外を処理します。</span><span class="sxs-lookup"><span data-stu-id="368e8-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="368e8-110">次の例では、`GetNumber` メソッドによってスローされた例外を処理します。</span><span class="sxs-lookup"><span data-stu-id="368e8-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

<span data-ttu-id="368e8-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="368e8-111">[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]</span></span>  

## <a name="re-throwing-an-exception"></a><span data-ttu-id="368e8-112">例外の再スロー</span><span class="sxs-lookup"><span data-stu-id="368e8-112">Re-throwing an exception</span></span>

<span data-ttu-id="368e8-113">`throw` を `catch` ブロックで使用すると、`catch` ブロックで処理された例外を再スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="368e8-113">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="368e8-114">この場合、`throw` は例外オペランドを使用しません。</span><span class="sxs-lookup"><span data-stu-id="368e8-114">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="368e8-115">これは、メソッドが呼び出し元から他のライブラリ メソッドに引数を渡し、そのライブラリ メソッドが、呼び出し元に渡す必要がある例外をスローするときに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="368e8-115">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="368e8-116">たとえば、次の例では、初期化されていない文字列の最初の文字を取得しようとしたときにスローされた @System.NullReferenceException を再スローします。</span><span class="sxs-lookup"><span data-stu-id="368e8-116">For example, the following example re-throws an @System.NullReferenceException that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span> 

<span data-ttu-id="368e8-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="368e8-117">[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="368e8-118">`catch` ブロックで `throw e` 構文を使用すると、呼び出し元に渡す新しい例外をインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="368e8-118">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="368e8-119">この場合、@System.Exception.Stacktrace プロパティから使用できる、元の例外のスタック トレースが保持されません。</span><span class="sxs-lookup"><span data-stu-id="368e8-119">In this case, the stack trace of the original exception, which is available from the @System.Exception.Stacktrace property, is not preserved.</span></span>
 
## <a name="the-throw-expression"></a><span data-ttu-id="368e8-120">`throw` 式</span><span class="sxs-lookup"><span data-stu-id="368e8-120">The `throw` expression</span></span>

<span data-ttu-id="368e8-121">C# 7 以降、`throw` は、式およびステートメントとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="368e8-121">Starting with C# 7, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="368e8-122">これにより、以前サポートされていなかったコンテキストでの例外のスローが可能になります。</span><span class="sxs-lookup"><span data-stu-id="368e8-122">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="368e8-123">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="368e8-123">These include:</span></span>

- <span data-ttu-id="368e8-124">[条件演算子](../operators/conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="368e8-124">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="368e8-125">次の例では、`throw` 式を使用して、メソッドに空の文字列配列が渡された場合に @System.ArgumentException をスローします。</span><span class="sxs-lookup"><span data-stu-id="368e8-125">The following example uses a `throw` expression to throw an @System.ArgumentException if a method is passed an empty string array.</span></span> <span data-ttu-id="368e8-126">C# 7 より前では、このロジックが `if`/`else` ステートメントで使用されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="368e8-126">Before C# 7, this logic would need to appear in an `if`/`else` statement.</span></span>

   <span data-ttu-id="368e8-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="368e8-127">[!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]</span></span>  
  
- <span data-ttu-id="368e8-128">[ull 合体演算子](../operators/null-conditional-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="368e8-128">[the null-coalescing operator](../operators/null-conditional-operator.md).</span></span> <span data-ttu-id="368e8-129">次の例では、null 合体演算子と共に `throw` 式を使用して、`Name` プロパティに割り当てられた文字列が `null` の場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="368e8-129">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>
 
   <span data-ttu-id="368e8-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="368e8-130">[!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]</span></span>  
 
- <span data-ttu-id="368e8-131">式形式の[ラムダ](../../lambda-expressions.md)またはメソッド。</span><span class="sxs-lookup"><span data-stu-id="368e8-131">an expression-bodied [lambda](../../lambda-expressions.md) or method.</span></span> <span data-ttu-id="368e8-132">次の例では、@System.DateTime 値への変換がサポートされていないため @System.InvalidCastException をスローする、式形式のメソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="368e8-132">The following example illustrates an expression-bodied method that throws an @System.InvalidCastException because a conversion to a @System.DateTime value is not supported.</span></span>
 
   <span data-ttu-id="368e8-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="368e8-133">[!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]</span></span>  
 
  
## <a name="c-language-specification"></a><span data-ttu-id="368e8-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="368e8-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="368e8-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="368e8-135">See Also</span></span>  
 <span data-ttu-id="368e8-136">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="368e8-137">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="368e8-138">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-138">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="368e8-139">[C++ の try、catch、および throw ステートメント](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-139">[The try, catch, and throw Statements in C++](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="368e8-140">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-140">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="368e8-141">[例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="368e8-141">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 [<span data-ttu-id="368e8-142">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="368e8-142">How to: Explicitly Throw Exceptions</span></span>](https://msdn.microsoft.com/library/xhcbs8fz)

