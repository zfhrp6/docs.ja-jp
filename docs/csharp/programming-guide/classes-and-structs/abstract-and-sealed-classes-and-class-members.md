---
title: "抽象クラスとシール クラス、およびクラス メンバー (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: 14
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
ms.openlocfilehash: 0788ea0778b3f8b846231fc2408938b2236314c9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="d9c02-102">抽象クラスとシール クラス、およびクラス メンバー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d9c02-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="d9c02-103">[abstract](../../../csharp/language-reference/keywords/abstract.md) キーワードを使用すると、派生クラスで実装する必要のある不完全な[クラス](../../../csharp/language-reference/keywords/class.md) メンバーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="d9c02-104">また、[sealed](../../../csharp/language-reference/keywords/sealed.md) キーワードを使用すると、既に [virtual](../../../csharp/language-reference/keywords/virtual.md) とマークされているクラスや特定のクラス メンバーを継承しないようにできます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="d9c02-105">抽象クラスと抽象クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="d9c02-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="d9c02-106">クラス定義の前にキーワード `abstract` を指定することで、クラスを抽象として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="d9c02-107">例:</span><span class="sxs-lookup"><span data-stu-id="d9c02-107">For example:</span></span>  
  
 <span data-ttu-id="d9c02-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-108">[!code-cs[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]</span></span>  
  
 <span data-ttu-id="d9c02-109">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="d9c02-109">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="d9c02-110">抽象クラスの目的は、複数の派生クラスで共有できる基底クラスの共通の定義を提供することです。</span><span class="sxs-lookup"><span data-stu-id="d9c02-110">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="d9c02-111">たとえば、クラス ライブラリでは、その多くの関数のパラメーターとして使用される抽象クラスを定義できます。このライブラリを使用する場合は、派生クラスを作成してクラスの独自の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9c02-111">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="d9c02-112">抽象クラスでは、抽象メソッドも定義できます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-112">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="d9c02-113">抽象メソッドを定義するには、メソッドの戻り値の型の前に `abstract` キーワードを記述します。</span><span class="sxs-lookup"><span data-stu-id="d9c02-113">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="d9c02-114">例:</span><span class="sxs-lookup"><span data-stu-id="d9c02-114">For example:</span></span>  
  
 <span data-ttu-id="d9c02-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-115">[!code-cs[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]</span></span>  
  
 <span data-ttu-id="d9c02-116">抽象メソッドには実装がないので、メソッド定義の後に、通常のメソッド ブロックの代わりにセミコロン (;) を配置します。</span><span class="sxs-lookup"><span data-stu-id="d9c02-116">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="d9c02-117">抽象クラスの派生クラスでは、すべての抽象メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d9c02-117">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="d9c02-118">抽象クラスが基底クラスから仮想メソッドを継承した場合は、この抽象クラスでは抽象メソッドで仮想メソッドをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-118">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="d9c02-119">例:</span><span class="sxs-lookup"><span data-stu-id="d9c02-119">For example:</span></span>  
  
 <span data-ttu-id="d9c02-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-120">[!code-cs[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]</span></span>  
  
 <span data-ttu-id="d9c02-121">`virtual` メソッドが `abstract` として宣言されている場合、そのメソッドは、その抽象クラスを継承するどのクラスでも仮想になります。</span><span class="sxs-lookup"><span data-stu-id="d9c02-121">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="d9c02-122">抽象メソッドを継承するクラスでは、そのメソッドの元の実装にアクセスできません。上の例では、クラス F の `DoWork` は、クラス D の `DoWork` を呼び出すことができません。このようにして抽象クラスは、派生クラスに対し、仮想メソッドの新しいメソッド実装を強制的に提供させることができます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-122">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="d9c02-123">シール クラスとシール クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="d9c02-123">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="d9c02-124">クラス定義の前にキーワード `sealed` を指定することで、クラスを [sealed](../../../csharp/language-reference/keywords/sealed.md) として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-124">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="d9c02-125">例:</span><span class="sxs-lookup"><span data-stu-id="d9c02-125">For example:</span></span>  
  
 <span data-ttu-id="d9c02-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-126">[!code-cs[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]</span></span>  
  
 <span data-ttu-id="d9c02-127">シール クラスは、基底クラスとして使用できません。</span><span class="sxs-lookup"><span data-stu-id="d9c02-127">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="d9c02-128">このため、シール クラスは抽象クラスになることもできません。</span><span class="sxs-lookup"><span data-stu-id="d9c02-128">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="d9c02-129">シール クラスにより、派生が防止されます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-129">Sealed classes prevent derivation.</span></span> <span data-ttu-id="d9c02-130">シール クラスは基底クラスとして使用できないので、実行時の最適化で、シール クラス メンバーを多少高速に呼び出すことができる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9c02-130">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="d9c02-131">基底クラスの仮想メンバーをオーバーライドしている派生クラスのメソッド、インデクサー、プロパティ、またはイベントでは、そのメンバーをシールとして宣言できます。</span><span class="sxs-lookup"><span data-stu-id="d9c02-131">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="d9c02-132">これにより、その後の派生クラスでは、メンバーの仮想性が無効になります。</span><span class="sxs-lookup"><span data-stu-id="d9c02-132">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="d9c02-133">このように宣言するには、クラス メンバー宣言で [override](../../../csharp/language-reference/keywords/override.md) キーワードの前に `sealed` キーワードを配置します。</span><span class="sxs-lookup"><span data-stu-id="d9c02-133">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="d9c02-134">例:</span><span class="sxs-lookup"><span data-stu-id="d9c02-134">For example:</span></span>  
  
 <span data-ttu-id="d9c02-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="d9c02-135">[!code-cs[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9c02-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9c02-136">See Also</span></span>  
 <span data-ttu-id="d9c02-137">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9c02-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d9c02-138">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9c02-138">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="d9c02-139">[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="d9c02-139">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="d9c02-140">[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="d9c02-140">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="d9c02-141">[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md) </span><span class="sxs-lookup"><span data-stu-id="d9c02-141">[Fields](../../../csharp/programming-guide/classes-and-structs/fields.md) </span></span>  
 [<span data-ttu-id="d9c02-142">方法: 抽象プロパティを定義する</span><span class="sxs-lookup"><span data-stu-id="d9c02-142">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)

