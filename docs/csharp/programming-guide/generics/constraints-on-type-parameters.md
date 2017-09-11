---
title: "型パラメーターの制約 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: 41
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
ms.openlocfilehash: e91ae026bd89a6dd30b4c9233da4dd897928291e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="constraints-on-type-parameters-c-programming-guide"></a><span data-ttu-id="40c9f-102">型パラメーターの制約 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="40c9f-102">Constraints on Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="40c9f-103">ジェネリック クラスを定義する場合、クライアント コードがクラスをインスタンス化するときに、型引数に使用できる種類の型に制限を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-103">When you define a generic class, you can apply restrictions to the kinds of types that client code can use for type arguments when it instantiates your class.</span></span> <span data-ttu-id="40c9f-104">クライアント コードで、この制限で許可されていない型を使用してクラスをインスタンス化しようとすると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-104">If client code tries to instantiate your class by using a type that is not allowed by a constraint, the result is a compile-time error.</span></span> <span data-ttu-id="40c9f-105">これらの制限は、制約と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-105">These restrictions are called constraints.</span></span> <span data-ttu-id="40c9f-106">制約を指定するには、`where` コンテキスト キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-106">Constraints are specified by using the `where` contextual keyword.</span></span> <span data-ttu-id="40c9f-107">次の表は、6 種類の制約をまとめた一覧です。</span><span class="sxs-lookup"><span data-stu-id="40c9f-107">The following table lists the six types of constraints:</span></span>  
  
|<span data-ttu-id="40c9f-108">制約</span><span class="sxs-lookup"><span data-stu-id="40c9f-108">Constraint</span></span>|<span data-ttu-id="40c9f-109">説明</span><span class="sxs-lookup"><span data-stu-id="40c9f-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="40c9f-110">where T: struct</span><span class="sxs-lookup"><span data-stu-id="40c9f-110">where T: struct</span></span>|<span data-ttu-id="40c9f-111">この型引数は値の型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-111">The type argument must be a value type.</span></span> <span data-ttu-id="40c9f-112"><xref:System.Nullable> を除く任意の値の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-112">Any value type except <xref:System.Nullable> can be specified.</span></span> <span data-ttu-id="40c9f-113">詳細については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40c9f-113">See [Using Nullable Types](../../../csharp/programming-guide/nullable-types/using-nullable-types.md) for more information.</span></span>|  
|<span data-ttu-id="40c9f-114">where T : class</span><span class="sxs-lookup"><span data-stu-id="40c9f-114">where T : class</span></span>|<span data-ttu-id="40c9f-115">この型引数は、参照型である必要があります。任意のクラス、インターフェイス、デリゲート、または配列型にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-115">The type argument must be a reference type; this applies also to any class, interface, delegate, or array type.</span></span>|  
|<span data-ttu-id="40c9f-116">where T : new()</span><span class="sxs-lookup"><span data-stu-id="40c9f-116">where T : new()</span></span>|<span data-ttu-id="40c9f-117">この型引数には、パラメーターなしのパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="40c9f-117">The type argument must have a public parameterless constructor.</span></span> <span data-ttu-id="40c9f-118">`new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-118">When used together with other constraints, the `new()` constraint must be specified last.</span></span>|  
|<span data-ttu-id="40c9f-119">where T : \<base class name></span><span class="sxs-lookup"><span data-stu-id="40c9f-119">where T : \<base class name></span></span>|<span data-ttu-id="40c9f-120">この型引数は、指定された基底クラスであるか、そのクラスから派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-120">The type argument must be or derive from the specified base class.</span></span>|  
|<span data-ttu-id="40c9f-121">where T : \<interface name></span><span class="sxs-lookup"><span data-stu-id="40c9f-121">where T : \<interface name></span></span>|<span data-ttu-id="40c9f-122">この型引数は、指定されたインターフェイスであるか、そのインターフェイスを実装している必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-122">The type argument must be or implement the specified interface.</span></span> <span data-ttu-id="40c9f-123">複数のインターフェイス制約を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-123">Multiple interface constraints can be specified.</span></span> <span data-ttu-id="40c9f-124">制約のインターフェイスを汎用的にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-124">The constraining interface can also be generic.</span></span>|  
|<span data-ttu-id="40c9f-125">where T : U</span><span class="sxs-lookup"><span data-stu-id="40c9f-125">where T : U</span></span>|<span data-ttu-id="40c9f-126">T に指定する型引数は、U に指定された引数であるか、その引数から派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-126">The type argument supplied for T must be or derive from the argument supplied for U.</span></span>|  
  
## <a name="why-use-constraints"></a><span data-ttu-id="40c9f-127">制約を使用する理由</span><span class="sxs-lookup"><span data-stu-id="40c9f-127">Why Use Constraints</span></span>  
 <span data-ttu-id="40c9f-128">ジェネリック リスト内の項目を調べて、有効かどうかを判断する場合、または他の項目と比較する場合、クライアント コードに指定される可能性があるすべての型引数が、呼び出す必要がある演算子またはメソッドをサポートしているという何らかの保証をコンパイラが獲得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-128">If you want to examine an item in a generic list to determine whether it is valid or to compare it to some other item, the compiler must have some guarantee that the operator or method it has to call will be supported by any type argument that might be specified by client code.</span></span> <span data-ttu-id="40c9f-129">この保証を獲得するには、1 つまたは複数の制約をジェネリック クラス定義に適用します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-129">This guarantee is obtained by applying one or more constraints to your generic class definition.</span></span> <span data-ttu-id="40c9f-130">たとえば、この基底クラスの制約は、この型のオブジェクト、またはこの型から派生したオブジェクトのみを型引数として使用することをコンパイラに指示しています。</span><span class="sxs-lookup"><span data-stu-id="40c9f-130">For example, the base class constraint tells the compiler that only objects of this type or derived from this type will be used as type arguments.</span></span> <span data-ttu-id="40c9f-131">コンパイラがこの保証を獲得したら、その型のメソッドをジェネリック クラスで呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-131">Once the compiler has this guarantee, it can allow methods of that type to be called in the generic class.</span></span> <span data-ttu-id="40c9f-132">制約を適用するには、コンテキスト キーワード `where` を使用します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-132">Constraints are applied by using the contextual keyword `where`.</span></span> <span data-ttu-id="40c9f-133">基底クラス制約を適用して `GenericList<T>` クラス (「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照) に追加できる機能を説明するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-133">The following code example demonstrates the functionality we can add to the `GenericList<T>` class (in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md)) by applying a base class constraint.</span></span>  
  
 <span data-ttu-id="40c9f-134">[!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-134">[!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="40c9f-135">この制約を使用すると、型 T のすべての項目は `Employee` オブジェクトであるか、`Employee` から継承されたオブジェクトであると保証されるため、ジェネリック クラスから `Employee.Name` プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-135">The constraint enables the generic class to use the `Employee.Name` property because all items of type T are guaranteed to be either an `Employee` object or an object that inherits from `Employee`.</span></span>  
  
 <span data-ttu-id="40c9f-136">同じ型パラメーターに複数の制約を適用できます。また、制約自体をジェネリック型にすることもできます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-136">Multiple constraints can be applied to the same type parameter, and the constraints themselves can be generic types, as follows:</span></span>  
  
 <span data-ttu-id="40c9f-137">[!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-137">[!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]</span></span>  
  
 <span data-ttu-id="40c9f-138">型パラメーターを制約すると、使用できる操作とメソッド呼び出しの数は、制約する型、およびその継承階層内のすべての型でサポートされている数まで増えます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-138">By constraining the type parameter, you increase the number of allowable operations and method calls to those supported by the constraining type and all types in its inheritance hierarchy.</span></span> <span data-ttu-id="40c9f-139">そのため、ジェネリック クラスまたはメソッドを指定するときに、単純な割り当てや、`System.Object` でサポートされていない任意のメソッド呼び出しでジェネリック メンバーに対して任意の操作を実行する場合、型パラメーターに制約を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-139">Therefore, when you design generic classes or methods, if you will be performing any operation on the generic members beyond simple assignment or calling any methods not supported by `System.Object`, you will have to apply constraints to the type parameter.</span></span>  
  
 <span data-ttu-id="40c9f-140">`where T : class` 制約を適用する場合は、型パラメーターに `==` および `!=` 演算子を使用しないでください。これらの演算子でテストされるのは、値の等価性ではなく、参照 ID についてのみです。</span><span class="sxs-lookup"><span data-stu-id="40c9f-140">When applying the `where T : class` constraint, avoid the `==` and `!=` operators on the type parameter because these operators will test for reference identity only, not for value equality.</span></span> <span data-ttu-id="40c9f-141">これらの演算子が、引数として使用されている型内でオーバーロードされている場合でも、同様のことが言えます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-141">This is the case even if these operators are overloaded in a type that is used as an argument.</span></span> <span data-ttu-id="40c9f-142">この点を説明するコードを次に示します。<xref:System.String> クラスが `==` 演算子をオーバーロードしている場合でも、出力は false です。</span><span class="sxs-lookup"><span data-stu-id="40c9f-142">The following code illustrates this point; the output is false even though the <xref:System.String> class overloads the `==` operator.</span></span>  
  
 <span data-ttu-id="40c9f-143">[!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-143">[!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]</span></span>  
  
 <span data-ttu-id="40c9f-144">この動作の理由は、コンパイル時に、コンパイラは T が参照型であることしか認識しておらず、すべての参照型で有効な既定の演算子を使用する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="40c9f-144">The reason for this behavior is that, at compile time, the compiler only knows that T is a reference type, and therefore must use the default operators that are valid for all reference types.</span></span> <span data-ttu-id="40c9f-145">値の等価性をテストする必要がある場合は、`where T : IComparable<T>` 制約も適用し、ジェネリック クラスの制約に使用されるすべてのクラスでそのインターフェイスを実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="40c9f-145">If you must test for value equality, the recommended way is to also apply the `where T : IComparable<T>` constraint and implement that interface in any class that will be used to construct the generic class.</span></span>  
  
## <a name="constraining-multiple-parameters"></a><span data-ttu-id="40c9f-146">複数のパラメーターを制約する</span><span class="sxs-lookup"><span data-stu-id="40c9f-146">Constraining Multiple Parameters</span></span>  
 <span data-ttu-id="40c9f-147">複数のパラメーターに制約を適用できます。また、複数の制約を 1 つのパラメーターに適用することができます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-147">You can apply constraints to multiple parameters, and multiple constraints to a single parameter, as shown in the following example:</span></span>  
  
 <span data-ttu-id="40c9f-148">[!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-148">[!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]</span></span>  
  
## <a name="unbounded-type-parameters"></a><span data-ttu-id="40c9f-149">非バインド型パラメーター</span><span class="sxs-lookup"><span data-stu-id="40c9f-149">Unbounded Type Parameters</span></span>  
 <span data-ttu-id="40c9f-150">パブリック クラス `SampleClass<T>{}` の T など、制約がない型パラメーターは、非バインド型パラメーターと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-150">Type parameters that have no constraints, such as T in public class `SampleClass<T>{}`, are called unbounded type parameters.</span></span> <span data-ttu-id="40c9f-151">非バインド型パラメーターには次の規則があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-151">Unbounded type parameters have the following rules:</span></span>  
  
-   <span data-ttu-id="40c9f-152">`!=` および `==` 演算子は使用できません。これは、具象型引数がこれらの演算子をサポートするという保証がないためです。</span><span class="sxs-lookup"><span data-stu-id="40c9f-152">The `!=` and `==` operators cannot be used because there is no guarantee that the concrete type argument will support these operators.</span></span>  
  
-   <span data-ttu-id="40c9f-153">これらの演算子は `System.Object` との間で相互に変換できます。また、任意のインターフェイス型に明示的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-153">They can be converted to and from `System.Object` or explicitly converted to any interface type.</span></span>  
  
-   <span data-ttu-id="40c9f-154">これは [null](../../../csharp/language-reference/keywords/null.md) と比較することができます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-154">You can compare to [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="40c9f-155">非バインド型パラメーターと `null` を比較し、その型引数が値の型の場合、比較結果として常に false が返されます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-155">If an unbounded parameter is compared to `null`, the comparison will always return false if the type argument is a value type.</span></span>  
  
## <a name="type-parameters-as-constraints"></a><span data-ttu-id="40c9f-156">制約としての型パラメーター</span><span class="sxs-lookup"><span data-stu-id="40c9f-156">Type Parameters as Constraints</span></span>  
 <span data-ttu-id="40c9f-157">制約としてジェネリック型パラメーターを使用する方法は、独自の型パラメーターがあるメンバー関数が、含まれる型の型パラメーターにそのパラメーターを制約する必要がある場合に便利です。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="40c9f-157">The use of a generic type parameter as a constraint is useful when a member function with its own type parameter has to constrain that parameter to the type parameter of the containing type, as shown in the following example:</span></span>  
  
 <span data-ttu-id="40c9f-158">[!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-158">[!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]</span></span>  
  
 <span data-ttu-id="40c9f-159">前の例の `T` は、`Add` メソッドのコンテキストでは型の制約ですが、`List` クラスのコンテキストでは非バインド型パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="40c9f-159">In the previous example, `T` is a type constraint in the context of the `Add` method, and an unbounded type parameter in the context of the `List` class.</span></span>  
  
 <span data-ttu-id="40c9f-160">型パラメーターは、ジェネリック クラス定義の制約としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="40c9f-160">Type parameters can also be used as constraints in generic class definitions.</span></span> <span data-ttu-id="40c9f-161">型パラメーターは、他の型パラメーターと共に山かっこ内で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="40c9f-161">Note that the type parameter must be declared within the angle brackets together with any other type parameters:</span></span>  
  
 <span data-ttu-id="40c9f-162">[!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="40c9f-162">[!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]</span></span>  
  
 <span data-ttu-id="40c9f-163">ジェネリック クラスで制約として型パラメーターを使用する方法が便利なのは、ごく限られた場合のみです。コンパイラでは、`System.Object` から派生したことを除き、型パラメーターに関して何も仮定できないためです。</span><span class="sxs-lookup"><span data-stu-id="40c9f-163">The usefulness of type parameters as constraints with generic classes is very limited because the compiler can assume nothing about the type parameter except that it derives from `System.Object`.</span></span> <span data-ttu-id="40c9f-164">2 つの型パラメーター間に継承関係を適用するシナリオには、ジェネリック クラスの制約として型パラメーターを使用してください。</span><span class="sxs-lookup"><span data-stu-id="40c9f-164">Use type parameters as constraints on generic classes in scenarios in which you want to enforce an inheritance relationship between two type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c9f-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="40c9f-165">See Also</span></span>  
 <span data-ttu-id="40c9f-166"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="40c9f-166"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="40c9f-167">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="40c9f-167">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="40c9f-168">[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="40c9f-168">[Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
 <span data-ttu-id="40c9f-169">[ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md) </span><span class="sxs-lookup"><span data-stu-id="40c9f-169">[Generic Classes](../../../csharp/programming-guide/generics/generic-classes.md) </span></span>  
 [<span data-ttu-id="40c9f-170">new 制約</span><span class="sxs-lookup"><span data-stu-id="40c9f-170">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)

