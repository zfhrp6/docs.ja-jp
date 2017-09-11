---
title: "ジェネリック メソッド (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], methods
ms.assetid: 673eeea2-4b48-4faa-9c4e-2e89449221b9
caps.latest.revision: 27
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 14461773303bafc098f79c3686b1f76827f11005
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-methods-c-programming-guide"></a><span data-ttu-id="91a16-102">ジェネリック メソッド (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="91a16-102">Generic Methods (C# Programming Guide)</span></span>
<span data-ttu-id="91a16-103">ジェネリック メソッドは、次のように型パラメーターで宣言されるメソッドです。</span><span class="sxs-lookup"><span data-stu-id="91a16-103">A generic method is a method that is declared with type parameters, as follows:</span></span>  
  
 <span data-ttu-id="91a16-104">[!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-104">[!code-cs[csProgGuideGenerics#22](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_1.cs)]</span></span>  
  
 <span data-ttu-id="91a16-105">メソッドの呼び出し方法の 1 つを示しているのが次のコード サンプルです。型引数に `int` を利用します。</span><span class="sxs-lookup"><span data-stu-id="91a16-105">The following code example shows one way to call the method by using `int` for the type argument:</span></span>  
  
 <span data-ttu-id="91a16-106">[!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-106">[!code-cs[csProgGuideGenerics#23](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_2.cs)]</span></span>  
  
 <span data-ttu-id="91a16-107">型引数は省略することもできます。コンパイラが推定します。</span><span class="sxs-lookup"><span data-stu-id="91a16-107">You can also omit the type argument and the compiler will infer it.</span></span> <span data-ttu-id="91a16-108">次は、前の呼び出しと同じように `Swap` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="91a16-108">The following call to `Swap` is equivalent to the previous call:</span></span>  
  
 <span data-ttu-id="91a16-109">[!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-109">[!code-cs[csProgGuideGenerics#24](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_3.cs)]</span></span>  
  
 <span data-ttu-id="91a16-110">型推定の同じ規則が静的メソッドとインスタンス メソッドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="91a16-110">The same rules for type inference apply to static methods and instance methods.</span></span> <span data-ttu-id="91a16-111">コンパイラは、渡されたメソッド引数に基づいて型パラメーターを推定できます。制約や戻り値だけでは型パラメーターを推定できません。</span><span class="sxs-lookup"><span data-stu-id="91a16-111">The compiler can infer the type parameters based on the method arguments you pass in; it cannot infer the type parameters only from a constraint or return value.</span></span> <span data-ttu-id="91a16-112">そのため、パラメーターのないメソッドでは型を推定できません。</span><span class="sxs-lookup"><span data-stu-id="91a16-112">Therefore type inference does not work with methods that have no parameters.</span></span> <span data-ttu-id="91a16-113">型はコンパイル時に、コンパイラがオーバーロードされたメソッド シグネチャを解決する前に推定されます。</span><span class="sxs-lookup"><span data-stu-id="91a16-113">Type inference occurs at compile time before the compiler tries to resolve overloaded method signatures.</span></span> <span data-ttu-id="91a16-114">コンパイラは、同じ名前を共有するすべてのジェネリック メソッドに型の推定ロジックを適用します。</span><span class="sxs-lookup"><span data-stu-id="91a16-114">The compiler applies type inference logic to all generic methods that share the same name.</span></span> <span data-ttu-id="91a16-115">オーバーロード解決手順では、型を推定できたジェネリック メソッドのみがコンパイラに含まれます。</span><span class="sxs-lookup"><span data-stu-id="91a16-115">In the overload resolution step, the compiler includes only those generic methods on which type inference succeeded.</span></span>  
  
 <span data-ttu-id="91a16-116">ジェネリック クラス内では、非ジェネリック メソッドは、次のように、クラスレベルの型パラメーターにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="91a16-116">Within a generic class, non-generic methods can access the class-level type parameters, as follows:</span></span>  
  
 <span data-ttu-id="91a16-117">[!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-117">[!code-cs[csProgGuideGenerics#25](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_4.cs)]</span></span>  
  
 <span data-ttu-id="91a16-118">包含クラスと同じ型パラメーターを受け取るジェネリック メソッドを定義すると、コンパイラは警告 CS0693 を生成します。これは、メソッド範囲内で、内側の `T` に与えられた引数により外側の `T` に与えられた引数が隠されるためです。</span><span class="sxs-lookup"><span data-stu-id="91a16-118">If you define a generic method that takes the same type parameters as the containing class, the compiler generates warning CS0693 because within the method scope, the argument supplied for the inner `T` hides the argument supplied for the outer `T`.</span></span> <span data-ttu-id="91a16-119">クラスがインスタンス化されたときに与えらたれ型パラメーター以外の型パラメーターでジェネリック クラス メソッドを呼び出すという柔軟性が必要な場合、メソッドの型パラメーターに別の識別子を指定することを検討してください。次の例の `GenericList2<T>` をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="91a16-119">If you require the flexibility of calling a generic class method with type arguments other than the ones provided when the class was instantiated, consider providing another identifier for the type parameter of the method, as shown in `GenericList2<T>` in the following example.</span></span>  
  
 <span data-ttu-id="91a16-120">[!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-120">[!code-cs[csProgGuideGenerics#26](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_5.cs)]</span></span>  
  
 <span data-ttu-id="91a16-121">メソッドの型パラメーターでさらに多くの特殊操作を可能にするために、制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="91a16-121">Use constraints to enable more specialized operations on type parameters in methods.</span></span> <span data-ttu-id="91a16-122">`SwapIfGreater<T>` という名前が付けられた `Swap<T>` のこのバージョンは、<xref:System.IComparable%601> を実装する型引数との併用でのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="91a16-122">This version of `Swap<T>`, now named `SwapIfGreater<T>`, can only be used with type arguments that implement <xref:System.IComparable%601>.</span></span>  
  
 <span data-ttu-id="91a16-123">[!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-123">[!code-cs[csProgGuideGenerics#27](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_6.cs)]</span></span>  
  
 <span data-ttu-id="91a16-124">ジェネリック メソッドは、いくつかの型パラメーターでオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="91a16-124">Generic methods can be overloaded on several type parameters.</span></span> <span data-ttu-id="91a16-125">たとえば、次のメソッドはすべて同じクラスに配置できます。</span><span class="sxs-lookup"><span data-stu-id="91a16-125">For example, the following methods can all be located in the same class:</span></span>  
  
 <span data-ttu-id="91a16-126">[!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="91a16-126">[!code-cs[csProgGuideGenerics#28](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-methods_7.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="91a16-127">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="91a16-127">C# Language Specification</span></span>  
 <span data-ttu-id="91a16-128">詳細については、「[C# 言語の仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91a16-128">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a16-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="91a16-129">See Also</span></span>  
 <span data-ttu-id="91a16-130"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="91a16-130"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="91a16-131">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="91a16-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="91a16-132">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="91a16-132">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 [<span data-ttu-id="91a16-133">メソッド</span><span class="sxs-lookup"><span data-stu-id="91a16-133">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

