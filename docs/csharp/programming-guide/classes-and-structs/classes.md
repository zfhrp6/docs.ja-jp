---
title: クラス (C# プログラミング ガイド)
description: クラスの型と、クラスの型を作成する方法について説明します
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 688736aa8556719789b02d7db25858f442b4309e
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312093"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="c9b81-103">クラス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c9b81-103">Classes (C# Programming Guide)</span></span>
<span data-ttu-id="c9b81-104">*クラス*とは、他の型、メソッド、およびイベントの変数をまとめてグループ化することで独自のカスタム型を作成できる構成要素です。</span><span class="sxs-lookup"><span data-stu-id="c9b81-104">A *class* is a construct that enables you to create your own custom types by grouping together variables of other types, methods and events.</span></span> <span data-ttu-id="c9b81-105">クラスは設計図に似ています。</span><span class="sxs-lookup"><span data-stu-id="c9b81-105">A class is like a blueprint.</span></span> <span data-ttu-id="c9b81-106">型の動作とデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-106">It defines the data and behavior of a type.</span></span> <span data-ttu-id="c9b81-107">クラスが static と宣言されていない場合、クライアント コードはそのクラスの "*インスタンス*" を作成できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-107">If the class is not declared as static, client code can create *instances* of it.</span></span> <span data-ttu-id="c9b81-108">これらのインスタンスは、変数に割り当てられる "*オブジェクト*" です。</span><span class="sxs-lookup"><span data-stu-id="c9b81-108">These instances are *objects* which are assigned to a variable.</span></span> <span data-ttu-id="c9b81-109">クラスのインスタンスは、その変数への参照がすべてスコープ外になるまで、メモリ内に保持されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-109">The instance of a class remains in memory until all references to it go out of scope.</span></span> <span data-ttu-id="c9b81-110">すべてスコープ外になったとき、CLR により、ガベージ コレクションの対象となるようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-110">At that time, the CLR marks it as eligible for garbage collection.</span></span> <span data-ttu-id="c9b81-111">クラスが [static](../../../csharp/language-reference/keywords/static.md) として宣言されている場合は、インスタンスを作成できず、クライアント コードはクラス自体を介してのみクラスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-111">If the class is declared as [static](../../../csharp/language-reference/keywords/static.md), you cannot create instances, and client code can only access it through the class itself.</span></span> <span data-ttu-id="c9b81-112">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  

## <a name="reference-types"></a><span data-ttu-id="c9b81-113">参照型</span><span class="sxs-lookup"><span data-stu-id="c9b81-113">Reference types</span></span>  
<span data-ttu-id="c9b81-114">[class](../../../csharp/language-reference/keywords/class.md) として定義された型は、*参照型*です。</span><span class="sxs-lookup"><span data-stu-id="c9b81-114">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="c9b81-115">実行時には、参照型の変数を宣言すると、[new](../../../csharp/language-reference/keywords/new.md) 演算子を使用してクラスのインスタンスを明示的に作成するまで、変数には値 [null](../../../csharp/language-reference/keywords/null.md) が格納されています。または、次の例に示すように、別の場所で作成されたオブジェクトを代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-115">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/keywords/new.md) operator, or assign it an object that has been created elsewhere, as shown in the following example:</span></span>

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

<span data-ttu-id="c9b81-116">オブジェクトが作成されると、マネージ ヒープ上でメモリが割り当てられ、変数にはそのオブジェクトの場所への参照のみが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-116">When the object is created, the memory is allocated on the managed heap, and the variable holds only a reference to the location of the object.</span></span> <span data-ttu-id="c9b81-117">マネージ ヒープを使用する型では、メモリの割り当て時と、CLR の自動メモリ管理機能 (*ガベージ コレクション*) による再要求時の両方についてオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-117">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="c9b81-118">しかし、ガベージ コレクションも高度に最適化されるため、ほとんどのシナリオでは、パフォーマンス上の問題が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-118">However, garbage collection is also highly optimized, and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="c9b81-119">ガベージ コレクションの詳細については、「[自動メモリ管理とガベージ コレクション](../../../standard/garbage-collection/gc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-119">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="c9b81-120">クラスの宣言</span><span class="sxs-lookup"><span data-stu-id="c9b81-120">Declaring Classes</span></span>  
 <span data-ttu-id="c9b81-121">クラスは、次の例に示すように、[class](../../../csharp/language-reference/keywords/class.md) キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-121">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword, as shown in the following example:</span></span>

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="c9b81-122">`class` キーワードは、アクセス レベルの後に配置します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-122">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="c9b81-123">この例では、[public](../../../csharp/language-reference/keywords/public.md) が使用されているため、誰でもこのクラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-123">Because [public](../../../csharp/language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="c9b81-124">`class` キーワードの後にクラスの名前を記述します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-124">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="c9b81-125">定義の残りの部分がクラス本体で、そこで動作とデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-125">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="c9b81-126">クラスのフィールド、プロパティ、メソッド、およびイベントは*クラス メンバー*と総称されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-126">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="c9b81-127">オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c9b81-127">Creating Objects</span></span>  
 <span data-ttu-id="c9b81-128">クラスとオブジェクトは、同義的に使用されることがありますが、これらは異なるものです。</span><span class="sxs-lookup"><span data-stu-id="c9b81-128">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="c9b81-129">クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-129">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="c9b81-130">オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="c9b81-130">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="c9b81-131">オブジェクトを作成するには、次のように、[new](../../../csharp/language-reference/keywords/new.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-131">Objects can be created by using the [new](../../../csharp/language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 <span data-ttu-id="c9b81-132">クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-132">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="c9b81-133">前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。</span><span class="sxs-lookup"><span data-stu-id="c9b81-133">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="c9b81-134">この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-134">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="c9b81-135">実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-135">In fact, you can create an object reference without creating an object at all:</span></span>  
  
  ```csharp
  Customer object2;
  ```
  
 <span data-ttu-id="c9b81-136">上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。</span><span class="sxs-lookup"><span data-stu-id="c9b81-136">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="c9b81-137">ただし、新しいオブジェクトを作成するか、既存のオブジェクトに割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-137">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 <span data-ttu-id="c9b81-138">上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-138">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="c9b81-139">そのため、`object3` を通じて行われたオブジェクトの変更は、後で `object4` を使用するときに反映されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-139">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="c9b81-140">これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="c9b81-140">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="c9b81-141">クラスの継承</span><span class="sxs-lookup"><span data-stu-id="c9b81-141">Class Inheritance</span></span>  

 <span data-ttu-id="c9b81-142">クラスは、オブジェクト指向プログラミングの基本的な特性である "*継承*" を完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="c9b81-142">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="c9b81-143">クラスを作成するときは、[sealed](../../../csharp/language-reference/keywords/sealed.md) として定義されているものを除く、他のすべてのインターフェイスまたはクラスから継承できます。また、作成したクラスから他のクラスを継承し、クラスの仮想メソッドをオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-143">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

 <span data-ttu-id="c9b81-144">継承は、*派生*を使用して行われます。派生とは、データの動作の継承元である*基底クラス*を使用してクラスを宣言することを意味します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-144">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="c9b81-145">基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c9b81-145">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 <span data-ttu-id="c9b81-146">クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-146">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="c9b81-147">詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-147">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>
  
 <span data-ttu-id="c9b81-148">C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-148">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="c9b81-149">ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。</span><span class="sxs-lookup"><span data-stu-id="c9b81-149">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="c9b81-150">さらに、クラスは複数のインターフェイスを直接実装できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-150">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="c9b81-151">詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-151">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="c9b81-152">クラスは[抽象](../../../csharp/language-reference/keywords/abstract.md)としても宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-152">A class can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="c9b81-153">抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c9b81-153">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="c9b81-154">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-154">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="c9b81-155">抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9b81-155">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="c9b81-156">これとは対照的に、[シール](../../../csharp/language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="c9b81-156">By contrast, a [sealed](../../../csharp/language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="c9b81-157">詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-157">For more information, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="c9b81-158">クラス定義は、別々のソース ファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-158">Class definitions can be split between different source files.</span></span> <span data-ttu-id="c9b81-159">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-159">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b81-160">例</span><span class="sxs-lookup"><span data-stu-id="c9b81-160">Example</span></span>  
 <span data-ttu-id="c9b81-161">次の例では、[自動実装プロパティ](auto-implemented-properties.md)、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="c9b81-161">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="c9b81-162">詳しくは、[プロパティ](properties.md)、[メソッド](methods.md)、および[コンス トラクター](constructors.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9b81-162">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="c9b81-163">このクラスのインスタンスは、`new` キーワードによってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="c9b81-163">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="c9b81-164">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c9b81-164">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c9b81-165">参照</span><span class="sxs-lookup"><span data-stu-id="c9b81-165">See Also</span></span>  
 [<span data-ttu-id="c9b81-166">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c9b81-166">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c9b81-167">オブジェクト指向プログラミング</span><span class="sxs-lookup"><span data-stu-id="c9b81-167">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)  
 [<span data-ttu-id="c9b81-168">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="c9b81-168">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="c9b81-169">メンバー</span><span class="sxs-lookup"><span data-stu-id="c9b81-169">Members</span></span>](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [<span data-ttu-id="c9b81-170">メソッド</span><span class="sxs-lookup"><span data-stu-id="c9b81-170">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="c9b81-171">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="c9b81-171">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="c9b81-172">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="c9b81-172">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="c9b81-173">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c9b81-173">Objects</span></span>](../../../csharp/programming-guide/classes-and-structs/objects.md)
