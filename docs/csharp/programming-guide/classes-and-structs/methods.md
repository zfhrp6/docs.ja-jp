---
title: "メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cf320a26e697943416cd8f1065f1b4ca4afeac07
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="c13b8-102">メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c13b8-102">Methods (C# Programming Guide)</span></span>
<span data-ttu-id="c13b8-103">メソッドは、一連のステートメントが含まれているコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="c13b8-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="c13b8-104">必要なメソッド引数を指定してプログラムからメソッドを呼び出すと、メソッド内のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="c13b8-105">C# では、実行されるすべての命令がメソッドのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="c13b8-106">Main メソッドは、すべての C# アプリケーションのエントリ ポイントです。プログラムが開始されると、このメソッドが共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-106">The Main method is the entry point for every C# application and it is called by the common language runtime (CLR) when the program is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c13b8-107">このトピックでは、名前付きメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-107">This topic discusses named methods.</span></span> <span data-ttu-id="c13b8-108">匿名関数については、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-108">For information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="method-signatures"></a><span data-ttu-id="c13b8-109">メソッド シグネチャ</span><span class="sxs-lookup"><span data-stu-id="c13b8-109">Method Signatures</span></span>  
 <span data-ttu-id="c13b8-110">メソッドは、 [クラス](../../../csharp/language-reference/keywords/class.md) または [構造体](../../../csharp/language-reference/keywords/struct.md) で、アクセス レベル ( `public` や `private`など)、オプションの修飾子 ( `abstract` や `sealed`など)、戻り値、メソッドの名前、およびメソッド パラメーターを指定して宣言します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-110">Methods are declared in a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="c13b8-111">これらのまとまりがメソッドのシグネチャとなります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-111">These parts together are the signature of the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c13b8-112">メソッドのオーバーロードを可能にするために、メソッドの戻り値の型はメソッドのシグネチャには含まれません。</span><span class="sxs-lookup"><span data-stu-id="c13b8-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="c13b8-113">ただし、デリゲートとそれが指すメソッドの互換性を決定する場合には、メソッドのシグネチャの一部となります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>  
  
 <span data-ttu-id="c13b8-114">メソッド パラメーターはかっこで囲み、各パラメーターをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="c13b8-115">かっこ内を空にすると、メソッドでパラメーターが不要なことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="c13b8-116">次に 3 つのメソッドを含むクラスの例を示します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-116">This class contains three methods:</span></span>  
  
 <span data-ttu-id="c13b8-117">[!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-117">[!code-cs[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]</span></span>  
  
## <a name="method-access"></a><span data-ttu-id="c13b8-118">メソッド アクセス</span><span class="sxs-lookup"><span data-stu-id="c13b8-118">Method Access</span></span>  
 <span data-ttu-id="c13b8-119">オブジェクトでメソッドを呼び出すのは、フィールドにアクセスするのと似ています。</span><span class="sxs-lookup"><span data-stu-id="c13b8-119">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="c13b8-120">オブジェクト名の後に、ピリオド、メソッド名、かっこを追加します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-120">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="c13b8-121">引数はかっこの中に記述し、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-121">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="c13b8-122">`Motorcycle` クラスのメソッドの呼び出し例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-122">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>  
  
 <span data-ttu-id="c13b8-123">[!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-123">[!code-cs[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]</span></span>  
  
## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="c13b8-124">メソッド パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="c13b8-124">Method Parameters vs. Arguments</span></span>  
 <span data-ttu-id="c13b8-125">メソッド定義には、必要なパラメーターの名前と型を指定します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-125">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="c13b8-126">呼び出し元のコードからメソッドを呼び出すときに、各パラメーターに引数と呼ばれる具体的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-126">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="c13b8-127">引数にはパラメーター型との互換性が必要ですが、呼び出し元のコードで引数名を使用する場合、引数名がメソッドで定義されるパラメーター名と同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c13b8-127">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code does not have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="c13b8-128">例:</span><span class="sxs-lookup"><span data-stu-id="c13b8-128">For example:</span></span>  
  
 <span data-ttu-id="c13b8-129">[!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-129">[!code-cs[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]</span></span>  
  
## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="c13b8-130">参照渡しと値渡し</span><span class="sxs-lookup"><span data-stu-id="c13b8-130">Passing by Reference vs. Passing by Value</span></span>  
 <span data-ttu-id="c13b8-131">既定では、値型がメソッドに渡されるときは、オブジェクト自体ではなく、そのコピーが渡されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-131">By default, when a value type is passed to a method, a copy is passed instead of the object itself.</span></span> <span data-ttu-id="c13b8-132">したがって、引数に加えた変更は、呼び出し元のメソッドにある元のコピーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="c13b8-132">Therefore, changes to the argument have no effect on the original copy in the calling method.</span></span> <span data-ttu-id="c13b8-133">ref キーワードを使用すると、値型を参照によって引き渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-133">You can pass a value-type by reference by using the ref keyword.</span></span> <span data-ttu-id="c13b8-134">詳細については、「[値型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-134">For more information, see [Passing Value-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md).</span></span> <span data-ttu-id="c13b8-135">組み込みの値型の一覧については、「[値型の一覧表](../../../csharp/language-reference/keywords/value-types-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-135">For a list of built-in value types, see [Value Types Table](../../../csharp/language-reference/keywords/value-types-table.md).</span></span>  
  
 <span data-ttu-id="c13b8-136">参照型のオブジェクトがメソッドに渡されると、オブジェクトへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-136">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="c13b8-137">つまり、メソッドは、オブジェクト自体ではなく、オブジェクトの場所を示す引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-137">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="c13b8-138">この参照を使用してオブジェクトのメンバーを変更した場合は、オブジェクトを値で渡しても、呼び出し元のメソッドの引数に変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-138">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>  
  
 <span data-ttu-id="c13b8-139">`class` キーワードを使用して参照型を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-139">You create a reference type by using the `class` keyword, as the following example shows.</span></span>  
  
 <span data-ttu-id="c13b8-140">[!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-140">[!code-cs[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-141">この型に基づくオブジェクトをメソッドに渡す場合は、オブジェクトへの参照が渡されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-141">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="c13b8-142">次の例では、 `SampleRefType` 型のオブジェクトをメソッド `ModifyObject`に渡します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-142">The following example passes an object of type `SampleRefType` to method `ModifyObject`.</span></span>  
  
 <span data-ttu-id="c13b8-143">[!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-143">[!code-cs[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-144">この例は、基本的に前の例と同様に、引数を値でメソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="c13b8-144">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="c13b8-145">しかし、参照型を使用しているため、結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-145">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="c13b8-146">`ModifyObject` のパラメーター `value` の `obj`フィールドで行われた変更によって、 `value` メソッドの引数 `rt`の `TestRefType` フィールドも変更されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-146">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="c13b8-147">`TestRefType` メソッドは出力として 33 を表示します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-147">The `TestRefType` method displays 33 as the output.</span></span>  
  
 <span data-ttu-id="c13b8-148">参照型を参照渡しまたは値渡しで渡す方法の詳細については、「[参照型パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)」と「[参照型](../../../csharp/language-reference/keywords/reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-148">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) and [Reference Types](../../../csharp/language-reference/keywords/reference-types.md).</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="c13b8-149">戻り値</span><span class="sxs-lookup"><span data-stu-id="c13b8-149">Return Values</span></span>  
<span data-ttu-id="c13b8-150">メソッドは、呼び出し元に値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-150">Methods can return a value to the caller.</span></span> <span data-ttu-id="c13b8-151">戻り値の型 (メソッド名の前に記述されている型) が `void`でない場合、メソッドは、 `return` キーワードを使用して値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-151">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="c13b8-152">`return` キーワードに続いて戻り値の型に一致する値が記述されたステートメントは、その値をメソッドの呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-152">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span> 

<span data-ttu-id="c13b8-153">値を呼び出し元に返す方法には、値によって返す方法と、C# 7 以降の[参照](ref-returns.md)によって返す方法があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-153">The value can be returned to the caller by value or, starting with C# 7, [by reference](ref-returns.md).</span></span> <span data-ttu-id="c13b8-154">値が参照によって呼び出し元に返されるのは、`ref` キーワードがメソッド シグネチャで使用されていて、そのキーワードが各 `return` キーワードの後に続いている場合です。</span><span class="sxs-lookup"><span data-stu-id="c13b8-154">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="c13b8-155">たとえば、次のメソッド シグネチャと return ステートメントは、メソッドが変数名 `estDistance` を参照によって呼び出し元に返すことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c13b8-155">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

<span data-ttu-id="c13b8-156">また、 `return` キーワードは、メソッドの実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-156">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="c13b8-157">戻り値の型が `void`の場合、値を持たない `return` ステートメントは、メソッドの実行を中止するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-157">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="c13b8-158">`return` キーワードを使用しない場合、メソッドは、コード ブロックの最後に到達したときに実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-158">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="c13b8-159">戻り値の型が void 以外のメソッドで値を返すには、 `return` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-159">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="c13b8-160">たとえば、次の 2 つのメソッドは、 `return` キーワードを使用して整数を返します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-160">For example, these two methods use the `return` keyword to return integers:</span></span>  
  
 <span data-ttu-id="c13b8-161">[!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-161">[!code-cs[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-162">メソッドから返された値を使用する場合、呼び出し元のメソッド内で同じ型の値を使用している場所では、メソッド呼び出し自体を値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-162">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="c13b8-163">戻り値は、変数に代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-163">You can also assign the return value to a variable.</span></span> <span data-ttu-id="c13b8-164">たとえば、次の 2 つのコードでは、同様の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-164">For example, the following two code examples accomplish the same goal:</span></span>  
  
 <span data-ttu-id="c13b8-165">[!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-165">[!code-cs[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-166">[!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-166">[!code-cs[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-167">この場合、ローカル変数 `result`を使用して値を格納する手順はオプションです。</span><span class="sxs-lookup"><span data-stu-id="c13b8-167">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="c13b8-168">このローカル変数によってコードの読みやすさが向上することがあります。また、引数の元の値をメソッドのスコープ全体で保持する場合に必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-168">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>  

<span data-ttu-id="c13b8-169">メソッドから参照によって返された値を使用する場合、値を変更するには、[ref ローカル](ref-returns.md#ref-locals)変数を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-169">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="c13b8-170">たとえば、`Planet.GetEstimatedDistance` メソッドが <xref:System.Double> の値を参照によって返す場合は、次のようなコードを使用して、その値を ref ローカル変数として定義できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-170">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant 
```

<span data-ttu-id="c13b8-171">呼び出し元の関数から、配列の内容を変更するメソッド `M` に配列が渡された場合、`M` から多次元配列を返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c13b8-171">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="c13b8-172">値の適切なスタイルまたは機能フローのために `M` から結果の配列を返すことはできますが、必須ではありません。変更された配列を返す必要がないのは、C# ではすべての参照型が値で渡され、配列参照の値がその配列へのポインターになるためです。</span><span class="sxs-lookup"><span data-stu-id="c13b8-172">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="c13b8-173">メソッド `M` では、次の例に示すように、配列の内容に対する変更は、配列への参照を含むコードによって監視できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-173">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example.</span></span>  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 <span data-ttu-id="c13b8-174">詳細については、「 [return](../../../csharp/language-reference/keywords/return.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-174">For more information, see [return](../../../csharp/language-reference/keywords/return.md).</span></span>  
  
## <a name="async-methods"></a><span data-ttu-id="c13b8-175">非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="c13b8-175">Async Methods</span></span>  
 <span data-ttu-id="c13b8-176">非同期機能を使用することによって、明示的なコールバックを使用せずに、または複数のメソッドやラムダ式にわたって手動でコードを分割することなく、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-176">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span> 
  
 <span data-ttu-id="c13b8-177">メソッドに [async](../../../csharp/language-reference/keywords/async.md) 修飾子を付けると、そのメソッドで [await](../../../csharp/language-reference/keywords/await.md) 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-177">If you mark a method with the [async](../../../csharp/language-reference/keywords/async.md) modifier, you can use the [await](../../../csharp/language-reference/keywords/await.md) operator in the method.</span></span> <span data-ttu-id="c13b8-178">コントロールが非同期メソッドの await 式に到達すると、コントロールは呼び出し元に戻り、待機中のタスクが完了するまでメソッドの進行状況は中断されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-178">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="c13b8-179">タスクが完了すると、メソッドで実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-179">When the task is complete, execution can resume in the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c13b8-180">非同期メソッドは、まだ完了していない待機中の最初のオブジェクトに達するか、または非同期メソッドの最後に達すると、呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-180">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>  
  
 <span data-ttu-id="c13b8-181">非同期メソッドの戻り値の型としては、 <xref:System.Threading.Tasks.Task%601>、 <xref:System.Threading.Tasks.Task>、または void を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-181">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="c13b8-182">戻り値の型 void は主として、void の戻り値の型が必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-182">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="c13b8-183">void を返す非同期メソッドは待機できません。void を返すメソッドの呼び出し元は、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="c13b8-183">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="c13b8-184">次の例で、 `DelayAsync` は戻り値の型が <xref:System.Threading.Tasks.Task%601>である非同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c13b8-184">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c13b8-185">`DelayAsync` には、整数を返す `return` ステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-185">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="c13b8-186">そのため、メソッド宣言 `DelayAsync` では、戻り値の型を `Task<int>`とする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-186">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="c13b8-187">戻り値の型が `Task<int>`であるため、ステートメント `await` に示すように、 `DoSomethingAsync` 内の `int result = await delayTask`式を評価すると整数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-187">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>  
  
 <span data-ttu-id="c13b8-188">`startButton_Click` メソッドは、戻り値の型が void の非同期メソッドの例です。</span><span class="sxs-lookup"><span data-stu-id="c13b8-188">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="c13b8-189">`DoSomethingAsync` が非同期メソッドであるため、 `DoSomethingAsync` を呼び出すタスクは、ステートメント `await DoSomethingAsync();`に示すように待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-189">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="c13b8-190">`startButton_Click` メソッドでは `async` 式が使用されているため、 `await` 修飾子を使用して定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-190">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>  
  
 <span data-ttu-id="c13b8-191">[!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="c13b8-191">[!code-cs[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]</span></span>  
  
 <span data-ttu-id="c13b8-192">非同期メソッドで [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターを宣言することはできませんが、これらのパラメーターが含まれたメソッドを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-192">An async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, but it can call methods that have such parameters.</span></span>  
  
 <span data-ttu-id="c13b8-193">非同期メソッドの詳細については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」、「[非同期プログラムにおける制御フロー](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)」、「[非同期の戻り値の型](../../../csharp/programming-guide/concepts/async/async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-193">For more information about async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="c13b8-194">式の本文の定義</span><span class="sxs-lookup"><span data-stu-id="c13b8-194">Expression Body Definitions</span></span>  
 <span data-ttu-id="c13b8-195">メソッドの定義としては、式の結果を即座に返すか、またはメソッドの本文として 1 つのステートメントを含むものが一般的です。</span><span class="sxs-lookup"><span data-stu-id="c13b8-195">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span>  <span data-ttu-id="c13b8-196">`=>`を使用してこのようなメソッドを定義するための構文ショートカットがあります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-196">There is a syntax shortcut for defining such methods using `=>`:</span></span>  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 <span data-ttu-id="c13b8-197">メソッドが `void` を返すか、非同期メソッドである場合は、メソッドの本文を (ラムダの場合と同様に) ステートメント式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c13b8-197">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span>  <span data-ttu-id="c13b8-198">プロパティとインデクサーは読み取り専用にする必要があるため、 `get` アクセサー キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-198">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>  
  
## <a name="iterators"></a><span data-ttu-id="c13b8-199">反復子</span><span class="sxs-lookup"><span data-stu-id="c13b8-199">Iterators</span></span>  
 <span data-ttu-id="c13b8-200">反復子は、リストや配列など、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-200">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="c13b8-201">反復子は、 [yield return](../../../csharp/language-reference/keywords/yield.md) ステートメントを使用して、各要素を 1 回に1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-201">An iterator uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="c13b8-202">[yield return](../../../csharp/language-reference/keywords/yield.md) ステートメントに達すると、コードの現在の場所が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-202">When a [yield return](../../../csharp/language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="c13b8-203">反復子が次回呼び出されたとき、この場所から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-203">Execution is restarted from that location when the iterator is called the next time.</span></span>  
  
 <span data-ttu-id="c13b8-204">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用して、クライアント コードから反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c13b8-204">You call an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
 <span data-ttu-id="c13b8-205">反復子の戻り値の型には、 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601>を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c13b8-205">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="c13b8-206">詳細については、「 [反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c13b8-206">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c13b8-207">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c13b8-207">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c13b8-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="c13b8-208">See Also</span></span>  
 <span data-ttu-id="c13b8-209">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-209">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c13b8-210">[クラスと構造体](index.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-210">[Classes and Structs](index.md) </span></span>  
 <span data-ttu-id="c13b8-211">[アクセス修飾子](access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-211">[Access Modifiers](access-modifiers.md) </span></span>  
 <span data-ttu-id="c13b8-212">[静的クラスと静的クラス メンバー](static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-212">[Static Classes and Static Class Members](static-classes-and-static-class-members.md) </span></span>  
 <span data-ttu-id="c13b8-213">[継承](inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-213">[Inheritance](inheritance.md) </span></span>  
 <span data-ttu-id="c13b8-214">[抽象クラスとシール クラス、およびクラス メンバー](abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-214">[Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="c13b8-215">[params](../../../csharp/language-reference/keywords/params.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-215">[params](../../../csharp/language-reference/keywords/params.md) </span></span>  
 <span data-ttu-id="c13b8-216">[return](../../../csharp/language-reference/keywords/return.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-216">[return](../../../csharp/language-reference/keywords/return.md) </span></span>  
 <span data-ttu-id="c13b8-217">[out](../../../csharp/language-reference/keywords/out.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-217">[out](../../../csharp/language-reference/keywords/out.md) </span></span>  
 <span data-ttu-id="c13b8-218">[ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="c13b8-218">[ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
 [<span data-ttu-id="c13b8-219">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="c13b8-219">Passing Parameters</span></span>](passing-parameters.md)

