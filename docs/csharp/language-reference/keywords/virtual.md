---
title: "virtual (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
dev_langs:
- CSharp
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
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
ms.openlocfilehash: 24ca77a0a645a17c0223437e73539bc04ba80f23
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="virtual-c-reference"></a><span data-ttu-id="a299f-102">virtual (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a299f-102">virtual (C# Reference)</span></span>
<span data-ttu-id="a299f-103">`virtual` キーワードは、メソッド、プロパティ、インデクサー、またはイベント宣言を変更し、それを派生クラスでオーバーライドできるようにするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a299f-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="a299f-104">たとえば、次のメソッドはそれを継承する任意のクラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="a299f-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="a299f-105">仮想メンバーの実装は、派生クラスの[オーバーライド メンバー](../../../csharp/language-reference/keywords/override.md)によって変更できます。</span><span class="sxs-lookup"><span data-stu-id="a299f-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="a299f-106">`virtual` キーワードの使い方について詳しくは、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a299f-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a299f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a299f-107">Remarks</span></span>  
 <span data-ttu-id="a299f-108">仮想メソッドが呼び出されると、オブジェクトの実行時の型が、オーバーライドするメンバーに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="a299f-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="a299f-109">いずれの派生クラスもメンバーをオーバーライドしなかった場合は、最派生クラスのオーバーライド メンバー (元のメンバーである可能性があります) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a299f-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="a299f-110">既定では、メソッドは仮想ではありません。</span><span class="sxs-lookup"><span data-stu-id="a299f-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="a299f-111">非仮想メソッドをオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a299f-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="a299f-112">`virtual` 修飾子を、`static`、`abstract, private`、または `override` 修飾子と共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a299f-112">You cannot use the `virtual` modifier with the `static`, `abstract, private`, or `override` modifiers.</span></span> <span data-ttu-id="a299f-113">次のコードは、仮想のプロパティの例です。</span><span class="sxs-lookup"><span data-stu-id="a299f-113">The following example shows a virtual property:</span></span>  
  
 <span data-ttu-id="a299f-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a299f-114">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]</span></span>  
  
 <span data-ttu-id="a299f-115">仮想プロパティは、宣言と呼び出しの構文の違いを除けば、抽象メソッドと似た働きを持ちます。</span><span class="sxs-lookup"><span data-stu-id="a299f-115">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="a299f-116">`virtual` 修飾子を静的プロパティに対して使うのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="a299f-116">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="a299f-117">継承する仮想プロパティは、派生クラス内で `override` 修飾子を使ったプロパティ宣言を記述することでオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="a299f-117">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a299f-118">例</span><span class="sxs-lookup"><span data-stu-id="a299f-118">Example</span></span>  
 <span data-ttu-id="a299f-119">この例では、`Shape` クラスに 2 つの座標 (`x` と `y`) と仮想メソッド `Area()` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a299f-119">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="a299f-120">他の図形クラス (`Circle`、 `Cylinder`、`Sphere` など) は `Shape` クラスを継承しており、各図の表面積が計算されています。</span><span class="sxs-lookup"><span data-stu-id="a299f-120">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="a299f-121">各派生クラスは、`Area()` のオーバーライド実装を独自に持っています。</span><span class="sxs-lookup"><span data-stu-id="a299f-121">Each derived class has it own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="a299f-122">次の宣言に示すように、継承されたクラス (`Circle`、 `Sphere`、および `Cylinder`) はいずれも、基底クラスを初期化するコンス トラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="a299f-122">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="a299f-123">次のプログラムは、メソッドに関連付けられたオブジェクトに従って `Area()` メソッドの適切な実装を呼び出すことにより、各図形の面積を計算し、表示します。</span><span class="sxs-lookup"><span data-stu-id="a299f-123">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 <span data-ttu-id="a299f-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a299f-124">[!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a299f-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a299f-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a299f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a299f-126">See Also</span></span>  
 <span data-ttu-id="a299f-127">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="a299f-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a299f-129">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-129">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="a299f-130">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="a299f-131">[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-131">[Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span></span>  
 <span data-ttu-id="a299f-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-132">[abstract](../../../csharp/language-reference/keywords/abstract.md) </span></span>  
 <span data-ttu-id="a299f-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="a299f-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="a299f-134">new</span><span class="sxs-lookup"><span data-stu-id="a299f-134">new</span></span>](../../../csharp/language-reference/keywords/new.md)

