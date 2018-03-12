---
title: "ref (C# リファレンス)"
ms.date: 05/30/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b1e926bd1d9c3a8e0525ed02d102f26e6ec9abd
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="ref-c-reference"></a><span data-ttu-id="9c98c-102">ref (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9c98c-102">ref (C# Reference)</span></span>

<span data-ttu-id="9c98c-103">`ref` キーワードは、参照渡しで渡される値を示します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-103">The `ref` keyword indicates a value that is passed by reference.</span></span> <span data-ttu-id="9c98c-104">このキーワードは、3 つの異なるコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-104">It is used in three different contexts:</span></span> 

- <span data-ttu-id="9c98c-105">メソッド シグネチャとメソッドの呼び出しで、参照によってメソッドに引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-105">In a method signature and in a method call, to pass an argument to a method by reference.</span></span> <span data-ttu-id="9c98c-106">詳細については、「[参照渡しで引数を渡す](#passing-an-argument-by-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-106">See [Passing an argument by reference](#passing-an-argument-by-reference) for more information.</span></span>

- <span data-ttu-id="9c98c-107">メソッド シグネチャで、参照渡しで呼び出し元に値を返します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-107">In a method signature, to return a value to the caller by reference.</span></span> <span data-ttu-id="9c98c-108">詳細については、「[参照戻り値](#reference-return-values)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-108">See [Reference return values](#reference-return-values) for more information.</span></span>

- <span data-ttu-id="9c98c-109">メンバーの本文で、参照戻り値が、呼び出し元によって変更される参照としてローカルに格納されることを示します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-109">In a member body, to indicate that a reference return value is stored locally as a reference that the caller intends to modify.</span></span> <span data-ttu-id="9c98c-110">詳細については、「[ref ローカル変数](#ref-locals)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-110">See [Ref locals](#ref-locals) for more information.</span></span>

## <a name="passing-an-argument-by-reference"></a><span data-ttu-id="9c98c-111">参照渡しで引数を渡す</span><span class="sxs-lookup"><span data-stu-id="9c98c-111">Passing an argument by reference</span></span>

<span data-ttu-id="9c98c-112">メソッドのパラメーター リストで使用した場合、`ref` キーワードは、引数を値ではなく、参照によって渡すことを示します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-112">When used in a method's parameter list, the `ref` keyword indicates that an argument is passed by reference, not by value.</span></span> <span data-ttu-id="9c98c-113">参照渡しで渡すことにより、呼び出されたメソッドの引数に対する変更が、呼び出し元のメソッドに反映されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-113">The effect of passing by reference is that any change to the argument in the called method is reflected in the calling method.</span></span> <span data-ttu-id="9c98c-114">たとえば、呼び出し元がローカル変数の式、または配列要素のアクセス式を渡し、呼び出されたメソッドが ref パラメーターが参照するオブジェクトを置き換える場合、メソッドが戻ったときに呼び出し元のローカル変数または配列要素は新しいオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-114">For example, if the caller passes a local variable expression or an array element access expression, and the called method replaces the object to which the ref parameter refers, then the caller’s local variable or the array element now refers to the new object when the method returns.</span></span>

> [!NOTE]
>  <span data-ttu-id="9c98c-115">参照渡しの概念と参照型の概念を混同しないでください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-115">Do not confuse the concept of passing by reference with the concept of reference types.</span></span> <span data-ttu-id="9c98c-116">2 つの概念は同じではありません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-116">The two concepts are not the same.</span></span> <span data-ttu-id="9c98c-117">メソッドのパラメーターは、値型か参照型かどうかに関係なく、`ref` によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-117">A method parameter can be modified by `ref` regardless of whether it is a value type or a reference type.</span></span> <span data-ttu-id="9c98c-118">参照渡しで渡される場合、値型はボックス化されません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-118">There is no boxing of a value type when it is passed by reference.</span></span>  

<span data-ttu-id="9c98c-119">`ref` パラメーターを使用するには、メソッド定義と呼び出し元のメソッドの両方が、次の例に示すように `ref` キーワードを明示的に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c98c-119">To use a `ref` parameter, both the method definition and the calling method must explicitly use the `ref` keyword, as shown in the following example.</span></span>  

[!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

<span data-ttu-id="9c98c-120">`ref` パラメーターに渡す引数は、渡す前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c98c-120">An argument that is passed to a `ref` parameter must be initialized before it is passed.</span></span> <span data-ttu-id="9c98c-121">これは、引数を渡す前に明示的に初期化する必要がない [out](out.md) パラメーターとは異なります。</span><span class="sxs-lookup"><span data-stu-id="9c98c-121">This differs from [out](out.md) parameters, whose arguments do not have to be explicitly initialized before they are passed.</span></span>

<span data-ttu-id="9c98c-122">クラスのメンバーは、`ref` と `out` だけが異なるシグネチャを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-122">Members of a class can't have signatures that differ only by `ref` and `out`.</span></span> <span data-ttu-id="9c98c-123">1 つの型の 2 つのメンバー間の違いが、1 つには `ref` パラメーターがあり、もう 1 つには `out` パラメーターがあることのみの場合は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-123">A compiler error occurs if the only difference between two members of a type is that one of them has a `ref` parameter and the other has an `out` parameter.</span></span> <span data-ttu-id="9c98c-124">たとえば、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-124">The following code, for example, doesn't compile.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 <span data-ttu-id="9c98c-125">ただし、次の例に示すように、1 つのメソッドに `ref` または `out` パラメーターがあり、もう 1 つのメソッドに値パラメーターがある場合、メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-125">However, methods can be overloaded when one method has a `ref` or `out` parameter and the other has a value parameter, as shown in the following example.</span></span>
  
 [!code-csharp[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 <span data-ttu-id="9c98c-126">非表示やオーバーライドなど、シグネチャの一致が必要な他の状況では、`ref` と `out` はシグネチャの一部であり互いに一致しません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-126">In other situations that require signature matching, such as hiding or overriding, `ref` and `out` are part of the signature and don't match each other.</span></span>  
  
 <span data-ttu-id="9c98c-127">プロパティは変数ではありません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-127">Properties are not variables.</span></span> <span data-ttu-id="9c98c-128">プロパティはメソッドであり、`ref` パラメーターに渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-128">They are methods, and cannot be passed to `ref` parameters.</span></span>  
  
 <span data-ttu-id="9c98c-129">配列を渡す方法については、「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-129">For information about how to pass arrays, see [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="9c98c-130">次の種類のメソッドには、`ref` キーワードと `out` キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c98c-130">You can't use the `ref` and `out` keywords for the following kinds of methods:</span></span>  
  
-   <span data-ttu-id="9c98c-131">[async](../../../csharp/language-reference/keywords/async.md) 修飾子を使用して定義した Async メソッド。</span><span class="sxs-lookup"><span data-stu-id="9c98c-131">Async methods, which you define by using the [async](../../../csharp/language-reference/keywords/async.md) modifier.</span></span>  
  
-   <span data-ttu-id="9c98c-132">[yield return](../../../csharp/language-reference/keywords/yield.md) または `yield break` ステートメントを含む Iterator メソッド。</span><span class="sxs-lookup"><span data-stu-id="9c98c-132">Iterator methods, which include a [yield return](../../../csharp/language-reference/keywords/yield.md) or `yield break` statement.</span></span>  
  
## <a name="passing-an-argument-by-reference-an-example"></a><span data-ttu-id="9c98c-133">参照渡しで引数を渡す: 使用例</span><span class="sxs-lookup"><span data-stu-id="9c98c-133">Passing an argument by reference: An example</span></span>

<span data-ttu-id="9c98c-134">前の例は、参照によって値型を渡す例でした。</span><span class="sxs-lookup"><span data-stu-id="9c98c-134">The previous examples pass value types by reference.</span></span> <span data-ttu-id="9c98c-135">`ref` キーワードを使用して、参照渡しで参照型を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-135">You can also use the `ref` keyword to pass reference types by reference.</span></span> <span data-ttu-id="9c98c-136">参照型を参照渡しで渡すと、呼び出されたメソッドは、参照パラメーターが呼び出し元で参照するオブジェクトに置換できます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-136">Passing a reference type by reference enables the called method to replace the object to which the reference parameter refers in the caller.</span></span> <span data-ttu-id="9c98c-137">オブジェクトの格納場所は、参照パラメーターの値としてメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-137">The storage location of the object is passed to the method as the value of the reference parameter.</span></span> <span data-ttu-id="9c98c-138">パラメーターの格納場所の値を変更する場合は (新しいオブジェクトをポイント)、呼び出し元が参照する格納場所を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-138">If you change the value in the storage location of the parameter (to point to a new object), you also change the storage location to which the caller refers.</span></span> <span data-ttu-id="9c98c-139">次の例では、参照型のインスタンスを `ref` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-139">The following example passes an instance of a reference type as a `ref` parameter.</span></span>   
  
 [!code-csharp[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

<span data-ttu-id="9c98c-140">参照型を値渡しまたは参照渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-140">For more information about how to pass reference types by value and by reference, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).</span></span>
  
## <a name="reference-return-values"></a><span data-ttu-id="9c98c-141">参照戻り値</span><span class="sxs-lookup"><span data-stu-id="9c98c-141">Reference return values</span></span>

<span data-ttu-id="9c98c-142">参照戻り値 (または ref 戻り値) は、メソッドから呼び出し元に参照渡しで返される値です。</span><span class="sxs-lookup"><span data-stu-id="9c98c-142">Reference return values (or ref returns) are values that a method returns by reference to the caller.</span></span> <span data-ttu-id="9c98c-143">つまり、呼び出し元はメソッドによって返される値を変更することができ、メソッドを格納するオブジェクトの状態にその変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-143">That is, the caller can modify the value returned by a method, and that change is reflected in the state of the object that contains the method.</span></span> 

<span data-ttu-id="9c98c-144">参照戻り値は `ref` キーワードを使用して以下に定義されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-144">A reference return value is defined by using the `ref` keyword:</span></span>

- <span data-ttu-id="9c98c-145">メソッド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="9c98c-145">In the method signature.</span></span> <span data-ttu-id="9c98c-146">たとえば、次のメソッド シグネチャは、`GetCurrentPrice` メソッドが参照渡しで <xref:System.Decimal> 値を返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="9c98c-146">For example, the following method signature inidicates that the `GetCurrentPrice` method returns a <xref:System.Decimal> value by reference.</span></span>

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- <span data-ttu-id="9c98c-147">メソッドの `return` ステートメントで返される変数と `return` トークンの間。</span><span class="sxs-lookup"><span data-stu-id="9c98c-147">Between the `return` token and the variable returned in a `return` statement in the method.</span></span> <span data-ttu-id="9c98c-148">例:</span><span class="sxs-lookup"><span data-stu-id="9c98c-148">For example:</span></span>
 
   ```csharp
   return ref DecimalArray[0];
   ``` 

<span data-ttu-id="9c98c-149">呼び出し元がオブジェクトの状態を変更するには、[ref ローカル変数](#ref-locals)として明示的に定義した変数に参照戻り値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c98c-149">In order for the caller to modify the object's state, the reference return value must be stored to a variable that is explicitly defined as a [ref local](#ref-locals).</span></span> 

<span data-ttu-id="9c98c-150">例については、「[ref 戻り値と ref ローカル変数](#a-ref-returns-and-ref-locals-example)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-150">For an example, see [A ref returns and ref locals example](#a-ref-returns-and-ref-locals-example)</span></span>

## <a name="ref-locals"></a><span data-ttu-id="9c98c-151">ref ローカル変数</span><span class="sxs-lookup"><span data-stu-id="9c98c-151">Ref locals</span></span>

<span data-ttu-id="9c98c-152">ref ローカル変数は、`return ref` を使用して返された値を参照するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-152">A ref local variable is used to refer to values returned using `return ref`.</span></span>  <span data-ttu-id="9c98c-153">ref ローカル変数は、初期化して ref 戻り値に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c98c-153">A ref local variable must be initialized and assigned to a ref return value.</span></span> <span data-ttu-id="9c98c-154">ref ローカル変数の値に変更を加えると、参照渡しの値を返すメソッドのオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-154">Any modifications to the value of the ref local are reflected in the state of the object whose method returned the value by reference.</span></span>

<span data-ttu-id="9c98c-155">ref ローカル変数を定義するには、変数宣言の前と、参照渡しで値を返すメソッドの呼び出しの直前に、`ref` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c98c-155">You define a ref local by using the `ref` keyword before the variable declaration, as well as immediately before the call to the method that returns the value by reference.</span></span> 

<span data-ttu-id="9c98c-156">たとえば、次のステートメントは、`GetEstimatedValue` という名前のメソッドによって返される ref ローカル変数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="9c98c-156">For example, the following statement defines a ref local value that is returned by a method named `GetEstimatedValue`:</span></span>

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

<span data-ttu-id="9c98c-157">なお、`ref` キーワードは両方の位置で使用する必要があります。そうしないと、コンパイラ エラー CS8172 "値を使用して参照渡し変数を初期化することはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-157">Note that the `ref` keyword must be used in both places, or the compiler generates error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="a-ref-returns-and-ref-locals-example"></a><span data-ttu-id="9c98c-158">ref 戻り値と ref ローカル変数の使用例</span><span class="sxs-lookup"><span data-stu-id="9c98c-158">A ref returns and ref locals example</span></span>

<span data-ttu-id="9c98c-159">次の例は、`Title` と `Author` という 2 つの <xref:System.String> フィールドを持つ `Book` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="9c98c-159">The following example defines a `Book` class that has two <xref:System.String> fields, `Title` and `Author`.</span></span> <span data-ttu-id="9c98c-160">また、`Book` オブジェクトのプライベート配列を含む `BookCollection` クラスも定義しています。</span><span class="sxs-lookup"><span data-stu-id="9c98c-160">It also defines a `BookCollection` class that includes a private array of `Book` objects.</span></span> <span data-ttu-id="9c98c-161">個々のブック オブジェクトは、`GetBookByTitle` メソッドを呼び出すことによって参照渡しで返されます。</span><span class="sxs-lookup"><span data-stu-id="9c98c-161">Individual book objects are returned by reference by calling its `GetBookByTitle` method.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

<span data-ttu-id="9c98c-162">呼び出し元が `GetBookByTitle` によって返される値を ref ローカル変数として格納する場合、呼び出し元が戻り値に加えた変更が `BookCollection` オブジェクトに反映されます。次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c98c-162">When the caller stores the value returned by the `GetBookByTitle` method as a ref local, changes that the caller makes to the return value are reflected in the `BookCollection` object, as the following example shows.</span></span>

[!code-csharp[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a><span data-ttu-id="9c98c-163">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9c98c-163">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9c98c-164">参照</span><span class="sxs-lookup"><span data-stu-id="9c98c-164">See Also</span></span>  
 [<span data-ttu-id="9c98c-165">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9c98c-165">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9c98c-166">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9c98c-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9c98c-167">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="9c98c-167">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="9c98c-168">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c98c-168">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)  
 [<span data-ttu-id="9c98c-169">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="9c98c-169">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
