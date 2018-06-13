---
title: out パラメーター修飾子 (C# リファレンス)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.openlocfilehash: 76c2c27d4575918bb2ed4209a7ff7d2b0517b6f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288620"
---
# <a name="out-parameter-modifier-c-reference"></a><span data-ttu-id="5411a-102">out パラメーター修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5411a-102">out parameter modifier (C# Reference)</span></span>
<span data-ttu-id="5411a-103">`out` キーワードによって、参照により引数が渡されます。</span><span class="sxs-lookup"><span data-stu-id="5411a-103">The `out` keyword causes arguments to be passed by reference.</span></span> <span data-ttu-id="5411a-104">これは、[ref](ref.md) キーワードと似ていますが、`ref` では、変数を初期化してから渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5411a-104">It is like the [ref](ref.md) keyword, except that `ref` requires that the variable be initialized before it is passed.</span></span> <span data-ttu-id="5411a-105">[in](in-parameter-modifier.md) キーワードとも似ていますが、`in` では、呼び出されたメソッドで引数の値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5411a-105">It is also like the [in](in-parameter-modifier.md) keyword, except that `in` does not allow the called method to modify the argument value.</span></span> <span data-ttu-id="5411a-106">`out` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方で `out` キーワードを明示的に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5411a-106">To use an `out` parameter, both the method definition and the calling method must explicitly use the `out` keyword.</span></span> <span data-ttu-id="5411a-107">例:</span><span class="sxs-lookup"><span data-stu-id="5411a-107">For example:</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#1)]  

> [!NOTE] 
> <span data-ttu-id="5411a-108">`out` キーワードは、ジェネリック型パラメーターと共に使用すると、型パラメーターが共変であることを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="5411a-108">The `out` keyword can also be used with a generic type parameter to specify that the type parameter is covariant.</span></span> <span data-ttu-id="5411a-109">このコンテキストでの `out` キーワードの使用方法の詳細については、「[out (ジェネリック修飾子)](out-generic-modifier.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5411a-109">For more information on the use of the `out` keyword in this context, see [out (Generic Modifier)](out-generic-modifier.md).</span></span>
  
<span data-ttu-id="5411a-110">`out` の引数として渡される変数は、メソッド呼び出しで渡される前に初期化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5411a-110">Variables passed as `out` arguments do not have to be initialized before being passed in a method call.</span></span> <span data-ttu-id="5411a-111">ただし、呼び出されたメソッドでは、メソッドから制御が返される前に値を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5411a-111">However, the called method is required to assign a value before the method returns.</span></span>  
  
<span data-ttu-id="5411a-112">`in`、`ref`、`out`キーワードは実行時の動作が異なりますが、コンパイル時にメソッド シグネチャの一部とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="5411a-112">Although the `in`, `ref`, and `out` keywords cause different run-time behavior, they are not considered part of the method signature at compile time.</span></span> <span data-ttu-id="5411a-113">したがって、唯一の違いが、1 つのメソッドは `ref` または `in` 引数を受け取り、もう一方のメソッドは `out` 引数を受け取ることである場合、メソッドはオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="5411a-113">Therefore, methods cannot be overloaded if the only difference is that one method takes a `ref` or `in` argument and the other takes an `out` argument.</span></span> <span data-ttu-id="5411a-114">たとえば、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="5411a-114">The following code, for example, will not compile:</span></span>  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
<span data-ttu-id="5411a-115">ただし、一方のメソッドが `ref`、`in`、または `out` 引数を受け取り、もう一方のメソッドにいずれの修飾子もない場合は、オーバーロードを実行できます。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5411a-115">Overloading is legal, however, if one method takes a `ref`, `in`, or `out` argument and the other has none of those modifiers, like this:</span></span>  
  
[!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#2)]  

<span data-ttu-id="5411a-116">コンパイラは、呼び出しサイトのパラメーター修飾子と、メソッド呼び出しで使用されるパラメーター修飾子を照合して、最適なオーバーロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="5411a-116">The compiler chooses the best overload by matching the parameter modifiers at the call site to the parameter modifiers used in the method call.</span></span>
 
<span data-ttu-id="5411a-117">プロパティは変数ではないため、`out` パラメーターとして渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5411a-117">Properties are not variables and therefore cannot be passed as `out` parameters.</span></span>
  
 <span data-ttu-id="5411a-118">配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5411a-118">For information about passing arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="5411a-119">次の種類のメソッドには、`in`、`ref`、`out` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5411a-119">You can't use the `in`, `ref`, and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="5411a-120">[async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。</span><span class="sxs-lookup"><span data-stu-id="5411a-120">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="5411a-121">[yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。</span><span class="sxs-lookup"><span data-stu-id="5411a-121">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  

## <a name="declaring-out-arguments"></a><span data-ttu-id="5411a-122">`out` 引数の宣言</span><span class="sxs-lookup"><span data-stu-id="5411a-122">Declaring `out` arguments</span></span>   

 <span data-ttu-id="5411a-123">`out` 引数を含むメソッドを宣言すると、メソッドで複数の値を返す場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="5411a-123">Declaring a method with `out` arguments is useful when you want a method to return multiple values.</span></span> <span data-ttu-id="5411a-124">次の例では `out` を使用して、1 つのメソッド呼び出しで 3 つの変数を返します。</span><span class="sxs-lookup"><span data-stu-id="5411a-124">The following example uses `out` to return three variables with a single method call.</span></span> <span data-ttu-id="5411a-125">3 番目の引数が null に割り当てられることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5411a-125">Note that the third argument is assigned to null.</span></span> <span data-ttu-id="5411a-126">これにより、必要に応じてメソッドが値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="5411a-126">This enables methods to return values optionally.</span></span>  
  
[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#3)]  

 <span data-ttu-id="5411a-127">[Try パターン](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md)には、操作が成功したか失敗したかを示す `bool` を返す処理と、操作によって生成された値を `out` 引数で返す処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5411a-127">The [Try pattern](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) involves returning a `bool` to indicate whether an operation succeeded and failed, and returning the value produced by the operation in an `out` argument.</span></span> <span data-ttu-id="5411a-128">[DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) メソッドなど、多くの解析メソッドでこのパターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5411a-128">A number of parsing methods, such as the [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) method, use this pattern.</span></span>
   
## <a name="calling-a-method-with-an-out-argument"></a><span data-ttu-id="5411a-129">`out` 引数を含むメソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="5411a-129">Calling a method with an `out` argument</span></span>

<span data-ttu-id="5411a-130">C# 6 以前では、変数を別のステートメントで宣言してから `out` 引数として渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5411a-130">In C# 6 and earlier, you must declare a variable in a separate statement before you pass it as an `out` argument.</span></span> <span data-ttu-id="5411a-131">次の例では、`number` という名前の変数を宣言してから、文字列を数値に変換する [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) メソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="5411a-131">The following example declares a variable named `number` before it is passed to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method, which attempts to convert a string to a number.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#4)]  

<span data-ttu-id="5411a-132">C# 7.0 以降では、`out` 変数を、別の変数宣言内ではなく、メソッド呼び出しの引数リスト内で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="5411a-132">Starting with C# 7.0, you can declare the `out` variable in the argument list of the method call, rather than in a separate variable declaration.</span></span> <span data-ttu-id="5411a-133">これにより、よりコンパクトで読みやすいコードが生成されます。また、メソッド呼び出しの前に誤って変数に値を割り当てることもなくなります。</span><span class="sxs-lookup"><span data-stu-id="5411a-133">This produces more compact, readable code, and also prevents you from inadvertently assigning a value to the variable before the method call.</span></span> <span data-ttu-id="5411a-134">次の例は前の例と似ていますが、[Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) メソッドの呼び出しで `number` 変数を定義している点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5411a-134">The following example is like the previous example, except that it defines the `number` variable in the call to the [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) method.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#5)]  
   
<span data-ttu-id="5411a-135">前の例では、`number` 変数は `int` として厳密に型指定されています。</span><span class="sxs-lookup"><span data-stu-id="5411a-135">In the previous example, the `number` variable is strongly typed as an `int`.</span></span> <span data-ttu-id="5411a-136">次の例のように、暗黙的に型指定されたローカル変数を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="5411a-136">You can also declare an implicitly typed local variable, as the following example does.</span></span>

[!code-csharp-interactive[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/OutParameterModifier.cs#6)]  
   
## <a name="c-language-specification"></a><span data-ttu-id="5411a-137">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5411a-137">C# Language Specification</span></span>  
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5411a-138">参照</span><span class="sxs-lookup"><span data-stu-id="5411a-138">See Also</span></span>  
 [<span data-ttu-id="5411a-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5411a-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5411a-140">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5411a-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5411a-141">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="5411a-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5411a-142">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="5411a-142">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
