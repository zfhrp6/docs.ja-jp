---
title: "オブジェクト (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
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
ms.openlocfilehash: a2a23d02e4ea95e908f97bc7264ee64d6899aee8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="objects-c-programming-guide"></a><span data-ttu-id="8d24a-102">オブジェクト (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8d24a-102">Objects (C# Programming Guide)</span></span>
<span data-ttu-id="8d24a-103">クラスまたは構造体の定義は、型の動作を指定する設計図に似ています。</span><span class="sxs-lookup"><span data-stu-id="8d24a-103">A class or struct definition is like a blueprint that specifies what the type can do.</span></span> <span data-ttu-id="8d24a-104">オブジェクトは基本的に、設計図に従って割り当てられて構成されたメモリのブロックです。</span><span class="sxs-lookup"><span data-stu-id="8d24a-104">An object is basically a block of memory that has been allocated and configured according to the blueprint.</span></span> <span data-ttu-id="8d24a-105">プログラムでは、同じクラスのオブジェクトを多数作成できます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-105">A program may create many objects of the same class.</span></span> <span data-ttu-id="8d24a-106">オブジェクトはインスタンスとも呼ばれ、名前付きの変数または配列やコレクションに格納できます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-106">Objects are also called instances, and they can be stored in either a named variable or in an array or collection.</span></span> <span data-ttu-id="8d24a-107">クライアント コードとは、これらの変数を使ってメソッドを呼び出し、オブジェクトのパブリック プロパティにアクセスするコードです。</span><span class="sxs-lookup"><span data-stu-id="8d24a-107">Client code is the code that uses these variables to call the methods and access the public properties of the object.</span></span> <span data-ttu-id="8d24a-108">C# などのオブジェクト指向言語では、一般的なプログラムは動的に対話する複数のオブジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="8d24a-108">In an object-oriented language such as C#, a typical program consists of multiple objects interacting dynamically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d24a-109">静的な型の動作方法は、ここで説明する動作方法とは異なります。</span><span class="sxs-lookup"><span data-stu-id="8d24a-109">Static types behave differently than what is described here.</span></span> <span data-ttu-id="8d24a-110">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d24a-110">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="struct-instances-vs-class-instances"></a><span data-ttu-id="8d24a-111">構造体インスタンスとクラス インスタンス</span><span class="sxs-lookup"><span data-stu-id="8d24a-111">Struct Instances vs. Class Instances</span></span>  
 <span data-ttu-id="8d24a-112">クラスは参照型であるため、クラスのオブジェクトの変数は、マネージ ヒープ上のオブジェクトのアドレスへの参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-112">Because classes are reference types, a variable of a class object holds a reference to the address of the object on the managed heap.</span></span> <span data-ttu-id="8d24a-113">同じ型の 2 番目のオブジェクトが最初のオブジェクトに割り当てられた場合、両方の変数がそのアドレスにあるオブジェクトを参照します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-113">If a second object of the same type is assigned to the first object, then both variables refer to the object at that address.</span></span> <span data-ttu-id="8d24a-114">この点については、後で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-114">This point is discussed in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="8d24a-115">クラスのインスタンスは、[new 演算子](../../../csharp/language-reference/keywords/new-operator.md)を使って作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-115">Instances of classes are created by using the [new operator](../../../csharp/language-reference/keywords/new-operator.md).</span></span> <span data-ttu-id="8d24a-116">次の例では、`Person` が型で、`person1` と `person 2` がその型のインスタンスつまりオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="8d24a-116">In the following example, `Person` is the type and `person1` and `person 2` are instances, or objects, of that type.</span></span>  
  
 <span data-ttu-id="8d24a-117">[!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d24a-117">[!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]</span></span>  
  
 <span data-ttu-id="8d24a-118">構造体は値型であるため、構造体オブジェクトの変数はオブジェクト全体のコピーを保持します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-118">Because structs are value types, a variable of a struct object holds a copy of the entire object.</span></span> <span data-ttu-id="8d24a-119">構造体のインスタンスも `new` 演算子を使って作成できますが、次の例で示すように、これは必要ではありません。</span><span class="sxs-lookup"><span data-stu-id="8d24a-119">Instances of structs can also be created by using the `new` operator, but this is not required, as shown in the following example:</span></span>  
  
 <span data-ttu-id="8d24a-120">[!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d24a-120">[!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]</span></span>  
  
 <span data-ttu-id="8d24a-121">`p1` と `p2` のメモリはどちらも、スレッドのスタックに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-121">The memory for both `p1` and `p2` is allocated on the thread stack.</span></span> <span data-ttu-id="8d24a-122">そのメモリは、それが宣言されている型またはメソッドと共に解放されます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-122">That memory is reclaimed along with the type or method in which it is declared.</span></span> <span data-ttu-id="8d24a-123">これは、割り当て時に構造体がコピーされる理由の 1 です。</span><span class="sxs-lookup"><span data-stu-id="8d24a-123">This is one reason why structs are copied on assignment.</span></span> <span data-ttu-id="8d24a-124">これに対し、クラスのインスタンスに割り当てられたメモリは、そのオブジェクトに対するすべての参照がスコープ外になると、共通言語ランタイムによって自動的に解放 (ガベージ コレクション) されます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-124">By contrast, the memory that is allocated for a class instance is automatically reclaimed (garbage collected) by the common language runtime when all references to the object have gone out of scope.</span></span> <span data-ttu-id="8d24a-125">C++ のようにクラスのオブジェクトを確定的に破棄することはできません。</span><span class="sxs-lookup"><span data-stu-id="8d24a-125">It is not possible to deterministically destroy a class object like you can in C++.</span></span> <span data-ttu-id="8d24a-126">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] でのガベージ コレクションについて詳しくは、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8d24a-126">For more information about garbage collection in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d24a-127">マネージ ヒープ上のメモリの割り当てと解放は、共通言語ランタイムにおいて高度に最適化されています。</span><span class="sxs-lookup"><span data-stu-id="8d24a-127">The allocation and deallocation of memory on the managed heap is highly optimized in the common language runtime.</span></span> <span data-ttu-id="8d24a-128">ほとんどの場合、ヒープへのクラス インスタンスの割り当てと、スタックへの構造体インスタンスの割り当てに、パフォーマンス コストの点で大きな違いはありません。</span><span class="sxs-lookup"><span data-stu-id="8d24a-128">In most cases there is no significant difference in the performance cost of allocating a class instance on the heap versus allocating a struct instance on the stack.</span></span>  
  
## <a name="object-identity-vs-value-equality"></a><span data-ttu-id="8d24a-129">オブジェクト ID と値の等価性</span><span class="sxs-lookup"><span data-stu-id="8d24a-129">Object Identity vs. Value Equality</span></span>  
 <span data-ttu-id="8d24a-130">2 つのオブジェクトが等しいかどうかを比較するときは、最初に、2 つの変数がメモリ内の同じオブジェクトを表しているかどうかを知りたいのか、それともオブジェクトの 1 つ以上のフィールドの値が等しいかどうかを知りたいのかを、区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d24a-130">When you compare two objects for equality, you must first distinguish whether you want to know whether the two variables represent the same object in memory, or whether the values of one or more of their fields are equivalent.</span></span> <span data-ttu-id="8d24a-131">値を比較する場合は、オブジェクトが値型 (構造体) のインスタンスか、または参照型 (クラス、デリゲート、配列) のインスタンスかを、検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d24a-131">If you are intending to compare values, you must consider whether the objects are instances of value types (structs) or reference types (classes, delegates, arrays).</span></span>  
  
-   <span data-ttu-id="8d24a-132">クラスの 2 つのインスタンスがメモリ内の同じ場所を参照しているかどうか (つまり、同じ *ID* か) を調べるには、静的な <xref:System.Object.Equals%2A> メソッドを使います</span><span class="sxs-lookup"><span data-stu-id="8d24a-132">To determine whether two class instances refer to the same location in memory (which means that they have the same *identity*), use the static <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="8d24a-133">(<xref:System.Object?displayProperty=fullName> は、ユーザー定義の構造体やクラスを含む、すべての値型と参照型の暗黙の基底クラスです)。</span><span class="sxs-lookup"><span data-stu-id="8d24a-133">(<xref:System.Object?displayProperty=fullName> is the implicit base class for all value types and reference types, including user-defined structs and classes.)</span></span>  
  
-   <span data-ttu-id="8d24a-134">2 つの構造体インスタンスのインスタンス フィールドが同じ値を持つかどうかを調べるには、<xref:System.ValueType.Equals%2A?displayProperty=fullName> メソッドを使います。</span><span class="sxs-lookup"><span data-stu-id="8d24a-134">To determine whether the instance fields in two struct instances have the same values, use the <xref:System.ValueType.Equals%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="8d24a-135">すべての構造体は <xref:System.ValueType?displayProperty=fullName> を暗黙的に継承するので、次の例で示すように、オブジェクトで直接メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-135">Because all structs implicitly inherit from <xref:System.ValueType?displayProperty=fullName>, you call the method directly on your object as shown in the following example:</span></span>  
  
 <span data-ttu-id="8d24a-136">[!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d24a-136">[!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]</span></span>  
  
 <span data-ttu-id="8d24a-137"><xref:System.ValueType?displayProperty=fullName> での `Equals` の実装は、構造体に存在するフィールドを特定できる必要があるため、リフレクションを使います。</span><span class="sxs-lookup"><span data-stu-id="8d24a-137">The <xref:System.ValueType?displayProperty=fullName> implementation of `Equals` uses reflection because it must be able to determine what the fields are in any struct.</span></span> <span data-ttu-id="8d24a-138">独自の構造体を作成するときは、`Equals` メソッドをオーバーライドして、独自の型に固有の効率的な等値アルゴリズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-138">When creating your own structs, override the `Equals` method to provide an efficient equality algorithm that is specific to your type.</span></span>  
  
-   <span data-ttu-id="8d24a-139">クラスの 2 つのインスタンスのフィールドの値が等しいかどうかを調べるには、<xref:System.Object.Equals%2A> メソッドまたは [== 演算子](../../../csharp/language-reference/operators/equality-comparison-operator.md)を使用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d24a-139">To determine whether the values of the fields in two class instances are equal, you might be able to use the <xref:System.Object.Equals%2A> method or the [== operator](../../../csharp/language-reference/operators/equality-comparison-operator.md).</span></span> <span data-ttu-id="8d24a-140">ただし、この方法を使用できるのは、その型のオブジェクトにおける "等値" の意味のカスタム定義が、クラスのオーバーライドまたはオーバーロードによって提供されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="8d24a-140">However, only use them if the class has overridden or overloaded them to provide a custom definition of what "equality" means for objects of that type.</span></span> <span data-ttu-id="8d24a-141">クラスは、<xref:System.IEquatable%601> インターフェイスまたは <xref:System.Collections.Generic.IEqualityComparer%601> インターフェイスを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d24a-141">The class might also implement the <xref:System.IEquatable%601> interface or the <xref:System.Collections.Generic.IEqualityComparer%601> interface.</span></span> <span data-ttu-id="8d24a-142">どちらのインターフェイスも、値の等価性をテストするために使うことができるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8d24a-142">Both interfaces provide methods that can be used to test value equality.</span></span> <span data-ttu-id="8d24a-143">`Equals` をオーバーライドする独自のクラスを設計するときは、「[方法: 型の値の等価性を定義する](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)」および「<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>」に記載されているガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="8d24a-143">When designing your own classes that override `Equals`, make sure to follow the guidelines stated in [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md) and <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d24a-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d24a-144">Related Sections</span></span>  
 <span data-ttu-id="8d24a-145">詳細情報</span><span class="sxs-lookup"><span data-stu-id="8d24a-145">For more information:</span></span>  
  
-   [<span data-ttu-id="8d24a-146">クラス</span><span class="sxs-lookup"><span data-stu-id="8d24a-146">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [<span data-ttu-id="8d24a-147">構造体</span><span class="sxs-lookup"><span data-stu-id="8d24a-147">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [<span data-ttu-id="8d24a-148">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="8d24a-148">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="8d24a-149">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="8d24a-149">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [<span data-ttu-id="8d24a-150">イベント</span><span class="sxs-lookup"><span data-stu-id="8d24a-150">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="8d24a-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d24a-151">See Also</span></span>  
 <span data-ttu-id="8d24a-152">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-152">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8d24a-153">[object](../../../csharp/language-reference/keywords/object.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-153">[object](../../../csharp/language-reference/keywords/object.md) </span></span>  
 <span data-ttu-id="8d24a-154">[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-154">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="8d24a-155">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-155">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="8d24a-156">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-156">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 <span data-ttu-id="8d24a-157">[New 演算子](../../../csharp/language-reference/keywords/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="8d24a-157">[new Operator](../../../csharp/language-reference/keywords/new-operator.md) </span></span>  
 [<span data-ttu-id="8d24a-158">共通型システム</span><span class="sxs-lookup"><span data-stu-id="8d24a-158">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)

