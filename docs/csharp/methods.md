---
title: メソッド - C# ガイド
description: メソッド、メソッド パラメーター、メソッド戻り値の概要
author: rpetrusha
ms.author: ronpet
ms.date: 10/26/2016
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 6a99ccc0157b044eb1a9ed7189de94ca69225d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="methods"></a><span data-ttu-id="deb98-103">メソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-103">Methods</span></span> #

<span data-ttu-id="deb98-104">メソッドは、一連のステートメントが含まれているコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="deb98-104">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="deb98-105">必要なメソッド引数を指定してプログラムからメソッドを呼び出すと、メソッド内のステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-105">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="deb98-106">C# では、実行されるすべての命令がメソッドのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-106">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="deb98-107">`Main` メソッドは、すべての C# アプリケーションのエントリ ポイントです。プログラムが開始されると、このメソッドが共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-107">The `Main` method is the entry point for every C# application and it is called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="deb98-108">このトピックでは、名前付きメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="deb98-108">This topic discusses named methods.</span></span> <span data-ttu-id="deb98-109">匿名関数については、「[匿名関数](programming-guide/statements-expressions-operators/anonymous-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-109">For information about anonymous functions, see [Anonymous Functions](programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>

<span data-ttu-id="deb98-110">このトピックは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="deb98-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="deb98-111">メソッド シグネチャ</span><span class="sxs-lookup"><span data-stu-id="deb98-111">Method signatures</span></span>](#signatures)
- [<span data-ttu-id="deb98-112">メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="deb98-112">Method invocation</span></span>](#invocation)
- [<span data-ttu-id="deb98-113">継承されたメソッドとオーバーライドされたメソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-113">Inherited and overridden methods</span></span>](#inherited)
- [<span data-ttu-id="deb98-114">パラメーターを渡す</span><span class="sxs-lookup"><span data-stu-id="deb98-114">Passing parameters</span></span>](#passing)
  - [<span data-ttu-id="deb98-115">パラメーターを値で渡す</span><span class="sxs-lookup"><span data-stu-id="deb98-115">Passing parameters by value</span></span>](#byval)
  - [<span data-ttu-id="deb98-116">パラメーターを参照で渡す</span><span class="sxs-lookup"><span data-stu-id="deb98-116">Passing parameters by reference</span></span>](#byref)
  - [<span data-ttu-id="deb98-117">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="deb98-117">Parameter arrays</span></span>](#paramarray)
- [<span data-ttu-id="deb98-118">省略可能なパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="deb98-118">Optional parameters and arguments</span></span>](#optional)
- [<span data-ttu-id="deb98-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="deb98-119">Return values</span></span>](#return)
- [<span data-ttu-id="deb98-120">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-120">Extension methods</span></span>](#extension)
- [<span data-ttu-id="deb98-121">非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-121">Async Methods</span></span>](#async)
- [<span data-ttu-id="deb98-122">式形式のメンバー</span><span class="sxs-lookup"><span data-stu-id="deb98-122">Expression-bodied members</span></span>](#expr)
- [<span data-ttu-id="deb98-123">反復子</span><span class="sxs-lookup"><span data-stu-id="deb98-123">Iterators</span></span>](#iterators)

<a name="signatures"></a>
## <a name="method-signatures"></a><span data-ttu-id="deb98-124">メソッド シグネチャ</span><span class="sxs-lookup"><span data-stu-id="deb98-124">Method signatures</span></span> ##

<span data-ttu-id="deb98-125">メソッドは次の項目を指定することで `class` または `struct` で宣言されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-125">Methods are declared in a `class` or `struct` by specifying:</span></span>

- <span data-ttu-id="deb98-126">`public` や `private` など、任意のアクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="deb98-126">An optional access level, such as `public` or `private`.</span></span> <span data-ttu-id="deb98-127">既定値は、`private` です。</span><span class="sxs-lookup"><span data-stu-id="deb98-127">The default is `private`.</span></span>
- <span data-ttu-id="deb98-128">`abstract` や `sealed` など、任意の修飾子。</span><span class="sxs-lookup"><span data-stu-id="deb98-128">Optional modifiers such as `abstract` or `sealed`.</span></span>
- <span data-ttu-id="deb98-129">メソッドに何も与えられていない場合、戻り値または `void`。</span><span class="sxs-lookup"><span data-stu-id="deb98-129">The return value, or `void` if the method has none.</span></span>
- <span data-ttu-id="deb98-130">メソッド名。</span><span class="sxs-lookup"><span data-stu-id="deb98-130">The method name.</span></span>
- <span data-ttu-id="deb98-131">メソッド パラメーター。</span><span class="sxs-lookup"><span data-stu-id="deb98-131">Any method parameters.</span></span> <span data-ttu-id="deb98-132">メソッド パラメーターはかっこで囲み、各パラメーターをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="deb98-132">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="deb98-133">かっこ内を空にすると、メソッドでパラメーターが不要なことを意味します。</span><span class="sxs-lookup"><span data-stu-id="deb98-133">Empty parentheses indicate that the method requires no parameters.</span></span>

<span data-ttu-id="deb98-134">これらのまとまりがメソッド シグネチャとなります。</span><span class="sxs-lookup"><span data-stu-id="deb98-134">These parts together form the method signature.</span></span>

> [!NOTE]
> <span data-ttu-id="deb98-135">メソッドのオーバーロードを可能にするために、メソッドの戻り値の型はメソッドのシグネチャには含まれません。</span><span class="sxs-lookup"><span data-stu-id="deb98-135">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="deb98-136">ただし、デリゲートとそれが指すメソッドの互換性を決定する場合には、メソッドのシグネチャの一部となります。</span><span class="sxs-lookup"><span data-stu-id="deb98-136">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="deb98-137">次の例では、5 つのメソッドを含む `Motorcycle` という名前のクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="deb98-137">The following example defines a class named `Motorcycle` that contains five methods:</span></span>

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

<span data-ttu-id="deb98-138">`Motorcycle` クラスにオーバーロードされたクラス `Drive` が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-138">Note that the `Motorcycle` class includes an overloaded method, `Drive`.</span></span> <span data-ttu-id="deb98-139">2 つのメソッドの名前が同じであり、パラメーターの種類で識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-139">Two methods have the same name, but must be differentiated by their parameter types.</span></span>

<a name="invocation"></a>
## <a name="method-invocation"></a><span data-ttu-id="deb98-140">メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="deb98-140">Method invocation</span></span> ##

<span data-ttu-id="deb98-141">メソッドは*インスタンス*または*静的*になります。</span><span class="sxs-lookup"><span data-stu-id="deb98-141">Methods can be either *instance* or *static*.</span></span> <span data-ttu-id="deb98-142">インスタンス メソッドを呼び出すには、オブジェクトをインスタンス化し、そのオブジェクトでメソッドを呼び出す必要があります。インスタンス メソッドはこのインスタンスとそのデータを操作します。</span><span class="sxs-lookup"><span data-stu-id="deb98-142">Invoking an instance method requires that you instantiate an object and call the method on that object; an instance method operates on that instance and its data.</span></span> <span data-ttu-id="deb98-143">メソッドが属する型の名前を参照して静的メソッドを呼び出します。静的メソッドはインスタンス データを操作しません。</span><span class="sxs-lookup"><span data-stu-id="deb98-143">You invoke a static method by referencing the name of the type to which the method belongs; static methods operate do not operate on instance data.</span></span> <span data-ttu-id="deb98-144">オブジェクト インスタンス経由で静的メソッドを呼び出そうとすると、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="deb98-144">Attempting to call a static method through an object instance generates a compiler error.</span></span>

<span data-ttu-id="deb98-145">メソッドを呼び出すことは、フィールドにアクセスするのと似ています。</span><span class="sxs-lookup"><span data-stu-id="deb98-145">Calling a method is like accessing a field.</span></span> <span data-ttu-id="deb98-146">オブジェクトの名前 (インスタンス メソッドを呼び出す場合) または型の名前 (`static` メソッドを呼び出す場合) の後ろに、期間、メソッドの名前、かっこを追加します。</span><span class="sxs-lookup"><span data-stu-id="deb98-146">After the object name (if you are calling an instance method) or the type name (if you are calling a `static` method), add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="deb98-147">引数はかっこの中に記述し、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="deb98-147">Arguments are listed within the parentheses, and are separated by commas.</span></span>

<span data-ttu-id="deb98-148">メソッド定義には、必要なパラメーターの名前と型を指定します。</span><span class="sxs-lookup"><span data-stu-id="deb98-148">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="deb98-149">呼び出し元からメソッドを呼び出すとき、各パラメーターに引数と呼ばれる具体的な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="deb98-149">When a caller invokes the method, it provides concrete values, called arguments, for each parameter.</span></span> <span data-ttu-id="deb98-150">引数にはパラメーター型との互換性が必要ですが、呼び出し元のコードで引数名を使用する場合、引数名がメソッドで定義されるパラメーター名と同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="deb98-150">The arguments must be compatible with the parameter type, but the argument name, if one is used in the calling code, does not have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="deb98-151">次の例では、`Square` メソッドに型が `int` で *i* という名前のパラメーターが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="deb98-151">In the following example, the `Square` method includes a single parameter of type `int` named *i*.</span></span> <span data-ttu-id="deb98-152">最初のメソッド呼び出しでは、型が `int` で *num* という名前の変数が `Square` メソッドに渡されます。2 つ目のメソッド呼び出しでは数値定数が、3 つ目のメソッド呼び出しでは式が渡されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-152">The first method call passes the `Square` method a variable of type `int` named *num*; the second, a numeric constant; and the third, an expression.</span></span>

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

<span data-ttu-id="deb98-153">メソッド呼び出しの最も一般的な形式では、位置引数が使用されます。これはメソッド パラメーターと同じ順序で引数を指定するものです。</span><span class="sxs-lookup"><span data-stu-id="deb98-153">The most common form of method invocation used positional arguments; it supplies arguments in the same order as method parameters.</span></span> <span data-ttu-id="deb98-154">そのため、`Motorcycle` クラスのメソッドは次の例のように呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-154">The methods of the `Motorcycle` class can therefore be called as in the following example.</span></span> <span data-ttu-id="deb98-155">たとえば、`Drive` メソッドの呼び出しには 2 つの引数が含まれます。この 2 つの引数は、メソッドの構文の 2 つのパラメーターに対応しています。</span><span class="sxs-lookup"><span data-stu-id="deb98-155">The call to the `Drive` method, for example, includes two arguments that correspond to the two parameters in the method's syntax.</span></span> <span data-ttu-id="deb98-156">1 つ目は `miles` パラメーターの値になります。2 つ目は `speed` パラメーターの値になります。</span><span class="sxs-lookup"><span data-stu-id="deb98-156">The first becomes the value of the `miles` parameter, the second the value of the `speed` parameter.</span></span>

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

<span data-ttu-id="deb98-157">メソッドを呼び出すとき、位置引数の代わりに*名前付き引数*を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="deb98-157">You can also used *named arguments* instead of positional arguments when invoking a method.</span></span> <span data-ttu-id="deb98-158">名前付き引数を使用するとき、パラメーター名に続けてコロン (":") と引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="deb98-158">When using named arguments, you specify the parameter name followed by a colon (":") and the argument.</span></span> <span data-ttu-id="deb98-159">必要なすべての引数が存在する限り、メソッドの引数の順序は問われません。</span><span class="sxs-lookup"><span data-stu-id="deb98-159">Arguments to the method can appear in any order, as long as all required arguments are present.</span></span> <span data-ttu-id="deb98-160">次の例では、名前付き引数を使用して `TestMotorcycle.Drive` メソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="deb98-160">The following example uses named arguments to invoke the `TestMotorcycle.Drive` method.</span></span> <span data-ttu-id="deb98-161">この例では、メソッドのパラメーター リストとは反対の順序で名前付き引数が渡されています。</span><span class="sxs-lookup"><span data-stu-id="deb98-161">In this example, the named arguments are passed in the opposite order from the method's parameter list.</span></span>

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

<span data-ttu-id="deb98-162">位置引数と名前付き引数の両方を利用してメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-162">You can invoke a method using both positional arguments and named arguments.</span></span> <span data-ttu-id="deb98-163">ただし、名前付き引数の後に位置指定引数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="deb98-163">However, a positional argument cannot follow a named argument.</span></span> <span data-ttu-id="deb98-164">次の例では、前の例にあった `TestMotorcycle.Drive` メソッドを呼び出していますが、位置引数が 1 つ、名前付き引数が 1 つ使用されています。</span><span class="sxs-lookup"><span data-stu-id="deb98-164">The following example invokes the `TestMotorcycle.Drive` method from the previous example using one positional argument and one named argument.</span></span>

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ##<a name="inherited-and-overridden-methods"></a><span data-ttu-id="deb98-165">継承されたメソッドとオーバーライドされたメソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-165">Inherited and overridden methods</span></span> ##

<span data-ttu-id="deb98-166">型に明示的に定義されるメンバーに加え、型は、その基底クラスに定義されているメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="deb98-166">In addition to the members that are explicitly defined in a type, a type inherits members defined in its base classes.</span></span> <span data-ttu-id="deb98-167">マネージ型という系統のすべての型は <xref:System.Object> クラスから直接的または間接的に継承するため、すべての型が、<xref:System.Object.Equals(System.Object)>、<xref:System.Object.GetType>、<xref:System.Object.ToString> など、そのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="deb98-167">Since all types in the managed type system inherit directly or indirectly from the <xref:System.Object> class, all types inherit its members, such as <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, and <xref:System.Object.ToString>.</span></span> <span data-ttu-id="deb98-168">次の例では、`Person` クラスを定義し、2 つの `Person` オブジェクトをインスタンス化し、`Person.Equals` メソッドを呼び出して 2 つのオブジェクトが等しいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="deb98-168">The following example defines a `Person` class, instantiates two `Person` objects, and calls the `Person.Equals` method to determine whether the two objects are equal.</span></span> <span data-ttu-id="deb98-169">ただし、`Equals` メソッドは `Person` クラスに定義されていません。<xref:System.Object> から継承されたものです。</span><span class="sxs-lookup"><span data-stu-id="deb98-169">The `Equals` method, however, is not defined in the `Person` class; it is inherited from <xref:System.Object>.</span></span>

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

<span data-ttu-id="deb98-170">型は継承されたメンバーをオーバーライドできます。`override` キーワードを使用し、オーバーライドされたメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="deb98-170">Types can override inherited members by using the `override` keyword and providing an implementation for the overridden method.</span></span> <span data-ttu-id="deb98-171">メソッド シグネチャは、オーバーライドされたメソッドのものと同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-171">The method signature must be the same as that of the overridden method.</span></span> <span data-ttu-id="deb98-172">次の例は前の例と似ていますが、<xref:System.Object.Equals(System.Object)> メソッドをオーバーライドしている点が異なります。</span><span class="sxs-lookup"><span data-stu-id="deb98-172">The following example is like the previous one, except that it overrides the <xref:System.Object.Equals(System.Object)> method.</span></span> <span data-ttu-id="deb98-173">(この 2 つのメソッドは一貫性のある結果を提供するため、<xref:System.Object.GetHashCode> メソッドもオーバーライドされます。)</span><span class="sxs-lookup"><span data-stu-id="deb98-173">(It also overrides the <xref:System.Object.GetHashCode> method, since the two methods are intended to provide consistent results.)</span></span>

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a><span data-ttu-id="deb98-174">パラメーターを渡す</span><span class="sxs-lookup"><span data-stu-id="deb98-174">Passing parameters</span></span> ##

<span data-ttu-id="deb98-175">C# の型は、*値型*と*参照型*のどちらかに区別されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-175">Types in C# are either *value types* or *reference types*.</span></span> <span data-ttu-id="deb98-176">組み込みの値型の一覧については、「[型と変数](./tour-of-csharp/types-and-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-176">For a list of built-in value types, see [Types and variables](./tour-of-csharp/types-and-variables.md).</span></span> <span data-ttu-id="deb98-177">既定では、値型と参照型の両方が値によりメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-177">By default, both value types and reference types are passed to a method by value.</span></span>

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a><span data-ttu-id="deb98-178">パラメーターを値で渡す</span><span class="sxs-lookup"><span data-stu-id="deb98-178">Passing parameters by value</span></span> ###

<span data-ttu-id="deb98-179">値型が値でメソッドに渡されるとき、オブジェクト自体の代わりにオブジェクトのコピーがメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-179">When a value type is passed to a method by value, a copy of the object instead of the object itself is passed to the method.</span></span> <span data-ttu-id="deb98-180">そのため、呼び出されたメソッドでオブジェクトに加えた変更は、コントロールが呼び出し元に戻ったとき、元のオブジェクトで反映されません。</span><span class="sxs-lookup"><span data-stu-id="deb98-180">Therefore, changes to the object in the called method have no effect on the original object when control returns to the caller.</span></span>

<span data-ttu-id="deb98-181">次の例では、値型を値でメソッドに渡します。呼び出されたメソッドが値型の値を変更しようとします。</span><span class="sxs-lookup"><span data-stu-id="deb98-181">The following example passes a value type to a method by value, and the called method attempts to change the value type's value.</span></span> <span data-ttu-id="deb98-182">型 `int` (値型) の変数を定義し、その値を 20 に初期化し、`ModifyValue` という名前のメソッドに値を渡します。このメソッドは変数の値を 30 に変更します。</span><span class="sxs-lookup"><span data-stu-id="deb98-182">It defines a variable of type `int`, which is a value type, initializes its value to 20, and passes it to a method named `ModifyValue` that changes the variable's value to 30.</span></span> <span data-ttu-id="deb98-183">しかしながら、メソッドが戻ると、変数の値は元のままです。</span><span class="sxs-lookup"><span data-stu-id="deb98-183">When the method returns, however, the variable's value remains unchanged.</span></span>

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

<span data-ttu-id="deb98-184">参照型のオブジェクトが値でメソッドに渡されると、オブジェクトへの参照が値で渡されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-184">When an object of a reference type is passed to a method by value, a reference to the object is passed by value.</span></span> <span data-ttu-id="deb98-185">つまり、メソッドは、オブジェクト自体ではなく、オブジェクトの場所を示す引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="deb98-185">That is, the method receives not the object itself, but an argument that indicates the location of the object.</span></span> <span data-ttu-id="deb98-186">この参照を使用してオブジェクトのメンバーを変更した場合、コントロールが呼び出し元のメソッドに戻ると、オブジェクトで変更が反映されています。</span><span class="sxs-lookup"><span data-stu-id="deb98-186">If you change a member of the object by using this reference, the change is reflected in the object when control returns to the calling method.</span></span> <span data-ttu-id="deb98-187">ただし、メソッドに渡されるオブジェクトを置換しても、コントロールが呼び出し元に戻ったとき、元のオブジェクトで反映されません。</span><span class="sxs-lookup"><span data-stu-id="deb98-187">However, replacing the object passed to the method has no effect on the original object when control returns to the caller.</span></span>

<span data-ttu-id="deb98-188">次の例では、`SampleRefType` という名前のクラス (参照型) を定義します。</span><span class="sxs-lookup"><span data-stu-id="deb98-188">The following example defines a class (which is a reference type) named `SampleRefType`.</span></span> <span data-ttu-id="deb98-189">`SampleRefType` オブジェクトをインスタンス化し、その `value` フィールドに 44 を割り当て、`ModifyObject` メソッドにオブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="deb98-189">It instantiates a `SampleRefType` object, assigns 44 to its `value` field, and passes the object to the `ModifyObject` method.</span></span> <span data-ttu-id="deb98-190">この例は、基本的に前の例と同様に、引数を値でメソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="deb98-190">This example does essentially the same thing as the previous example -- it passes an argument by value to a method.</span></span> <span data-ttu-id="deb98-191">ただし、参照型を使用しているため、結果は異なります。</span><span class="sxs-lookup"><span data-stu-id="deb98-191">But because a reference type is used, the result is different.</span></span> <span data-ttu-id="deb98-192">`ModifyObject` の `obj.value` フィールドを変更したことで、`Main` メソッドの引数 `rt` の `value` フィールドも 33 に変更されます。例の出力で確認できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-192">The modification that is made in `ModifyObject` to the `obj.value` field also changes the `value` field of the argument, `rt`, in the `Main` method to 33, as the output from the example shows.</span></span>

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a><span data-ttu-id="deb98-193">パラメーターの参照渡し</span><span class="sxs-lookup"><span data-stu-id="deb98-193">Passing parameters by reference</span></span> ###

<span data-ttu-id="deb98-194">メソッドの引数の値を変更し、コントロールが呼び出し元に戻ったときにその変更を反映させるには、参照でパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="deb98-194">You pass a parameter by reference when you want to change the value of an argument in a method and want to refect that change when control returns to the calling method.</span></span> <span data-ttu-id="deb98-195">パラメーターを参照で渡すには、[`ref`](language-reference/keywords/ref.md) または [`out`](language-reference/keywords/out-parameter-modifier.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="deb98-195">To pass a parameter by reference, you use the [`ref`](language-reference/keywords/ref.md) or [`out`](language-reference/keywords/out-parameter-modifier.md) keyword.</span></span> <span data-ttu-id="deb98-196">値を参照で渡すことで、コピーを回避することもできますが、[`in`](language-reference/keywords/in-parameter-modifier.md) キーワードを使用して変更を防ぐこともできます。</span><span class="sxs-lookup"><span data-stu-id="deb98-196">You can also pass a value by reference to avoid copying but still prevent modifications using the [`in`](language-reference/keywords/in-parameter-modifier.md) keyword.</span></span>

<span data-ttu-id="deb98-197">次の例は前の例とよく似ていますが、値が参照で `ModifyValue` メソッドに渡される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="deb98-197">The following example is identical to the previous one, except the value is passed by reference to the `ModifyValue` method.</span></span> <span data-ttu-id="deb98-198">パラメーターの値が `ModifyValue` メソッドで変更されると、コントロールが呼び出し元に戻ったとき、地の変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-198">When the value of the parameter is modified in the `ModifyValue` method, the change in value is reflected when control returns to the caller.</span></span>

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

<span data-ttu-id="deb98-199">参照型パラメーターを利用する典型的なパターンが変数の値の入れ替えです。</span><span class="sxs-lookup"><span data-stu-id="deb98-199">A common pattern that uses by ref parameters involves swapping the values of variables.</span></span> <span data-ttu-id="deb98-200">参照でメソッドに 2 つの変数を渡すと、メソッドがその中身を入れ替えます。</span><span class="sxs-lookup"><span data-stu-id="deb98-200">You pass two variables to a method by reference, and the method swaps their contents.</span></span> <span data-ttu-id="deb98-201">次の例では、整数値が入れ替えられます。</span><span class="sxs-lookup"><span data-stu-id="deb98-201">The following example swaps integer values.</span></span>

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

<span data-ttu-id="deb98-202">参照型パラメーターを渡すことで、個々の要素またはフィールドの値ではなく、参照自体の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-202">Passing a reference-type parameter allows you to change the value of the reference itself, rather than the value of its individual elements or fields.</span></span>

<a name="paramarray"></a>
### <a name="parameter-arrays"></a><span data-ttu-id="deb98-203">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="deb98-203">Parameter arrays</span></span> ###

<span data-ttu-id="deb98-204">メソッドに厳密な数の引数を指定する要件が限定的になることがあります。</span><span class="sxs-lookup"><span data-stu-id="deb98-204">Sometimes, the requirement that you specify the exact number of arguments to your method is restrictive.</span></span> <span data-ttu-id="deb98-205">`params` キーワードを利用し、パラメーターがパラメーター配列であることを示すことで、可変数の引数でメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-205">By using the `params` keyword to indicate that a parameter is a parameter array, you allow your method to be called with a variable number of arguments.</span></span> <span data-ttu-id="deb98-206">`params` キーワードでタグが付けられたパラメーターは配列型にする必要があり、メソッドのパラメーター リストの最後のパラメーターにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-206">The parameter tagged with the `params` keyword must must be an array type, and it must be the last parameter in the method's parameter list.</span></span>

<span data-ttu-id="deb98-207">呼び出し元は、次の 3 つの方法のいずれかでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-207">A caller can then invoke the method in either of three ways:</span></span>

- <span data-ttu-id="deb98-208">必要な数の要素を含む、適切な型の配列を渡す。</span><span class="sxs-lookup"><span data-stu-id="deb98-208">By passing an array of the appropriate type that contains the desired number of elements.</span></span>
- <span data-ttu-id="deb98-209">適切な型の引数をコンマで区切った一覧をメソッドに渡す。</span><span class="sxs-lookup"><span data-stu-id="deb98-209">By passing a comma-separated list of individual arguments of the appropriate type to the method.</span></span>
- <span data-ttu-id="deb98-210">パラメーター配列に引数を指定しない。</span><span class="sxs-lookup"><span data-stu-id="deb98-210">By not providing an argument to the parameter array.</span></span>

<span data-ttu-id="deb98-211">次の例では、`DoStringOperation` という名前のメソッドを定義します。このメソッドは、その最初のパラメーターである `StringOperation` 列挙メンバーにより指定された文字列操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="deb98-211">The following example defines a method named `DoStringOperation` that performs the string operation specified by its first parameter, a `StringOperation` enumeration member.</span></span> <span data-ttu-id="deb98-212">操作の実行対象である文字列はパラメーター配列により設定されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-212">The strings upon which it is to perform the operation are defined by a parameter array.</span></span> <span data-ttu-id="deb98-213">`Main` メソッドには、メソッド呼び出しの 3 つ全部の方法が入っています。</span><span class="sxs-lookup"><span data-stu-id="deb98-213">The `Main` method illustrates all three ways of invoking the method.</span></span> <span data-ttu-id="deb98-214">パラメーター配列に引数が指定されず、その値が `null` になるケースを処理するには、`params` キーワードでタグが付けられたメソッドを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-214">Note that the method tagged with the `params` keyword must be prepared to handle the case in which no argument is supplied for the parameter array, so that its value is `null`.</span></span>

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a><span data-ttu-id="deb98-215">省略可能なパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="deb98-215">Optional parameters and arguments</span></span> ##

<span data-ttu-id="deb98-216">メソッド定義では、そのパラメーターが必須であるか、任意であるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-216">A method definition can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="deb98-217">既定では、パラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="deb98-217">By default, parameters are required.</span></span> <span data-ttu-id="deb98-218">省略可能なパラメーターを指定するには、メソッド定義にパラメーターの既定値を追加します。</span><span class="sxs-lookup"><span data-stu-id="deb98-218">Optional parameters are specified by including the parameter's default value in the method definition.</span></span> <span data-ttu-id="deb98-219">メソッドが呼び出されるとき、省略可能なパラメーターに引数が指定されていなければ、既定値が代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-219">When the method is called, if no argument is supplied for an optional parameter, the default value is used instead.</span></span>

<span data-ttu-id="deb98-220">パラメーターの既定値は、次の種類の式のいずれかで割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-220">The parameter's default value must be assigned by one of the following kinds of expressions:</span></span>

- <span data-ttu-id="deb98-221">リテラル文字列や数値など、定数。</span><span class="sxs-lookup"><span data-stu-id="deb98-221">A constant, such as a literal string or number.</span></span>
- <span data-ttu-id="deb98-222">`ValType` が値型となる、`new ValType` 形式の式。</span><span class="sxs-lookup"><span data-stu-id="deb98-222">An expression of the form `new ValType`, where `ValType` is a value type.</span></span> <span data-ttu-id="deb98-223">型の実際のメンバーではない、値型の暗黙の既定コンストラクターが呼び出されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-223">Note that this invokes the value type's implicit default constructor, which is not an actual member of the type.</span></span>
- <span data-ttu-id="deb98-224">`ValType` が値型となる、`default(ValType)` 形式の式。</span><span class="sxs-lookup"><span data-stu-id="deb98-224">An expression of the form `default(ValType)`, where `ValType` is a value type.</span></span>

<span data-ttu-id="deb98-225">メソッドに必須のパラメーターと省略可能なパラメーターの両方が含まれる場合、省略可能なパラメーターはパラメーター リストの終わりに定義されます (すべての必須パラメーターの後に)。</span><span class="sxs-lookup"><span data-stu-id="deb98-225">If a method includes both required and optional parameters, optional parameters are defined at the end of the parameter list, after all required parameters.</span></span>

<span data-ttu-id="deb98-226">次の例では、`ExampleMethod` メソッドを定義しています。必須のパラメーターが 1 つ、省略可能なパラメーターが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="deb98-226">The following example defines a method, `ExampleMethod`, that has one required and two optional parameters.</span></span>

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

<span data-ttu-id="deb98-227">省略可能なパラメーターを複数持つメソッドが位置引数で呼び出された場合、呼び出し元は、引数が指定される最初のパラメーターから最後のパラメーターまで、すべての省略可能なパラメーターに引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-227">If a method with multiple optional arguments is invoked using positional arguments, the caller must supply an argument for all optional parameters from the first one to the last one for which an argument is supplied.</span></span> <span data-ttu-id="deb98-228">たとえば、`ExampleMethod` メソッドの場合、呼び出し元が `description` パラメーターの引数を指定した場合、`optionalInt` パラメーターの引数も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-228">In the case of the  `ExampleMethod` method, for example, if the caller supplies an argument for the `description` parameter, it must also supply one for the `optionalInt` parameter.</span></span> <span data-ttu-id="deb98-229">`opt.ExampleMethod(2, 2, "Addition of 2 and 2");` は有効なメソッド呼び出しです。`opt.ExampleMethod(2, , "Addition of 2 and 0);` は、"引数がありません" というコンパイラ エラーを発生させます。</span><span class="sxs-lookup"><span data-stu-id="deb98-229">`opt.ExampleMethod(2, 2, "Addition of 2 and 2");` is a valid method call; `opt.ExampleMethod(2, , "Addition of 2 and 0);` generates an "Argument missing" compiler error.</span></span>

<span data-ttu-id="deb98-230">メソッドが名前付き引数または位置引数と名前付き引数の組み合わせで呼び出される場合、呼び出し元は、メソッド呼び出しの最後の位置引数の後に続く引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-230">If a method is called using named arguments or a combination of positional and named arguments, the caller can omit any arguments that follow the last positional argument in the method call.</span></span>

<span data-ttu-id="deb98-231">次の例では、`ExampleMethod` メソッドが 3 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-231">The following example calls the `ExampleMethod` method three times.</span></span>  <span data-ttu-id="deb98-232">最初の 2 つのメソッド呼び出しでは、位置引数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-232">The first two method calls use positional arguments.</span></span> <span data-ttu-id="deb98-233">最初の呼び出しではいずれの省略可能なパラメーターも省略され、2 つ目の呼び出しでは最後の引数が省略されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-233">The first omits both optional arguments, while the second omits the last argument.</span></span> <span data-ttu-id="deb98-234">3 つ目のメソッドは必須パラメーターの位置引数を指定しますが、名前付き引数を利用して `description` パラメーターに値を指定します。`optionalInt` パラメーターは省略します。</span><span class="sxs-lookup"><span data-stu-id="deb98-234">The third method call supplies a positional argument for the required parameter, but uses a named argument to supply a value to the `description` parameter while omitting the `optionalInt` argument.</span></span>

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

<span data-ttu-id="deb98-235">省略可能なパラメーターの使用は、*オーバーロードの解決*に影響を与えます。次のように、特定のオーバーロードをメソッド呼び出しで呼び出すかどうかを C# コンパイラが決定する方法に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="deb98-235">The use of optional parameters affects *overload resolution*, or the way in which the C# compiler determines which particular overload should be invoked by a method call, as follows:</span></span>

- <span data-ttu-id="deb98-236">メソッド、インデクサー、コンストラクターのパラメーターのそれぞれが任意であるか、名前か位置により、呼び出しステートメントの 1 つの引数に対応するとき、その引数がパラメーターの型に変換できる場合、メソッド、インデクサー、コンストラクターが実行の候補になります。</span><span class="sxs-lookup"><span data-stu-id="deb98-236">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>
- <span data-ttu-id="deb98-237">複数の候補が見つかった場合、明示的に指定される引数には、優先変換に関するオーバーロード解決の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-237">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="deb98-238">任意のパラメーターの省略された引数は無視されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-238">Omitted arguments for optional parameters are ignored.</span></span>
- <span data-ttu-id="deb98-239">2 つの候補が等しく良好であると判断された場合、呼び出しで引数が省略された任意のパラメーターのない候補が優先されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-239">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="deb98-240">これはパラメーターの少ない候補に関するオーバーロード解決の一般優先設定の結果です。</span><span class="sxs-lookup"><span data-stu-id="deb98-240">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>

 <a name="return"></a>
 ## <a name="return-values"></a><span data-ttu-id="deb98-241">戻り値</span><span class="sxs-lookup"><span data-stu-id="deb98-241">Return values</span></span> ##

<span data-ttu-id="deb98-242">メソッドは、呼び出し元に値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-242">Methods can return a value to the caller.</span></span> <span data-ttu-id="deb98-243">戻り値の型 (メソッド名の前に記述されている型) が `void`でない場合、メソッドは、`return` キーワードを使用して値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-243">If the return type (the type listed before the method name) is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="deb98-244">`return` キーワードに続いて変数、定数、または戻り値の型に一致する値が記述されたステートメントは、その値をメソッドの呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="deb98-244">A statement with the `return` keyword followed by a variable, constant, or expression that matches the return type will return that value to the method caller.</span></span> <span data-ttu-id="deb98-245">戻り値の型が void 以外のメソッドで値を返すには、 `return` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-245">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="deb98-246">また、 `return` キーワードは、メソッドの実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="deb98-246">The `return` keyword also stops the execution of the method.</span></span>

<span data-ttu-id="deb98-247">戻り値の型が `void`の場合、値を持たない `return` ステートメントは、メソッドの実行を中止するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="deb98-247">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="deb98-248">`return` キーワードを使用しない場合、メソッドは、コード ブロックの最後に到達したときに実行を中止します。</span><span class="sxs-lookup"><span data-stu-id="deb98-248">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span>

<span data-ttu-id="deb98-249">たとえば、次の 2 つのメソッドは、 `return` キーワードを使用して整数を返します。</span><span class="sxs-lookup"><span data-stu-id="deb98-249">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

<span data-ttu-id="deb98-250">メソッドから返された値を使用する場合、呼び出し元のメソッド内で同じ型の値を使用している場所では、メソッド呼び出し自体を値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-250">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="deb98-251">戻り値は、変数に代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="deb98-251">You can also assign the return value to a variable.</span></span> <span data-ttu-id="deb98-252">たとえば、次の 2 つのコードでは、同様の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="deb98-252">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

<span data-ttu-id="deb98-253">この場合、ローカル変数 `result`を使用して値を格納する手順はオプションです。</span><span class="sxs-lookup"><span data-stu-id="deb98-253">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="deb98-254">このローカル変数によってコードの読みやすさが向上することがあります。また、引数の元の値をメソッドのスコープ全体で保持する場合に必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="deb98-254">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="deb98-255">メソッドで複数の値を返すと便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-255">Sometimes, you want your method to return more than a single value.</span></span> <span data-ttu-id="deb98-256">C# 7.0 以降では、*タプル型*と*タプル リテラル*を使用してこれを簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-256">Starting with C# 7.0, you can do this easily by using *tuple types* and *tuple literals*.</span></span> <span data-ttu-id="deb98-257">タプル型は、タプルの要素のデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="deb98-257">The tuple type defines the data types of the tuple's elements.</span></span> <span data-ttu-id="deb98-258">タプル リテラルは、返されたタプルの実際の値を提供します。</span><span class="sxs-lookup"><span data-stu-id="deb98-258">Tuple literals provide the actual values of the returned tuple.</span></span> <span data-ttu-id="deb98-259">次の例では、`(string, string, string, int)` は、`GetPersonalInfo` メソッドにより返されるタプル型を定義します。</span><span class="sxs-lookup"><span data-stu-id="deb98-259">In the following example, `(string, string, string, int)` defines the tuple type that is returned by the `GetPersonalInfo` method.</span></span> <span data-ttu-id="deb98-260">式 `(per.FirstName, per.MiddleName, per.LastName, per.Age)` はタプル リテラルです。このメソッドは、`PersonInfo` オブジェクトの名、ミドルネーム、姓、年齢を返します。</span><span class="sxs-lookup"><span data-stu-id="deb98-260">The expression `(per.FirstName, per.MiddleName, per.LastName, per.Age)` is the tuple literal; the method returns the first, middle, and last name, along with the age, of a `PersonInfo` object.</span></span>

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

<span data-ttu-id="deb98-261">呼び出し元はそれから、次のようなコードで返されたタプルを利用します。</span><span class="sxs-lookup"><span data-stu-id="deb98-261">The caller can then consume the returned tuple with code like the following:</span></span>

```csharp
var person = GetPersonalInfo("111111111")
if (person != null)
   Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

<span data-ttu-id="deb98-262">名前は、タプル型の定義のタプル要素に割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="deb98-262">Names can also be assigned to the tuple elements in the tuple type definition.</span></span> <span data-ttu-id="deb98-263">次の例は、名前付き要素を使用する `GetPersonalInfo` メソッドの別バージョンです。</span><span class="sxs-lookup"><span data-stu-id="deb98-263">The following example shows an alternate version of the `GetPersonalInfo` method that uses named elements:</span></span>

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

<span data-ttu-id="deb98-264">この例の `GetPersonInfo` メソッドの呼び出しは次のように変更できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-264">The previous call to the `GetPersonInfo` method can then be modified as follows:</span></span>

```csharp
var person = GetPersonalInfo("111111111");
if (person != null)
   Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

<span data-ttu-id="deb98-265">メソッドに引数として配列が渡されるとき、そのメソッドが個々の要素の値を変更する場合、メソッドが配列を返す必要はありません。ただし、見やすいから、値の流れが機能的になるからといった理由で配列を返してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="deb98-265">If a method is passed an array as an argument and modifies the value of individual elements, it is not necessary for the method to return the array, although you may choose to do so for good style or functional flow of values.</span></span>  <span data-ttu-id="deb98-266">配列を返す必要がないのは、C# ではすべての参照型が値で渡され、配列参照の値がその配列のポインターになるためです。</span><span class="sxs-lookup"><span data-stu-id="deb98-266">This is because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="deb98-267">次の例では、`DoubleValues` メソッドで行われた `values` 配列の内容の変更を、配列の参照があるあらゆるコードで観察できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-267">In the following example, changes to the contents of the `values` array that are made in the `DoubleValues` method are observable by any code that has a reference to the array.</span></span>

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="exten"></a>
 ## <a name="extension-methods"></a><span data-ttu-id="deb98-268">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-268">Extension methods</span></span> ##

<span data-ttu-id="deb98-269">通常、既存の型にメソッドを追加する方法が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="deb98-269">Ordinarily, there are two ways to add a method to an existing type:</span></span>

- <span data-ttu-id="deb98-270">その型のソース コードを変更する。</span><span class="sxs-lookup"><span data-stu-id="deb98-270">Modify the source code for that type.</span></span> <span data-ttu-id="deb98-271">もちろん、型のソース コードを所有していない場合、これはできません。</span><span class="sxs-lookup"><span data-stu-id="deb98-271">You cannot do this, of course, if you do not own the type's source code.</span></span> <span data-ttu-id="deb98-272">また、メソッドをサポートするプライベース データ フィールドも追加した場合、これは互換性に影響する変更になります。</span><span class="sxs-lookup"><span data-stu-id="deb98-272">And this becomes a breaking change if you also add any private data fields to support the method.</span></span>
- <span data-ttu-id="deb98-273">派生クラスで新しいメソッドを定義する。</span><span class="sxs-lookup"><span data-stu-id="deb98-273">Define the new method in a derived class.</span></span> <span data-ttu-id="deb98-274">構造体や列挙型など、その他の型の継承を利用し、メソッドをこの方法で追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="deb98-274">A method cannot be added in this way using inheritance for other types, such as structures and enumerations.</span></span> <span data-ttu-id="deb98-275">シール クラスにメソッドを "追加する" こともできません。</span><span class="sxs-lookup"><span data-stu-id="deb98-275">Nor can it be used to "add" a method to a sealed class.</span></span>

<span data-ttu-id="deb98-276">拡張メソッドでは、型自体を変更せずに、あるいは継承された型に新しいメソッドを実装せずに、既存の型にメソッドを "追加" できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-276">Extension methods let you "add" a method to an existing type without modifying the type itself or implementing the new method in an inherited type.</span></span> <span data-ttu-id="deb98-277">また、拡張メソッドは、それが拡張する型と同じアセンブリに置く必要がありません。</span><span class="sxs-lookup"><span data-stu-id="deb98-277">The extension method also does not have to reside in the same assembly as the type it extends.</span></span> <span data-ttu-id="deb98-278">型の定義済みメンバーのように拡張メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="deb98-278">You call an extension method as if it were a defined member of a type.</span></span>

<span data-ttu-id="deb98-279">詳細については、「[拡張メソッド](programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-279">For more information, see [Extension Methods](programming-guide/classes-and-structs/extension-methods.md).</span></span>

<a name="async"></a>
## <a name="async-methods"></a><span data-ttu-id="deb98-280">非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="deb98-280">Async Methods</span></span> ##

<span data-ttu-id="deb98-281">非同期機能を使用することによって、明示的なコールバックを使用せずに、または複数のメソッドやラムダ式にわたって手動でコードを分割することなく、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="deb98-281">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="deb98-282">メソッドに [async](language-reference/keywords/async.md) 修飾子を付けると、そのメソッドで [await](language-reference/keywords/await.md) 演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-282">If you mark a method with the [async](language-reference/keywords/async.md) modifier, you can use the [await](language-reference/keywords/await.md) operator in the method.</span></span> <span data-ttu-id="deb98-283">コントロールが非同期メソッドの `await` 式に到達すると、待機中のタスクが完了していない場合、コントロールが呼び出し元に戻ります。`await` キーワードが与えられたメソッドの進行は、待機中のタスクが完了するまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-283">When control reaches an `await` expression in the async method, control returns to the caller if the awaited task is not completed, and progress in the method with the `await` keyword is suspended until the awaited task completes.</span></span> <span data-ttu-id="deb98-284">タスクが完了すると、メソッドで実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-284">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="deb98-285">非同期メソッドは、まだ完了していない待機中の最初のオブジェクトに達するか、または非同期メソッドの最後に達すると、呼び出し元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="deb98-285">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="deb98-286">非同期メソッドの戻り値の型としては、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task>、`void` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-286">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or `void`.</span></span> <span data-ttu-id="deb98-287">戻り値の型 `void` は主として、戻り値の型 `void` が必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-287">The `void` return type is used primarily to define event handlers, where a `void` return type is required.</span></span> <span data-ttu-id="deb98-288">`void` を返す非同期メソッドは待機できません。void を返すメソッドの呼び出し元は、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="deb98-288">An async method that returns `void` can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span> <span data-ttu-id="deb98-289">C# 7.0 がリリースされるとこの制約が緩和され、非同期メソッドで[タスクと同種のあらゆる型を返す](https://github.com/ljw1004/roslyn/blob/features/async-return/docs/specs/feature%20-%20arbitrary%20async%20returns.md)ことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="deb98-289">C# 7.0, when it is released, will ease this restriction to allow an async method [to return any task-like type](https://github.com/ljw1004/roslyn/blob/features/async-return/docs/specs/feature%20-%20arbitrary%20async%20returns.md).</span></span>

<span data-ttu-id="deb98-290">次の例では、`DelayAsync` は、整数を返す return ステートメントのある非同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="deb98-290">In the following example, `DelayAsync` is an async method that has a return statement that returns an integer.</span></span> <span data-ttu-id="deb98-291">非同期メソッドであるため、そのメソッド宣言で戻り値の型 `Task<int>` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-291">Because it is an async method, its method declaration must have a return type of `Task<int>`.</span></span> <span data-ttu-id="deb98-292">戻り値の型が `Task<int>`であるため、次のステートメント `int result = await delayTask` に示すように、`DoSomethingAsync` 内の `await` 式を評価すると整数が生成されます。</span><span class="sxs-lookup"><span data-stu-id="deb98-292">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer, as the following `int result = await delayTask` statement demonstrates.</span></span>

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

<span data-ttu-id="deb98-293">非同期メソッドで [in](language-reference/keywords/in-parameter-modifier.md)、[ref](language-reference/keywords/ref.md)、[out](language-reference/keywords/out-parameter-modifier.md) パラメーターを宣言することはできませんが、これらのパラメーターを持つメソッドを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="deb98-293">An async method can't declare any [in](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), or [out](language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

 <span data-ttu-id="deb98-294">非同期メソッドの詳細については、「[Async および Await を使用した非同期プログラミング](async.md)」、「[非同期プログラムにおける制御フロー](programming-guide/concepts/async/control-flow-in-async-programs.md)」、「[非同期の戻り値の型](programming-guide/concepts/async/async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-294">For more information about async methods, see [Asynchronous Programming with Async and Await](async.md), [Control Flow in Async Programs](programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](programming-guide/concepts/async/async-return-types.md).</span></span>

<a name="expr"></a>
## <a name="expression-bodied-members"></a><span data-ttu-id="deb98-295">式形式のメンバー</span><span class="sxs-lookup"><span data-stu-id="deb98-295">Expression-bodied members</span></span> ##

<span data-ttu-id="deb98-296">メソッドの定義としては、式の結果を即座に返すか、またはメソッドの本文として 1 つのステートメントを含むものが一般的です。</span><span class="sxs-lookup"><span data-stu-id="deb98-296">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span>  <span data-ttu-id="deb98-297">`=>`を使用してこのようなメソッドを定義するための構文ショートカットがあります。</span><span class="sxs-lookup"><span data-stu-id="deb98-297">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="deb98-298">メソッドが `void` を返すか、非同期メソッドである場合は、メソッドの本文を (ラムダの場合と同様に) ステートメント式にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="deb98-298">If the method returns `void` or is an async method, the body of the method must be a statement expression (same as with lambdas).</span></span>  <span data-ttu-id="deb98-299">プロパティとインデクサーは読み取り専用にする必要があるため、`get` アクセサー キーワードは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="deb98-299">For properties and indexers, they must be read-only, and you do not use the `get` accessor keyword.</span></span>

<a name="iterators"></a>
## <a name="iterators"></a><span data-ttu-id="deb98-300">Iterators</span><span class="sxs-lookup"><span data-stu-id="deb98-300">Iterators</span></span> ##

<span data-ttu-id="deb98-301">反復子は、リストや配列など、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="deb98-301">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="deb98-302">反復子は、[yield return](language-reference/keywords/yield.md) ステートメントを使用して、各要素を 1 回に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="deb98-302">An iterator uses the [yield return](language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="deb98-303">`yield return` ステートメントに到達すると、現在の場所が記録されます。呼び出し元は、シーケンス内の次の要素を要求できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-303">When a `yield return` statement is reached, the current location is remembered so that the caller can request the next element in the sequence.</span></span>

<span data-ttu-id="deb98-304">反復子の戻り値の型には、 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601>を指定できます。</span><span class="sxs-lookup"><span data-stu-id="deb98-304">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="deb98-305">詳細については、「 [反復子](programming-guide/concepts/iterators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deb98-305">For more information, see [Iterators](programming-guide/concepts/iterators.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="deb98-306">関連項目</span><span class="sxs-lookup"><span data-stu-id="deb98-306">See also</span></span> ##

<span data-ttu-id="deb98-307">[アクセス修飾子](language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-307">[Access Modifiers](language-reference/keywords/access-modifiers.md) </span></span>  
<span data-ttu-id="deb98-308">[静的クラスと静的クラス メンバー](programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-308">[Static Classes and Static Class Members](programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
<span data-ttu-id="deb98-309">[継承](programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-309">[Inheritance](programming-guide/classes-and-structs/inheritance.md) </span></span>  
<span data-ttu-id="deb98-310">[抽象クラスとシール クラス、およびクラス メンバー](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-310">[Abstract and Sealed Classes and Class Members](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
<span data-ttu-id="deb98-311">[params](language-reference/keywords/params.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-311">[params](language-reference/keywords/params.md) </span></span>  
<span data-ttu-id="deb98-312">[out](language-reference/keywords/out-parameter-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-312">[out](language-reference/keywords/out-parameter-modifier.md) </span></span>  
<span data-ttu-id="deb98-313">[ref](language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-313">[ref](language-reference/keywords/ref.md) </span></span>  
<span data-ttu-id="deb98-314">[in](language-reference/keywords/in-parameter-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="deb98-314">[in](language-reference/keywords/in-parameter-modifier.md) </span></span>  
[<span data-ttu-id="deb98-315">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="deb98-315">Passing Parameters</span></span>](programming-guide/classes-and-structs/passing-parameters.md)
