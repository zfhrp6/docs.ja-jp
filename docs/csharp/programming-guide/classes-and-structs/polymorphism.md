---
title: "ポリモーフィズム (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
caps.latest.revision: 31
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
ms.openlocfilehash: c278a6a931154af97cab5b1ff33124dd31a3fa2e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="polymorphism-c-programming-guide"></a><span data-ttu-id="26143-102">ポリモーフィズム (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="26143-102">Polymorphism (C# Programming Guide)</span></span>
<span data-ttu-id="26143-103">ポリモーフィズムは、カプセル化と継承に次ぐ、オブジェクト指向プログラミングの第 3 の柱と言われることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="26143-103">Polymorphism is often referred to as the third pillar of object-oriented programming, after encapsulation and inheritance.</span></span> <span data-ttu-id="26143-104">ポリモーフィズムは、ギリシャ語で "多形" を意味し、次の 2 つの側面を持っています。</span><span class="sxs-lookup"><span data-stu-id="26143-104">Polymorphism is a Greek word that means "many-shaped" and it has two distinct aspects:</span></span>  
  
-   <span data-ttu-id="26143-105">メソッド パラメーター、コレクション、配列などに渡された派生クラスのオブジェクトは、実行時に基底クラスのオブジェクトとして扱われることがあります。</span><span class="sxs-lookup"><span data-stu-id="26143-105">At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays.</span></span> <span data-ttu-id="26143-106">この場合、オブジェクトの宣言された型は、その実行時の型と同じではなくなります。</span><span class="sxs-lookup"><span data-stu-id="26143-106">When this occurs, the object's declared type is no longer identical to its run-time type.</span></span>  
  
-   <span data-ttu-id="26143-107">基底クラスでは、[virtual](../../../csharp/language-reference/keywords/virtual.md) *メソッド*を定義して実行できます。派生クラスでそれを[オーバーライド](../../../csharp/language-reference/keywords/override.md)すると、独自の定義と実装を提供できます。</span><span class="sxs-lookup"><span data-stu-id="26143-107">Base classes may define and implement [virtual](../../../csharp/language-reference/keywords/virtual.md) *methods*, and derived classes can [override](../../../csharp/language-reference/keywords/override.md) them, which means they provide their own definition and implementation.</span></span> <span data-ttu-id="26143-108">実行時には、クライアント コードがメソッドを呼び出したとき、CLR によってオブジェクトの実行時の型が検索され、仮想メソッドのオーバーライドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="26143-108">At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method.</span></span> <span data-ttu-id="26143-109">このように、ソース コード内で基底クラスのメソッドを呼び出して、派生クラスのメソッドが実行されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="26143-109">Thus in your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.</span></span>  
  
 <span data-ttu-id="26143-110">仮想メソッドを使用すると、関連するオブジェクトのグループを同一の方法で扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="26143-110">Virtual methods enable you to work with groups of related objects in a uniform way.</span></span> <span data-ttu-id="26143-111">たとえば、描画サーフェイスにさまざまな種類の図形を作成できる描画アプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="26143-111">For example, suppose you have a drawing application that enables a user to create various kinds of shapes on a drawing surface.</span></span> <span data-ttu-id="26143-112">コンパイル時には、ユーザーがどのような種類の図形を作成するかわかりません。</span><span class="sxs-lookup"><span data-stu-id="26143-112">You do not know at compile time which specific types of shapes the user will create.</span></span> <span data-ttu-id="26143-113">しかし、アプリケーションでは、作成されたさまざまな種類の図形を追跡し、ユーザーのマウス操作に応じて更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26143-113">However, the application has to keep track of all the various types of shapes that are created, and it has to update them in response to user mouse actions.</span></span> <span data-ttu-id="26143-114">ポリモーフィズムを使用すると、2 つの基本的な手順でこの問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="26143-114">You can use polymorphism to solve this problem in two basic steps:</span></span>  
  
1.  <span data-ttu-id="26143-115">各図形クラスが共通の基底クラスから派生するようなクラス階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="26143-115">Create a class hierarchy in which each specific shape class derives from a common base class.</span></span>  
  
2.  <span data-ttu-id="26143-116">仮想メソッドを使用して、基底クラスの 1 つのメソッドを呼び出すことで、派生クラスの適切なメソッドが呼び出されるようにします。</span><span class="sxs-lookup"><span data-stu-id="26143-116">Use a virtual method to invoke the appropriate method on any derived class through a single call to the base class method.</span></span>  
  
 <span data-ttu-id="26143-117">まず、`Shape` という基底クラスと、`Rectangle`、`Circle`、`Triangle` などの派生クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="26143-117">First, create a base class called `Shape`, and derived classes such as `Rectangle`, `Circle`, and `Triangle`.</span></span> <span data-ttu-id="26143-118">`Shape` クラスで `Draw` という仮想メソッドを定義し、各派生クラスでそれをオーバーライドして、そのクラスが表す特定の図形を描画します。</span><span class="sxs-lookup"><span data-stu-id="26143-118">Give the `Shape` class a virtual method called `Draw`, and override it in each derived class to draw the particular shape that the class represents.</span></span> <span data-ttu-id="26143-119">`List<Shape>` オブジェクトを作成し、Circle、Triangle、および Rectangle を追加します。</span><span class="sxs-lookup"><span data-stu-id="26143-119">Create a `List<Shape>` object and add a Circle, Triangle and Rectangle to it.</span></span> <span data-ttu-id="26143-120">描画サーフェイスを更新するには、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ループを使用してリストを反復処理し、リスト内の各 `Shape` オブジェクトの `Draw` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="26143-120">To update the drawing surface, use a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loop to iterate through the list and call the `Draw` method on each `Shape` object in the list.</span></span> <span data-ttu-id="26143-121">リスト内の各オブジェクトの宣言された型は `Shape` ですが、呼び出されるのは実行時の型 (それぞれの派生クラスでオーバーライドされたメソッド) になります。</span><span class="sxs-lookup"><span data-stu-id="26143-121">Even though each object in the list has a declared type of `Shape`, it is the run-time type (the overridden version of the method in each derived class) that will be invoked.</span></span>  
  
 <span data-ttu-id="26143-122">[!code-cs[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-122">[!code-cs[csProgGuideInheritance#50](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_1.cs)]</span></span>  
  
 <span data-ttu-id="26143-123">C# では、すべての型がポリモーフィックです。これは、ユーザー定義型を含むすべての型が <xref:System.Object> から派生するためです。</span><span class="sxs-lookup"><span data-stu-id="26143-123">In C#, every type is polymorphic because all types, including user-defined types, inherit from <xref:System.Object>.</span></span>  
  
## <a name="polymorphism-overview"></a><span data-ttu-id="26143-124">ポリモーフィズムの概要</span><span class="sxs-lookup"><span data-stu-id="26143-124">Polymorphism Overview</span></span>  
  
### <a name="virtual-members"></a><span data-ttu-id="26143-125">仮想メンバー</span><span class="sxs-lookup"><span data-stu-id="26143-125">Virtual Members</span></span>  
 <span data-ttu-id="26143-126">基底クラスから派生クラスを継承すると、派生クラスは、基底クラスのすべてのメソッド、フィールド、プロパティ、およびイベントを継承します。</span><span class="sxs-lookup"><span data-stu-id="26143-126">When a derived class inherits from a base class, it gains all the methods, fields, properties and events of the base class.</span></span> <span data-ttu-id="26143-127">派生クラスの設計者は、次の点を選択できます。</span><span class="sxs-lookup"><span data-stu-id="26143-127">The designer of the derived class can choose whether to</span></span>  
  
-   <span data-ttu-id="26143-128">基底クラスの仮想メンバーをオーバーライドするかどうか</span><span class="sxs-lookup"><span data-stu-id="26143-128">override virtual members in the base class,</span></span>  
  
-   <span data-ttu-id="26143-129">最も近い基底クラスのメソッドを、オーバーライドせずに継承するかどうか</span><span class="sxs-lookup"><span data-stu-id="26143-129">inherit the closest base class method without overriding it</span></span>  
  
-   <span data-ttu-id="26143-130">これらのメンバーの仮想でない実装を新しく定義して、基底クラスの実装を隠ぺいするかどうか</span><span class="sxs-lookup"><span data-stu-id="26143-130">define new non-virtual implementation of those members that hide the base class implementations</span></span>  
  
 <span data-ttu-id="26143-131">派生クラスが基底クラスのメンバーをオーバーライドできるのは、基底クラスのメンバーが [virtual](../../../csharp/language-reference/keywords/virtual.md) または [abstract](../../../csharp/language-reference/keywords/abstract.md) として宣言されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="26143-131">A derived class can override a base class member only if the base class member is declared as [virtual](../../../csharp/language-reference/keywords/virtual.md) or [abstract](../../../csharp/language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="26143-132">派生メンバーでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用して、そのメソッドが仮想呼び出しに加わることを明示的に示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="26143-132">The derived member must use the [override](../../../csharp/language-reference/keywords/override.md) keyword to explicitly indicate that the method is intended to participate in virtual invocation.</span></span> <span data-ttu-id="26143-133">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-133">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-134">[!code-cs[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-134">[!code-cs[csProgGuideInheritance#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_2.cs)]</span></span>  
  
 <span data-ttu-id="26143-135">フィールドは仮想メンバーにできません。仮想メンバーにできるのは、メソッド、プロパティ、イベント、およびインデクサーに限られます。</span><span class="sxs-lookup"><span data-stu-id="26143-135">Fields cannot be virtual; only methods, properties, events and indexers can be virtual.</span></span> <span data-ttu-id="26143-136">派生クラスが仮想メンバーをオーバーライドすると、派生クラスのメンバーは、そのクラスのインスタンスが基底クラスのインスタンスとしてアクセスされるときでも呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="26143-136">When a derived class overrides a virtual member, that member is called even when an instance of that class is being accessed as an instance of the base class.</span></span> <span data-ttu-id="26143-137">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-137">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-138">[!code-cs[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-138">[!code-cs[csProgGuideInheritance#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_3.cs)]</span></span>  
  
 <span data-ttu-id="26143-139">仮想メソッドとプロパティを使用すると、派生クラスは、基底クラスのメソッドの実装を使用せずに基底クラスを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="26143-139">Virtual methods and properties enable derived classes to extend a base class without needing to use the base class implementation of a method.</span></span> <span data-ttu-id="26143-140">詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26143-140">For more information, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md).</span></span> <span data-ttu-id="26143-141">1 つまたは一連のメソッドを定義し、その実装を派生クラスに任せるもう 1 つの方法として、インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="26143-141">An interface provides another way to define a method or set of methods whose implementation is left to derived classes.</span></span> <span data-ttu-id="26143-142">詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26143-142">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
### <a name="hiding-base-class-members-with-new-members"></a><span data-ttu-id="26143-143">新しいメンバーによる基底クラスのメンバーの隠ぺい</span><span class="sxs-lookup"><span data-stu-id="26143-143">Hiding Base Class Members with New Members</span></span>  
 <span data-ttu-id="26143-144">派生メンバーに基底クラスのメンバーと同じ名前を付けながら、そのメンバーが仮想呼び出しに加わらないようにするには、[new](../../../csharp/language-reference/keywords/new.md) キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="26143-144">If you want your derived member to have the same name as a member in a base class, but you do not want it to participate in virtual invocation, you can use the [new](../../../csharp/language-reference/keywords/new.md) keyword.</span></span> <span data-ttu-id="26143-145">`new` キーワードは、置き換えられるクラス メンバーの戻り値の型の前に配置します。</span><span class="sxs-lookup"><span data-stu-id="26143-145">The `new` keyword is put before the return type of a class member that is being replaced.</span></span> <span data-ttu-id="26143-146">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-146">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-147">[!code-cs[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-147">[!code-cs[csProgGuideInheritance#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_4.cs)]</span></span>  
  
 <span data-ttu-id="26143-148">基底クラスのメンバーが隠ぺいされても、派生クラスのインスタンスを基底クラスのインスタンスにキャストすることで、クライアント コードから基底クラスのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="26143-148">Hidden base class members can still be accessed from client code by casting the instance of the derived class to an instance of the base class.</span></span> <span data-ttu-id="26143-149">例:</span><span class="sxs-lookup"><span data-stu-id="26143-149">For example:</span></span>  
  
 <span data-ttu-id="26143-150">[!code-cs[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-150">[!code-cs[csProgGuideInheritance#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_5.cs)]</span></span>  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a><span data-ttu-id="26143-151">派生クラスが仮想メンバーをオーバーライドしないようにする</span><span class="sxs-lookup"><span data-stu-id="26143-151">Preventing Derived Classes from Overriding Virtual Members</span></span>  
 <span data-ttu-id="26143-152">仮想メンバーは、それを最初に宣言したクラスとの間でどれほど多くのクラスが宣言されても、いつまでも仮想のままです。</span><span class="sxs-lookup"><span data-stu-id="26143-152">Virtual members remain virtual indefinitely, regardless of how many classes have been declared between the virtual member and the class that originally declared it.</span></span> <span data-ttu-id="26143-153">たとえば、クラス A が仮想メンバーを宣言し、クラス B がクラス A から派生し、クラス C がクラス B から派生した場合、クラス C は仮想メンバーを継承し、クラス B がその仮想メンバーのオーバーライドを宣言したかどうかに関係なく、そのメンバーをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="26143-153">If class A declares a virtual member, and class B derives from A, and class C derives from B, class C inherits the virtual member, and has the option to override it, regardless of whether class B declared an override for that member.</span></span> <span data-ttu-id="26143-154">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-154">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-155">[!code-cs[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-155">[!code-cs[csProgGuideInheritance#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_6.cs)]</span></span>  
  
 <span data-ttu-id="26143-156">派生クラスでは、オーバーライドを [sealed](../../../csharp/language-reference/keywords/sealed.md) として宣言することで仮想継承を中止できます。</span><span class="sxs-lookup"><span data-stu-id="26143-156">A derived class can stop virtual inheritance by declaring an override as [sealed](../../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="26143-157">この場合、クラス メンバーの宣言で、`sealed` キーワードの前に `override` キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26143-157">This requires putting the `sealed` keyword before the `override` keyword in the class member declaration.</span></span> <span data-ttu-id="26143-158">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-158">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-159">[!code-cs[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-159">[!code-cs[csProgGuideInheritance#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_7.cs)]</span></span>  
  
 <span data-ttu-id="26143-160">上の例では、`DoWork` メソッドは C から派生したどのクラスに対しても仮想メソッドではありません。C のインスタンスに対しては、B 型や A 型にキャストされた場合でも、依然として仮想メソッドです。シール メソッドは、次のコード例に示すように、`new` キーワードを使用して派生クラスに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="26143-160">In the previous example, the method `DoWork` is no longer virtual to any class derived from C. It is still virtual for instances of C, even if they are cast to type B or type A. Sealed methods can be replaced by derived classes by using the `new` keyword, as the following example shows:</span></span>  
  
 <span data-ttu-id="26143-161">[!code-cs[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-161">[!code-cs[csProgGuideInheritance#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_8.cs)]</span></span>  
  
 <span data-ttu-id="26143-162">このコード例では、`DoWork` が、D 型の変数を使用して D で呼び出されると、新しい `DoWork` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="26143-162">In this case, if `DoWork` is called on D using a variable of type D, the new `DoWork` is called.</span></span> <span data-ttu-id="26143-163">また、C 型、B 型、または A 型の変数を使用して D のインスタンスにアクセスした場合、`DoWork` への呼び出しは、仮想継承の規則に従って、クラス C の `DoWork` の実装に転送されます。</span><span class="sxs-lookup"><span data-stu-id="26143-163">If a variable of type C, B, or A is used to access an instance of D, a call to `DoWork` will follow the rules of virtual inheritance, routing those calls to the implementation of `DoWork` on class C.</span></span>  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a><span data-ttu-id="26143-164">派生クラスからの基底クラスの仮想メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="26143-164">Accessing Base Class Virtual Members from Derived Classes</span></span>  
 <span data-ttu-id="26143-165">メソッドやプロパティを置き換えたり、オーバーライドしたりした派生クラスでは、base キーワードを使用することで、基底クラスのメソッドやプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="26143-165">A derived class that has replaced or overridden a method or property can still access the method or property on the base class using the base keyword.</span></span> <span data-ttu-id="26143-166">次にコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="26143-166">The following code provides an example:</span></span>  
  
 <span data-ttu-id="26143-167">[!code-cs[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="26143-167">[!code-cs[csProgGuideInheritance#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/polymorphism_9.cs)]</span></span>  
  
 <span data-ttu-id="26143-168">詳細については、「[base](../../../csharp/language-reference/keywords/base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26143-168">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26143-169">仮想メンバーの場合、その固有の実装で `base` を使用して、その仮想メンバーの基底クラス実装を呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="26143-169">It is recommended that virtual members use `base` to call the base class implementation of that member in their own implementation.</span></span> <span data-ttu-id="26143-170">基底クラスの動作を実行できるようにすることで、派生クラスは、派生クラスに固有の動作を実装することに集中できます。</span><span class="sxs-lookup"><span data-stu-id="26143-170">Letting the base class behavior occur enables the derived class to concentrate on implementing behavior specific to the derived class.</span></span> <span data-ttu-id="26143-171">基底クラス実装を呼び出さない場合は、基底クラスの動作と互換性のある動作を派生クラスで実現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26143-171">If the base class implementation is not called, it is up to the derived class to make their behavior compatible with the behavior of the base class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="26143-172">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="26143-172">In This Section</span></span>  
  
-   [<span data-ttu-id="26143-173">Override キーワードと New キーワードによるバージョン管理</span><span class="sxs-lookup"><span data-stu-id="26143-173">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
  
-   [<span data-ttu-id="26143-174">Override キーワードと New キーワードを使用する場合について</span><span class="sxs-lookup"><span data-stu-id="26143-174">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)  
  
-   [<span data-ttu-id="26143-175">方法: ToString メソッドをオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="26143-175">How to: Override the ToString Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="26143-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="26143-176">See Also</span></span>  
 <span data-ttu-id="26143-177">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="26143-177">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="26143-178">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="26143-178">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="26143-179">[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="26143-179">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="26143-180">[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="26143-180">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="26143-181">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="26143-181">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="26143-182">[イベント](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="26143-182">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="26143-183">[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="26143-183">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="26143-184">[インデクサー](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="26143-184">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="26143-185">型</span><span class="sxs-lookup"><span data-stu-id="26143-185">Types</span></span>](../../../csharp/programming-guide/types/index.md)

