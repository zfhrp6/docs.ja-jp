---
title: "クラス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
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
ms.openlocfilehash: eedb087f177b1bff6f4d4177cd56ac4cca016490
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="4a67e-102">クラス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4a67e-102">Classes (C# Programming Guide)</span></span>
<span data-ttu-id="4a67e-103">*クラス*とは、他の型、メソッド、およびイベントの変数をまとめてグループ化することで独自のカスタム型を作成できる構成要素です。</span><span class="sxs-lookup"><span data-stu-id="4a67e-103">A *class* is a construct that enables you to create your own custom types by grouping together variables of other types, methods and events.</span></span> <span data-ttu-id="4a67e-104">クラスは設計図に似ています。</span><span class="sxs-lookup"><span data-stu-id="4a67e-104">A class is like a blueprint.</span></span> <span data-ttu-id="4a67e-105">型の動作とデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-105">It defines the data and behavior of a type.</span></span> <span data-ttu-id="4a67e-106">クラスが静的として宣言されていない場合、クライアント コードでは、*オブジェクト*または*インスタンス*を作成して変数に割り当てることでクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-106">If the class is not declared as static, client code can use it by creating *objects* or *instances* which are assigned to a variable.</span></span> <span data-ttu-id="4a67e-107">変数は、その変数への参照がすべてスコープ外になるまで、メモリ内に保持されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-107">The variable remains in memory until all references to it go out of scope.</span></span> <span data-ttu-id="4a67e-108">すべてスコープ外になったとき、CLR により、ガベージ コレクションの対象となるようにマークされます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-108">At that time, the CLR marks it as eligible for garbage collection.</span></span> <span data-ttu-id="4a67e-109">クラスが[静的](../../../csharp/language-reference/keywords/static.md)として宣言されている場合、メモリ内には 1 つのコピーだけが存在し、クライアント コードは*インスタンス変数*ではなくクラス自体を介してそのコピーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4a67e-109">If the class is declared as [static](../../../csharp/language-reference/keywords/static.md), then only one copy exists in memory and client code can only access it through the class itself, not an *instance variable*.</span></span> <span data-ttu-id="4a67e-110">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-110">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="4a67e-111">構造体とは異なり、クラスは、オブジェクト指向プログラミングの基本的な特性である*継承*をサポートします。</span><span class="sxs-lookup"><span data-stu-id="4a67e-111">Unlike structs, classes support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="4a67e-112">詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-112">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="4a67e-113">クラスの宣言</span><span class="sxs-lookup"><span data-stu-id="4a67e-113">Declaring Classes</span></span>  
 <span data-ttu-id="4a67e-114">クラスは、次の例に示すように、[class](../../../csharp/language-reference/keywords/class.md) キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-114">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword, as shown in the following example:</span></span>  
  
 <span data-ttu-id="4a67e-115">[!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-115">[!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]</span></span>  
  
 <span data-ttu-id="4a67e-116">`class` キーワードは、アクセス レベルの後に配置します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-116">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="4a67e-117">この例では、[public](../../../csharp/language-reference/keywords/public.md) が使用されているため、だれもがこのクラスからオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-117">Because [public](../../../csharp/language-reference/keywords/public.md) is used in this case, anyone can create objects from this class.</span></span> <span data-ttu-id="4a67e-118">`class` キーワードの後にクラスの名前を記述します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-118">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="4a67e-119">定義の残りの部分がクラス本体で、そこで動作とデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-119">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="4a67e-120">クラスのフィールド、プロパティ、メソッド、およびイベントは*クラス メンバー*と総称されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-120">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="4a67e-121">オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4a67e-121">Creating Objects</span></span>  
 <span data-ttu-id="4a67e-122">クラスとオブジェクトは、同義的に使用されることがありますが、これらは異なるものです。</span><span class="sxs-lookup"><span data-stu-id="4a67e-122">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="4a67e-123">クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。</span><span class="sxs-lookup"><span data-stu-id="4a67e-123">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="4a67e-124">オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="4a67e-124">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="4a67e-125">オブジェクトを作成するには、次のように、[new](../../../csharp/language-reference/keywords/new.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-125">Objects can be created by using the [new](../../../csharp/language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  
  
 <span data-ttu-id="4a67e-126">[!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-126">[!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]</span></span>  
  
 <span data-ttu-id="4a67e-127">クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-127">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="4a67e-128">前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。</span><span class="sxs-lookup"><span data-stu-id="4a67e-128">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="4a67e-129">この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。</span><span class="sxs-lookup"><span data-stu-id="4a67e-129">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="4a67e-130">実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-130">In fact, you can create an object reference without creating an object at all:</span></span>  
  
 <span data-ttu-id="4a67e-131">[!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-131">[!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]</span></span>  
  
 <span data-ttu-id="4a67e-132">上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。</span><span class="sxs-lookup"><span data-stu-id="4a67e-132">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="4a67e-133">ただし、新しいオブジェクトを作成するか、既存のオブジェクトに割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-133">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  
  
 <span data-ttu-id="4a67e-134">[!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-134">[!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]</span></span>  
  
 <span data-ttu-id="4a67e-135">上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-135">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="4a67e-136">そのため、`object3` を通じて行われたオブジェクトの変更は、その後、`object4`を使用する際にも反映されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-136">Therefore, any changes to the object made through `object3` will be reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="4a67e-137">これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="4a67e-137">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="4a67e-138">クラスの継承</span><span class="sxs-lookup"><span data-stu-id="4a67e-138">Class Inheritance</span></span>  
 <span data-ttu-id="4a67e-139">継承は、*派生*を使用して行われます。派生とは、データの動作の継承元である*基底クラス*を使用してクラスを宣言することを意味します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-139">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="4a67e-140">基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4a67e-140">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  
  
 <span data-ttu-id="4a67e-141">[!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-141">[!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]</span></span>  
  
 <span data-ttu-id="4a67e-142">クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-142">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span>  
  
 <span data-ttu-id="4a67e-143">C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。</span><span class="sxs-lookup"><span data-stu-id="4a67e-143">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="4a67e-144">ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。</span><span class="sxs-lookup"><span data-stu-id="4a67e-144">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="4a67e-145">さらに、クラスは複数のインターフェイスを直接実装できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-145">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="4a67e-146">詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-146">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="4a67e-147">クラスは[抽象](../../../csharp/language-reference/keywords/abstract.md)としても宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-147">A class can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="4a67e-148">抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4a67e-148">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="4a67e-149">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="4a67e-149">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="4a67e-150">抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a67e-150">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="4a67e-151">これとは対照的に、[シール](../../../csharp/language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="4a67e-151">By contrast, a [sealed](../../../csharp/language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="4a67e-152">詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-152">For more information, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="4a67e-153">クラス定義は、別々のソース ファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-153">Class definitions can be split between different source files.</span></span> <span data-ttu-id="4a67e-154">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-154">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="4a67e-155">説明</span><span class="sxs-lookup"><span data-stu-id="4a67e-155">Description</span></span>  
 <span data-ttu-id="4a67e-156">次の例では、フィールド、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="4a67e-156">In the following example, a public class that contains a single field, a method, and a special method called a constructor is defined.</span></span> <span data-ttu-id="4a67e-157">詳細については、「[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a67e-157">For more information, see [Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span> <span data-ttu-id="4a67e-158">このクラスは、`new` キーワードによってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="4a67e-158">The class is then instantiated with the `new` keyword.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a67e-159">例</span><span class="sxs-lookup"><span data-stu-id="4a67e-159">Example</span></span>  
 <span data-ttu-id="4a67e-160">[!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="4a67e-160">[!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4a67e-161">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4a67e-161">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4a67e-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a67e-162">See Also</span></span>  
 <span data-ttu-id="4a67e-163">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-163">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4a67e-164">[オブジェクト指向プログラミング](../concepts/object-oriented-programming.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-164">[Object-Oriented Programming](../concepts/object-oriented-programming.md) </span></span>  
 <span data-ttu-id="4a67e-165">[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-165">[Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span></span>  
 <span data-ttu-id="4a67e-166">[メンバー](../../../csharp/programming-guide/classes-and-structs/members.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-166">[Members](../../../csharp/programming-guide/classes-and-structs/members.md) </span></span>  
 <span data-ttu-id="4a67e-167">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-167">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="4a67e-168">[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-168">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="4a67e-169">[ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="4a67e-169">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 [<span data-ttu-id="4a67e-170">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4a67e-170">Objects</span></span>](../../../csharp/programming-guide/classes-and-structs/objects.md)

