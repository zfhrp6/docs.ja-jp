---
title: virtual (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 5a188e9a7cbb7a1c497d577039c2b2578eaa7526
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="virtual-c-reference"></a><span data-ttu-id="1ac56-102">virtual (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1ac56-102">virtual (C# Reference)</span></span>
<span data-ttu-id="1ac56-103">`virtual` キーワードは、メソッド、プロパティ、インデクサー、またはイベント宣言を変更し、それを派生クラスでオーバーライドできるようにするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="1ac56-104">たとえば、次のメソッドはそれを継承する任意のクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="1ac56-105">仮想メンバーの実装は、派生クラスの[オーバーライド メンバー](../../../csharp/language-reference/keywords/override.md)によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="1ac56-106">`virtual` キーワードの使い方について詳しくは、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1ac56-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ac56-107">コメント</span><span class="sxs-lookup"><span data-stu-id="1ac56-107">Remarks</span></span>  
 <span data-ttu-id="1ac56-108">仮想メソッドが呼び出されると、オブジェクトの実行時の型が、オーバーライドするメンバーに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="1ac56-109">いずれの派生クラスもメンバーをオーバーライドしなかった場合は、最派生クラスのオーバーライド メンバー (元のメンバーである可能性があります) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="1ac56-110">既定では、メソッドは仮想ではありません。</span><span class="sxs-lookup"><span data-stu-id="1ac56-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="1ac56-111">非仮想メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1ac56-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="1ac56-112">`virtual` 修飾子を、`static`、`abstract`、`private`、`override` 修飾子と共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1ac56-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="1ac56-113">次のコードは、仮想のプロパティの例です。</span><span class="sxs-lookup"><span data-stu-id="1ac56-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="1ac56-114">仮想プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="1ac56-115">`virtual` 修飾子を静的プロパティに対して使うのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="1ac56-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="1ac56-116">継承する仮想プロパティは、派生クラス内で `override` 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="1ac56-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ac56-117">例</span><span class="sxs-lookup"><span data-stu-id="1ac56-117">Example</span></span>  
 <span data-ttu-id="1ac56-118">この例では、`Shape` クラスに 2 つの座標 (`x` と `y`) と仮想メソッド `Area()` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ac56-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="1ac56-119">他の図形クラス (`Circle`、 `Cylinder`、`Sphere` など) は `Shape` クラスを継承しており、各図の表面積が計算されています。</span><span class="sxs-lookup"><span data-stu-id="1ac56-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="1ac56-120">各派生クラスは、`Area()` のオーバーライド実装を独自に持っています。</span><span class="sxs-lookup"><span data-stu-id="1ac56-120">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="1ac56-121">次の宣言に示すように、継承されたクラス (`Circle`、 `Sphere`、および `Cylinder`) はいずれも、基底クラスを初期化するコンス トラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="1ac56-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="1ac56-122">次のプログラムは、メソッドに関連付けられたオブジェクトに従って `Area()` メソッドの適切な実装を呼び出すことにより、各図形の面積を計算し、表示します。</span><span class="sxs-lookup"><span data-stu-id="1ac56-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1ac56-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1ac56-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1ac56-124">参照</span><span class="sxs-lookup"><span data-stu-id="1ac56-124">See Also</span></span>  
 [<span data-ttu-id="1ac56-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1ac56-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1ac56-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1ac56-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1ac56-127">修飾子</span><span class="sxs-lookup"><span data-stu-id="1ac56-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="1ac56-128">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="1ac56-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1ac56-129">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="1ac56-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="1ac56-130">abstract</span><span class="sxs-lookup"><span data-stu-id="1ac56-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="1ac56-131">override</span><span class="sxs-lookup"><span data-stu-id="1ac56-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="1ac56-132">new</span><span class="sxs-lookup"><span data-stu-id="1ac56-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
