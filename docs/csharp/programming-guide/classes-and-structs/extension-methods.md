---
title: "拡張メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
caps.latest.revision: 35
author: BillWagner
ms.author: wiwagn
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
ms.sourcegitcommit: d74c1d0760d4e776c2cf4c7dea1dac060c85a83c
ms.openlocfilehash: 657f9ebfba5d6f49d3a88cb1cf790e4a0134a007
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="extension-methods-c-programming-guide"></a><span data-ttu-id="7fad2-102">拡張メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7fad2-102">Extension Methods (C# Programming Guide)</span></span>
<span data-ttu-id="7fad2-103">拡張メソッドを使用すると、新規の派生型の作成、再コンパイル、または元の型の変更を行うことなく既存の型にメソッドを "追加" できます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-103">Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type.</span></span> <span data-ttu-id="7fad2-104">拡張メソッドは特別な種類の静的メソッドですが、拡張された型のインスタンス メソッドのように呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-104">Extension methods are a special kind of static method, but they are called as if they were instance methods on the extended type.</span></span> <span data-ttu-id="7fad2-105">C#、F#、および Visual Basic で作成されたクライアント コードの場合は、拡張メソッドの呼び出しと、型で実際に定義されたメソッドの呼び出しに明確な違いはありません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-105">For client code written in C#, F# and Visual Basic, there is no apparent difference between calling an extension method and the methods that are actually defined in a type.</span></span>  
  
 <span data-ttu-id="7fad2-106">最も一般的な拡張メソッドは、既存の [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 型および <xref:System.Collections.IEnumerable?displayProperty=fullName> 型にクエリ機能を追加する <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 標準クエリ演算子です。</span><span class="sxs-lookup"><span data-stu-id="7fad2-106">The most common extension methods are the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] standard query operators that add query functionality to the existing <xref:System.Collections.IEnumerable?displayProperty=fullName> and <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> types.</span></span> <span data-ttu-id="7fad2-107">この標準クエリ演算子を使用するには、まず `using System.Linq` ディレクティブを使用して、スコープに含めます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-107">To use the standard query operators, first bring them into scope with a `using System.Linq` directive.</span></span> <span data-ttu-id="7fad2-108"><xref:System.Collections.Generic.IEnumerable%601> を実装するすべての型は、<xref:System.Linq.Enumerable.GroupBy%2A>、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Average%2A> などのインスタンス メソッドを持っていると考えられます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-108">Then any type that implements <xref:System.Collections.Generic.IEnumerable%601> appears to have instance methods such as <xref:System.Linq.Enumerable.GroupBy%2A>, <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="7fad2-109"><xref:System.Collections.Generic.List%601>、<xref:System.Array> などの <xref:System.Collections.Generic.IEnumerable%601> 型のインスタンスの後に "ドット" を入力すると、IntelliSense により、ステートメントの入力候補としてこれらの追加メソッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-109">You can see these additional methods in IntelliSense statement completion when you type "dot" after an instance of an <xref:System.Collections.Generic.IEnumerable%601> type such as <xref:System.Collections.Generic.List%601> or <xref:System.Array>.</span></span>  
  
 <span data-ttu-id="7fad2-110">整数の配列において、標準クエリ演算子の `OrderBy` メソッドを呼び出す方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-110">The following example shows how to call the standard query operator `OrderBy` method on an array of integers.</span></span> <span data-ttu-id="7fad2-111">かっこ内の式はラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="7fad2-111">The expression in parentheses is a lambda expression.</span></span> <span data-ttu-id="7fad2-112">標準クエリ演算子の多くはパラメーターとしてラムダ式を受け取りますが、拡張メソッドでは、これは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-112">Many standard query operators take lambda expressions as parameters, but this is not a requirement for extension methods.</span></span> <span data-ttu-id="7fad2-113">詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-113">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="7fad2-114">[!code-cs[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7fad2-114">[!code-cs[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="7fad2-115">拡張メソッドは、静的メソッドとして定義しますが、インスタンス メソッドの構文を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-115">Extension methods are defined as static methods but are called by using instance method syntax.</span></span> <span data-ttu-id="7fad2-116">最初のパラメーターでは、メソッドが操作する型を指定します。このパラメーターの前には [this](../../../csharp/language-reference/keywords/this.md) 修飾子を付加します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-116">Their first parameter specifies which type the method operates on, and the parameter is preceded by the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span> <span data-ttu-id="7fad2-117">`using` ディレクティブを使用して名前空間をソース コードに明示的にインポートした場合、拡張メソッドはそのスコープでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7fad2-117">Extension methods are only in scope when you explicitly import the namespace into your source code with a `using` directive.</span></span>  
  
 <span data-ttu-id="7fad2-118"><xref:System.String?displayProperty=fullName> クラスに対して拡張メソッドを定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-118">The following example shows an extension method defined for the <xref:System.String?displayProperty=fullName> class.</span></span> <span data-ttu-id="7fad2-119">入れ子になっていない、非ジェネリックの静的クラス内で定義されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-119">Note that it is defined inside a non-nested, non-generic static class:</span></span>  
  
 <span data-ttu-id="7fad2-120">[!code-cs[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7fad2-120">[!code-cs[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="7fad2-121">この `WordCount` ディレクティブを使用することで、`using` 拡張メソッドをスコープに取り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-121">The `WordCount` extension method can be brought into scope with this `using` directive:</span></span>  
  
```  
using ExtensionMethods;  
```  
  
 <span data-ttu-id="7fad2-122">また、この構文を使用することで、アプリケーションから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-122">And it can be called from an application by using this syntax:</span></span>  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 <span data-ttu-id="7fad2-123">コードでは、インスタンス メソッドの構文を使用して拡張メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-123">In your code you invoke the extension method with instance method syntax.</span></span> <span data-ttu-id="7fad2-124">ただし、コンパイラが生成する中間言語 (IL: Intermediate Language) により、コードは静的メソッドに対する呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-124">However, the intermediate language (IL) generated by the compiler translates your code into a call on the static method.</span></span> <span data-ttu-id="7fad2-125">したがって、カプセル化の原則には実質的に違反していません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-125">Therefore, the principle of encapsulation is not really being violated.</span></span> <span data-ttu-id="7fad2-126">実際に、拡張メソッドは、それらが拡張している型のプライベート変数にはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-126">In fact, extension methods cannot access private variables in the type they are extending.</span></span>  
  
 <span data-ttu-id="7fad2-127">詳細については、「[方法: カスタム拡張メソッドを実装して呼び出す](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-127">For more information, see [How to: Implement and Call a Custom  Extension Method](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).</span></span>  
  
 <span data-ttu-id="7fad2-128">一般的には、独自の拡張メソッドを実装するよりも、拡張メソッドを呼び出すことの方がはるかに多くなります。</span><span class="sxs-lookup"><span data-stu-id="7fad2-128">In general, you will probably be calling extension methods far more often than implementing your own.</span></span> <span data-ttu-id="7fad2-129">拡張メソッドは、インスタンス メソッドの構文を使用して呼び出すので、特別な知識がなくてもクライアント コードからそれらを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-129">Because extension methods are called by using instance method syntax, no special knowledge is required to use them from client code.</span></span> <span data-ttu-id="7fad2-130">メソッドが定義されている名前空間に関する `using` ディレクティブを追加するだけで、特定の型の拡張メソッドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7fad2-130">To enable extension methods for a particular type, just add a `using` directive for the namespace in which the methods are defined.</span></span> <span data-ttu-id="7fad2-131">たとえば、標準クエリ演算子を使用するには、次の `using` ディレクティブをコードに追加します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-131">For example, to use the standard query operators, add this `using` directive to your code:</span></span>  
  
```  
using System.Linq;  
```  
  
 <span data-ttu-id="7fad2-132">場合によっては、System.Core.dll への参照も追加する必要があります。ほとんどの <xref:System.Collections.Generic.IEnumerable%601> 型で利用できる追加メソッドとして、標準クエリ演算子が IntelliSense により表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7fad2-132">(You may also have to add a reference to System.Core.dll.) You will notice that the standard query operators now appear in IntelliSense as additional methods available for most <xref:System.Collections.Generic.IEnumerable%601> types.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fad2-133"><xref:System.String> の場合、IntelliSense により標準クエリ演算子は表示されませんが、利用できます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-133">Although standard query operators do not appear in IntelliSense for <xref:System.String>, they are still available.</span></span>  
  
## <a name="binding-extension-methods-at-compile-time"></a><span data-ttu-id="7fad2-134">コンパイル時の拡張メソッドのバインディング</span><span class="sxs-lookup"><span data-stu-id="7fad2-134">Binding Extension Methods at Compile Time</span></span>  
 <span data-ttu-id="7fad2-135">拡張メソッドを使用してクラスまたはインターフェイスを拡張することはできますが、これらをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-135">You can use extension methods to extend a class or interface, but not to override them.</span></span> <span data-ttu-id="7fad2-136">インターフェイス メソッドまたはクラス メソッドと同じ名前およびシグネチャを持つ拡張メソッドは決して呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-136">An extension method with the same name and signature as an interface or class method will never be called.</span></span> <span data-ttu-id="7fad2-137">コンパイル時に、型自体で定義されているインスタンス メソッドよりも低い優先順位が拡張メソッドには必ず設定されます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-137">At compile time, extension methods always have lower priority than instance methods defined in the type itself.</span></span> <span data-ttu-id="7fad2-138">つまり、型に `Process(int i)` という名前のメソッドがあり、これと同じシグネチャの拡張メソッドがある場合、コンパイラは必ずインスタンス メソッドにバインドします。</span><span class="sxs-lookup"><span data-stu-id="7fad2-138">In other words, if a type has a method named `Process(int i)`, and you have an extension method with the same signature, the compiler will always bind to the instance method.</span></span> <span data-ttu-id="7fad2-139">コンパイラは、メソッド呼び出しを検出すると、最初に型のインスタンス メソッドから一致するものを探します。</span><span class="sxs-lookup"><span data-stu-id="7fad2-139">When the compiler encounters a method invocation, it first looks for a match in the type's instance methods.</span></span> <span data-ttu-id="7fad2-140">一致するものが見つからない場合、型に対して定義されている拡張メソッドを検索し、見つかった最初の拡張メソッドにバインドします。</span><span class="sxs-lookup"><span data-stu-id="7fad2-140">If no match is found, it will search for any extension methods that are defined for the type, and bind to the first extension method that it finds.</span></span> <span data-ttu-id="7fad2-141">次の例は、コンパイラが拡張メソッドとインスタンス メソッドのどちらにバインドするかを決定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7fad2-141">The following example demonstrates how the compiler determines which extension method or instance method to bind to.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fad2-142">例</span><span class="sxs-lookup"><span data-stu-id="7fad2-142">Example</span></span>  
 <span data-ttu-id="7fad2-143">次の例は、C# のコンパイラがメソッド呼び出しを型のインスタンス メソッドにバインドするか、拡張メソッドにバインドするかを決定するときに従う規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="7fad2-143">The following example demonstrates the rules that the C# compiler follows in determining whether to bind a method call to an instance method on the type, or to an extension method.</span></span> <span data-ttu-id="7fad2-144">`Extensions` 静的クラスには、`IMyInterface` を実装する型に対して定義された拡張メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fad2-144">The static class `Extensions` contains extension methods defined for any type that implements `IMyInterface`.</span></span> <span data-ttu-id="7fad2-145">`A`、`B`、および `C` の各クラスはすべてこのインターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="7fad2-145">Classes `A`, `B`, and `C` all implement the interface.</span></span>  
  
 <span data-ttu-id="7fad2-146">`MethodB` 拡張メソッドは、その名前とシグネチャがクラスにより既に実装されているメソッドと完全に一致しているため、呼び出されることはありません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-146">The `MethodB` extension method is never called because its name and signature exactly match methods already implemented by the classes.</span></span>  
  
 <span data-ttu-id="7fad2-147">コンパイラは、一致するシグネチャを持つインスタンス メソッドを検出できない場合、一致する拡張メソッド (存在する場合) にバインドします。</span><span class="sxs-lookup"><span data-stu-id="7fad2-147">When the compiler cannot find an instance method with a matching signature, it will bind to a matching extension method if one exists.</span></span>  
  
 <span data-ttu-id="7fad2-148">[!code-cs[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="7fad2-148">[!code-cs[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/extension-methods_3.cs)]</span></span>  
  
## <a name="general-guidelines"></a><span data-ttu-id="7fad2-149">一般的なガイドライン</span><span class="sxs-lookup"><span data-stu-id="7fad2-149">General Guidelines</span></span>  
 <span data-ttu-id="7fad2-150">拡張メソッドは、一般的に、必要な場合に限り注意して実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7fad2-150">In general, we recommend that you implement extension methods sparingly and only when you have to.</span></span> <span data-ttu-id="7fad2-151">クライアント コードで既存の型を拡張する必要がある場合、可能であれば既存の型から派生した新しい型を作成することで行ってください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-151">Whenever possible, client code that must extend an existing type should do so by creating a new type derived from the existing type.</span></span> <span data-ttu-id="7fad2-152">詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-152">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="7fad2-153">拡張メソッドを使用して、変更できないソース コードのある型を拡張する場合、型の実装の変更により拡張メソッドが破損するというリスクを負うことになります。</span><span class="sxs-lookup"><span data-stu-id="7fad2-153">When using an extension method to extend a type whose source code you cannot change, you run the risk that a change in the implementation of the type will cause your extension method to break.</span></span>  
  
 <span data-ttu-id="7fad2-154">所定の型の拡張メソッドを実装する場合、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-154">If you do implement extension methods for a given type, remember the following points:</span></span>  
  
-   <span data-ttu-id="7fad2-155">拡張メソッドが型で定義されているメソッドと同じシグネチャを持つ場合、その拡張メソッドは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="7fad2-155">An extension method will never be called if it has the same signature as a method defined in the type.</span></span>  
  
-   <span data-ttu-id="7fad2-156">拡張メソッドは名前空間レベルでスコープ内に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-156">Extension methods are brought into scope at the namespace level.</span></span> <span data-ttu-id="7fad2-157">たとえば、`Extensions` という名前の単一の名前空間に、拡張メソッドを含む複数の静的クラスがある場合、`using Extensions;` ディレクティブによって、それらのすべての拡張メソッドがスコープ内に取り込まれます。</span><span class="sxs-lookup"><span data-stu-id="7fad2-157">For example, if you have multiple static classes that contain extension methods in a single namespace named `Extensions`, they will all be brought into scope by the `using Extensions;` directive.</span></span>  
  
 <span data-ttu-id="7fad2-158">実装したクラス ライブラリでは、アセンブリのバージョン番号のインクリメントを避けるために、拡張メソッドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-158">For a class library that you implemented, you shouldn't use extension methods to avoid incrementing the version number of an assembly.</span></span> <span data-ttu-id="7fad2-159">ソース コードを所有するライブラリに重要な機能を追加する場合は、アセンブリのバージョン管理について標準の .NET Framework ガイドラインに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fad2-159">If you want to add significant functionality to a library for which you own the source code, you should follow the standard .NET Framework guidelines for assembly versioning.</span></span> <span data-ttu-id="7fad2-160">詳細については、「[アセンブリのバージョン管理](https://msdn.microsoft.com/library/51ket42z)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fad2-160">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fad2-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fad2-161">See Also</span></span>  
 <span data-ttu-id="7fad2-162">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7fad2-162">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7fad2-163">[並列プログラミングのサンプル (拡張メソッドの例が多数掲載されています)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364) </span><span class="sxs-lookup"><span data-stu-id="7fad2-163">[Parallel Programming Samples (these include many example extension methods)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364) </span></span>  
 <span data-ttu-id="7fad2-164">[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="7fad2-164">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
 <span data-ttu-id="7fad2-165">[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2) </span><span class="sxs-lookup"><span data-stu-id="7fad2-165">[Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2) </span></span>  
 <span data-ttu-id="7fad2-166">[インスタンス パラメーターの変換規則とその影響](http://go.microsoft.com/fwlink/?LinkId=112385) </span><span class="sxs-lookup"><span data-stu-id="7fad2-166">[Conversion rules for Instance parameters and their impact](http://go.microsoft.com/fwlink/?LinkId=112385) </span></span>  
 <span data-ttu-id="7fad2-167">[拡張メソッドの言語間での相互運用性](http://go.microsoft.com/fwlink/?LinkId=112386) </span><span class="sxs-lookup"><span data-stu-id="7fad2-167">[Extension methods Interoperability between languages](http://go.microsoft.com/fwlink/?LinkId=112386) </span></span>  
 <span data-ttu-id="7fad2-168">[拡張メソッドとカリー化デリゲート](http://go.microsoft.com/fwlink/?LinkId=112387) </span><span class="sxs-lookup"><span data-stu-id="7fad2-168">[Extension methods and Curried Delegates](http://go.microsoft.com/fwlink/?LinkId=112387) </span></span>  
 [<span data-ttu-id="7fad2-169">バインディングとエラー報告に関する拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="7fad2-169">Extension method Binding and Error reporting</span></span>](http://go.microsoft.com/fwlink/?LinkId=112388)

