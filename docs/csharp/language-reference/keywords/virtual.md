---
title: virtual (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dce3333646bca6f558e3760849b6cffdb34a6c0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-c-reference"></a><span data-ttu-id="ea206-102">virtual (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ea206-102">virtual (C# Reference)</span></span>
<span data-ttu-id="ea206-103">`virtual` キーワードは、メソッド、プロパティ、インデクサー、またはイベント宣言を変更し、それを派生クラスでオーバーライドできるようにするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea206-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="ea206-104">たとえば、次のメソッドはそれを継承する任意のクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ea206-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="ea206-105">仮想メンバーの実装は、派生クラスの[オーバーライド メンバー](../../../csharp/language-reference/keywords/override.md)によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="ea206-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="ea206-106">`virtual` キーワードの使い方について詳しくは、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ea206-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea206-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ea206-107">Remarks</span></span>  
 <span data-ttu-id="ea206-108">仮想メソッドが呼び出されると、オブジェクトの実行時の型が、オーバーライドするメンバーに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ea206-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="ea206-109">いずれの派生クラスもメンバーをオーバーライドしなかった場合は、最派生クラスのオーバーライド メンバー (元のメンバーである可能性があります) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ea206-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="ea206-110">既定では、メソッドは仮想ではありません。</span><span class="sxs-lookup"><span data-stu-id="ea206-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="ea206-111">非仮想メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ea206-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="ea206-112">使用することはできません、`virtual`修飾子を`static`、 `abstract`、 `private`、または`override`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="ea206-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="ea206-113">次のコードは、仮想のプロパティの例です。</span><span class="sxs-lookup"><span data-stu-id="ea206-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="ea206-114">仮想プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。</span><span class="sxs-lookup"><span data-stu-id="ea206-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="ea206-115">`virtual` 修飾子を静的プロパティに対して使うのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="ea206-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="ea206-116">継承する仮想プロパティは、派生クラス内で `override` 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="ea206-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea206-117">例</span><span class="sxs-lookup"><span data-stu-id="ea206-117">Example</span></span>  
 <span data-ttu-id="ea206-118">この例では、`Shape` クラスに 2 つの座標 (`x` と `y`) と仮想メソッド `Area()` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea206-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="ea206-119">他の図形クラス (`Circle`、 `Cylinder`、`Sphere` など) は `Shape` クラスを継承しており、各図の表面積が計算されています。</span><span class="sxs-lookup"><span data-stu-id="ea206-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="ea206-120">各派生クラスは、`Area()` のオーバーライド実装を独自に持っています。</span><span class="sxs-lookup"><span data-stu-id="ea206-120">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="ea206-121">次の宣言に示すように、継承されたクラス (`Circle`、 `Sphere`、および `Cylinder`) はいずれも、基底クラスを初期化するコンス トラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea206-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="ea206-122">次のプログラムは、メソッドに関連付けられたオブジェクトに従って `Area()` メソッドの適切な実装を呼び出すことにより、各図形の面積を計算し、表示します。</span><span class="sxs-lookup"><span data-stu-id="ea206-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ea206-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ea206-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ea206-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea206-124">See Also</span></span>  
 [<span data-ttu-id="ea206-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ea206-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ea206-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ea206-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ea206-127">修飾子</span><span class="sxs-lookup"><span data-stu-id="ea206-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="ea206-128">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="ea206-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ea206-129">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="ea206-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="ea206-130">abstract</span><span class="sxs-lookup"><span data-stu-id="ea206-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="ea206-131">override</span><span class="sxs-lookup"><span data-stu-id="ea206-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="ea206-132">new</span><span class="sxs-lookup"><span data-stu-id="ea206-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
