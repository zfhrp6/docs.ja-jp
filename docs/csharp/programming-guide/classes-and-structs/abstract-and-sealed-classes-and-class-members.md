---
title: 抽象クラスとシール クラス、およびクラス メンバー (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: aa7c951acadd2e7b60f6da17cd7bf357fbd02d95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="ac62b-102">抽象クラスとシール クラス、およびクラス メンバー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ac62b-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="ac62b-103">[abstract](../../../csharp/language-reference/keywords/abstract.md) キーワードを使用すると、派生クラスで実装する必要のある不完全な[クラス](../../../csharp/language-reference/keywords/class.md) メンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="ac62b-104">また、[sealed](../../../csharp/language-reference/keywords/sealed.md) キーワードを使用すると、既に [virtual](../../../csharp/language-reference/keywords/virtual.md) とマークされているクラスや特定のクラス メンバーを継承しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="ac62b-105">抽象クラスと抽象クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="ac62b-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="ac62b-106">クラス定義の前にキーワード `abstract` を指定することで、クラスを抽象として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="ac62b-107">例:</span><span class="sxs-lookup"><span data-stu-id="ac62b-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 <span data-ttu-id="ac62b-108">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="ac62b-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="ac62b-109">抽象クラスの目的は、複数の派生クラスで共有できる基底クラスの共通の定義を提供することです。</span><span class="sxs-lookup"><span data-stu-id="ac62b-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="ac62b-110">たとえば、クラス ライブラリでは、その多くの関数のパラメーターとして使用される抽象クラスを定義できます。このライブラリを使用する場合は、派生クラスを作成してクラスの独自の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac62b-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="ac62b-111">抽象クラスでは、抽象メソッドも定義できます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="ac62b-112">抽象メソッドを定義するには、メソッドの戻り値の型の前に `abstract` キーワードを記述します。</span><span class="sxs-lookup"><span data-stu-id="ac62b-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="ac62b-113">例:</span><span class="sxs-lookup"><span data-stu-id="ac62b-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 <span data-ttu-id="ac62b-114">抽象メソッドには実装がないので、メソッド定義の後に、通常のメソッド ブロックの代わりにセミコロン (;) を配置します。</span><span class="sxs-lookup"><span data-stu-id="ac62b-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="ac62b-115">抽象クラスの派生クラスでは、すべての抽象メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac62b-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="ac62b-116">抽象クラスが基底クラスから仮想メソッドを継承した場合は、この抽象クラスでは抽象メソッドで仮想メソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="ac62b-117">例:</span><span class="sxs-lookup"><span data-stu-id="ac62b-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 <span data-ttu-id="ac62b-118">`virtual` メソッドが `abstract` として宣言されている場合、そのメソッドは、その抽象クラスを継承するどのクラスでも仮想になります。</span><span class="sxs-lookup"><span data-stu-id="ac62b-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="ac62b-119">抽象メソッドを継承するクラスでは、そのメソッドの元の実装にアクセスできません。上の例では、クラス F の `DoWork` は、クラス D の `DoWork` を呼び出すことができません。このようにして抽象クラスは、派生クラスに対し、仮想メソッドの新しいメソッド実装を強制的に提供させることができます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="ac62b-120">シール クラスとシール クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="ac62b-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="ac62b-121">クラス定義の前にキーワード `sealed` を指定することで、クラスを [sealed](../../../csharp/language-reference/keywords/sealed.md) として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-121">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="ac62b-122">例:</span><span class="sxs-lookup"><span data-stu-id="ac62b-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 <span data-ttu-id="ac62b-123">シール クラスは、基底クラスとして使用できません。</span><span class="sxs-lookup"><span data-stu-id="ac62b-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="ac62b-124">このため、シール クラスは抽象クラスになることもできません。</span><span class="sxs-lookup"><span data-stu-id="ac62b-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="ac62b-125">シール クラスにより、派生が防止されます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="ac62b-126">シール クラスは基底クラスとして使用できないので、実行時の最適化で、シール クラス メンバーを多少高速に呼び出すことができる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac62b-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="ac62b-127">基底クラスの仮想メンバーをオーバーライドしている派生クラスのメソッド、インデクサー、プロパティ、またはイベントでは、そのメンバーをシールとして宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ac62b-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="ac62b-128">これにより、その後の派生クラスでは、メンバーの仮想性が無効になります。</span><span class="sxs-lookup"><span data-stu-id="ac62b-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="ac62b-129">このように宣言するには、クラス メンバー宣言で [override](../../../csharp/language-reference/keywords/override.md) キーワードの前に `sealed` キーワードを配置します。</span><span class="sxs-lookup"><span data-stu-id="ac62b-129">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="ac62b-130">例:</span><span class="sxs-lookup"><span data-stu-id="ac62b-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ac62b-131">参照</span><span class="sxs-lookup"><span data-stu-id="ac62b-131">See Also</span></span>  
 [<span data-ttu-id="ac62b-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ac62b-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ac62b-133">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="ac62b-133">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ac62b-134">継承</span><span class="sxs-lookup"><span data-stu-id="ac62b-134">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="ac62b-135">メソッド</span><span class="sxs-lookup"><span data-stu-id="ac62b-135">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="ac62b-136">フィールド</span><span class="sxs-lookup"><span data-stu-id="ac62b-136">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [<span data-ttu-id="ac62b-137">方法: 抽象プロパティを定義する</span><span class="sxs-lookup"><span data-stu-id="ac62b-137">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
