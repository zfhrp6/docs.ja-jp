---
title: "インターフェイス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: 45
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
ms.openlocfilehash: 0552cea71f66ba8c299b1706cab6778c9e3367c9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="interfaces-c-programming-guide"></a><span data-ttu-id="4c84f-102">インターフェイス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4c84f-102">Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="4c84f-103">インターフェイスには、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)で実装できる関連機能のグループの定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-103">An interface contains definitions for a group of related functionalities that a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md) can implement.</span></span>  
  
 <span data-ttu-id="4c84f-104">インターフェイスを使用すると、たとえば、クラス内の複数のソースからの動作を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-104">By using interfaces, you can, for example, include behavior from multiple sources in a class.</span></span> <span data-ttu-id="4c84f-105">C# ではクラスの複数の継承がサポートされないため、この機能は重要です。</span><span class="sxs-lookup"><span data-stu-id="4c84f-105">That capability is important in C# because the language doesn't support multiple inheritance of classes.</span></span> <span data-ttu-id="4c84f-106">また、構造体の継承をシミュレートする場合はインターフェイスを使用する必要があります。これは、実際に別の構造体またはクラスから継承することができないためです。</span><span class="sxs-lookup"><span data-stu-id="4c84f-106">In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.</span></span>  
  
 <span data-ttu-id="4c84f-107">インターフェイスを定義するには、次の例に示すように、[interface](../../../csharp/language-reference/keywords/interface.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-107">You define an interface by using the [interface](../../../csharp/language-reference/keywords/interface.md) keyword, as the following example shows.</span></span>  
  
 <span data-ttu-id="4c84f-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c84f-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span></span>  
  
 <span data-ttu-id="4c84f-109"><xref:System.IEquatable%601> インターフェイスを実装するすべてのクラスまたは構造体は、インターフェイスで指定された署名に一致する <xref:System.IEquatable%601.Equals%2A> メソッドの定義を含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-109">Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies.</span></span> <span data-ttu-id="4c84f-110">したがって、`IEquatable<T>` を実装するクラスが `Equals` メソッドを含むと想定したうえで、これを使用してクラスの 1 つのインスタンスが同じクラスの別のインスタンスと等しいかどうかを判定できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-110">As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.</span></span>  
  
 <span data-ttu-id="4c84f-111">`IEquatable<T>` の定義は `Equals` の実装を提供しません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-111">The definition of `IEquatable<T>` doesn’t provide an implementation for `Equals`.</span></span> <span data-ttu-id="4c84f-112">インターフェイスは、署名のみを定義します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-112">The interface defines only the signature.</span></span> <span data-ttu-id="4c84f-113">つまり、C# のインターフェイスは、すべてのメソッドが抽象的である抽象クラスに似ています。</span><span class="sxs-lookup"><span data-stu-id="4c84f-113">In that way, an interface in C# is similar to an abstract class in which all the methods are abstract.</span></span> <span data-ttu-id="4c84f-114">クラスまたは構造体は複数のインターフェイスを実装できます。ただし、クラスが継承できるのは、抽象的かどうかに関係なく、1 つのクラスのみです。</span><span class="sxs-lookup"><span data-stu-id="4c84f-114">However, a class or struct can implement multiple interfaces, but a class can inherit only a single class, abstract or not.</span></span> <span data-ttu-id="4c84f-115">したがって、インターフェイスを使用することにより、クラス内の複数のソースの動作を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-115">Therefore, by using interfaces, you can include behavior from multiple sources in a class.</span></span>  
  
 <span data-ttu-id="4c84f-116">抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c84f-116">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="4c84f-117">インターフェイスには、メソッド、プロパティ、イベント、インデクサー、またはこれらの 4 種類のメンバーの任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-117">Interfaces can contain methods, properties, events, indexers, or any combination of those four member types.</span></span> <span data-ttu-id="4c84f-118">例へのリンクについては、「[関連項目](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c84f-118">For links to examples, see [Related Sections](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections).</span></span> <span data-ttu-id="4c84f-119">インターフェイスには、定数、フィールド、演算子、インスタンス コンストラクター、ファイナライザー、または型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-119">An interface can't contain constants, fields, operators, instance constructors, finalizers, or types.</span></span> <span data-ttu-id="4c84f-120">インターフェイスのメンバーは、自動的にパブリックに設定され、アクセス修飾子を含むことはできません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-120">Interface members are automatically public, and they can't include any access modifiers.</span></span> <span data-ttu-id="4c84f-121">メンバーを [static](../../../csharp/language-reference/keywords/static.md) として宣言することもできません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-121">Members also can't be [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
 <span data-ttu-id="4c84f-122">インターフェイスのメンバーを実装するには、実装するクラスの対応するメンバーがパブリックかつ非静的であり、インターフェイスのメンバーと同じ名前および署名を持つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-122">To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.</span></span>  
  
 <span data-ttu-id="4c84f-123">クラスまたは構造体でインターフェイスを実装するときは、インターフェイスで定義されているすべてのメンバーの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-123">When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface defines.</span></span> <span data-ttu-id="4c84f-124">インターフェイス自体は、基本クラスの機能を継承できるようにクラスまたは構造体が継承できる機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-124">The interface itself provides no functionality that a class or struct can inherit in the way that it can inherit base class functionality.</span></span> <span data-ttu-id="4c84f-125">ただし、基本クラスでインターフェイスが実装される場合、その基本クラスから派生するすべてのクラスはその実装を継承します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-125">However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.</span></span>  
  
 <span data-ttu-id="4c84f-126">IEquatable<T\> インターフェイスの実装例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-126">The following example shows an implementation of the IEquatable<T\> interface.</span></span> <span data-ttu-id="4c84f-127">実装するクラスの `Car` は、<xref:System.IEquatable%601.Equals%2A> メソッドの実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-127">The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.</span></span>  
  
 <span data-ttu-id="4c84f-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c84f-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="4c84f-129">クラスのプロパティとインデクサーでは、インターフェイスに定義されているプロパティまたはインデクサーの追加のアクセサーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-129">Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface.</span></span> <span data-ttu-id="4c84f-130">たとえば、インターフェイスで [get](../../../csharp/language-reference/keywords/get.md) アクセサーを持つプロパティを宣言するとします。</span><span class="sxs-lookup"><span data-stu-id="4c84f-130">For example, an interface might declare a property that has a [get](../../../csharp/language-reference/keywords/get.md) accessor.</span></span> <span data-ttu-id="4c84f-131">このインターフェイスを実装するクラスでは、`get` アクセサーと [set](../../../csharp/language-reference/keywords/set.md) アクセサーの両方を持つ同じプロパティを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-131">The class that implements the interface can declare the same property with both a `get` and [set](../../../csharp/language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="4c84f-132">ただし、プロパティまたはインデクサーで明示的な実装を使用する場合は、これらのアクセサーが一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-132">However, if the property or indexer uses explicit implementation, the accessors must match.</span></span> <span data-ttu-id="4c84f-133">明示的な実装の詳細については、「[明示的なインターフェイス実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」および「[インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c84f-133">For more information about explicit implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) and [Interface Properties](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).</span></span>  
  
 <span data-ttu-id="4c84f-134">インターフェイスは、他のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-134">Interfaces can implement other interfaces.</span></span> <span data-ttu-id="4c84f-135">クラスは、継承する基底クラスまたは他のインターフェイスが実装するインターフェイスを介して、インターフェイスを複数回含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-135">A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces implement.</span></span> <span data-ttu-id="4c84f-136">ただし、クラスでインターフェイスの実装を提供できるのは 1 回のみであり、それもクラスでクラスの定義の一部としてインターフェイスを宣言する場合 (`class ClassName : InterfaceName`) に限られます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-136">However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`).</span></span> <span data-ttu-id="4c84f-137">インターフェイスを実装する基本クラスを継承することによってインターフェイスを継承する場合、基本クラスは、そのインターフェイスのメンバーの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-137">If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface.</span></span> <span data-ttu-id="4c84f-138">ただし、派生クラスでは、継承された実装を使用する代わりに、インターフェイスのメンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-138">However, the derived class can reimplement the interface members instead of using the inherited implementation.</span></span>  
  
 <span data-ttu-id="4c84f-139">また、基本クラスでは、仮想メンバーを使用して、インターフェイスのメンバーを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-139">A base class can also implement interface members by using virtual members.</span></span> <span data-ttu-id="4c84f-140">その場合、派生クラスでは、仮想メンバーをオーバーライドすることでインターフェイスの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-140">In that case, a derived class can change the interface behavior by overriding the virtual members.</span></span> <span data-ttu-id="4c84f-141">仮想メンバーの詳細については、「[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c84f-141">For more information about virtual members, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="interfaces-summary"></a><span data-ttu-id="4c84f-142">インターフェイスの概要</span><span class="sxs-lookup"><span data-stu-id="4c84f-142">Interfaces Summary</span></span>  
 <span data-ttu-id="4c84f-143">インターフェイスは、次の特性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-143">An interface has the following properties:</span></span>  
  
-   <span data-ttu-id="4c84f-144">インターフェイスは、抽象基本クラスに似ています。</span><span class="sxs-lookup"><span data-stu-id="4c84f-144">An interface is like an abstract base class.</span></span> <span data-ttu-id="4c84f-145">インターフェイスを実装するすべてのクラスまたは構造体では、そのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c84f-145">Any class or struct that implements the interface must implement all its members.</span></span>  
  
-   <span data-ttu-id="4c84f-146">インターフェイスを直接インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-146">An interface can't be instantiated directly.</span></span> <span data-ttu-id="4c84f-147">そのメンバーは、インターフェイスを実装する任意のクラスまたは構造体によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-147">Its members are implemented by any class or struct that implements the interface.</span></span>  
  
-   <span data-ttu-id="4c84f-148">インターフェイスには、イベント、インデクサー、メソッド、およびプロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-148">Interfaces can contain events, indexers, methods, and properties.</span></span>  
  
-   <span data-ttu-id="4c84f-149">インターフェイスには、メソッドの実装は含まれません。</span><span class="sxs-lookup"><span data-stu-id="4c84f-149">Interfaces contain no implementation of methods.</span></span>  
  
-   <span data-ttu-id="4c84f-150">クラスまたは構造体は、複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-150">A class or struct can implement multiple interfaces.</span></span> <span data-ttu-id="4c84f-151">クラスは、基本クラスを継承する一方で、1 つまたは複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="4c84f-151">A class can inherit a base class and also implement one or more interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c84f-152">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c84f-152">In This Section</span></span>  
 [<span data-ttu-id="4c84f-153">明示的なインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="4c84f-153">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 <span data-ttu-id="4c84f-154">インターフェイスに固有のクラス メンバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-154">Explains how to create a class member that’s specific to an interface.</span></span>  
  
 [<span data-ttu-id="4c84f-155">方法: インターフェイス メンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="4c84f-155">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 <span data-ttu-id="4c84f-156">インターフェイスのメンバーを明示的に実装する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-156">Provides an example of how to explicitly implement members of interfaces.</span></span>  
  
 [<span data-ttu-id="4c84f-157">方法: 2 つのインターフェイスのメンバーを明示的に実装する</span><span class="sxs-lookup"><span data-stu-id="4c84f-157">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 <span data-ttu-id="4c84f-158">継承を持つインターフェイスのメンバーを明示的に実装する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="4c84f-158">Provides an example of how to explicitly implement members of interfaces with inheritance.</span></span>  
  
##  <span data-ttu-id="4c84f-159"><a name="BKMK_RelatedSections"></a>関連項目</span><span class="sxs-lookup"><span data-stu-id="4c84f-159"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="4c84f-160">インターフェイスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="4c84f-160">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="4c84f-161">インターフェイスのインデクサー</span><span class="sxs-lookup"><span data-stu-id="4c84f-161">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="4c84f-162">方法: インターフェイス イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="4c84f-162">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="4c84f-163">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="4c84f-163">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [<span data-ttu-id="4c84f-164">継承</span><span class="sxs-lookup"><span data-stu-id="4c84f-164">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [<span data-ttu-id="4c84f-165">メソッド</span><span class="sxs-lookup"><span data-stu-id="4c84f-165">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="4c84f-166">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="4c84f-166">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [<span data-ttu-id="4c84f-167">抽象クラスとシール クラス、およびクラス メンバー</span><span class="sxs-lookup"><span data-stu-id="4c84f-167">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [<span data-ttu-id="4c84f-168">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4c84f-168">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [<span data-ttu-id="4c84f-169">イベント</span><span class="sxs-lookup"><span data-stu-id="4c84f-169">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
-   [<span data-ttu-id="4c84f-170">インデクサー</span><span class="sxs-lookup"><span data-stu-id="4c84f-170">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="4c84f-171">参考書籍の該当する章</span><span class="sxs-lookup"><span data-stu-id="4c84f-171">Featured Book Chapter</span></span>  
 <span data-ttu-id="4c84f-172">「[Learning C# 3.0: Master the Fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)」の「[Interfaces (インターフェイス)](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx)」</span><span class="sxs-lookup"><span data-stu-id="4c84f-172">[Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c84f-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c84f-173">See Also</span></span>  
 <span data-ttu-id="4c84f-174">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c84f-174">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4c84f-175">継承</span><span class="sxs-lookup"><span data-stu-id="4c84f-175">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

