---
title: インスタンス コンストラクター (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 5864511e6323ca1508494abfe2350e8eaffb6a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="664e5-102">インスタンス コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="664e5-102">Instance Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="664e5-103">インスタンス コンストラクターは、[new](../../../csharp/language-reference/keywords/new.md) 式を使って[クラス](../../../csharp/language-reference/keywords/class.md)のオブジェクトを作成するときに、インスタンス メンバー変数を作成および初期化するために使われます。</span><span class="sxs-lookup"><span data-stu-id="664e5-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/keywords/new.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md).</span></span> <span data-ttu-id="664e5-104">[静的](../../../csharp/language-reference/keywords/static.md)クラスを初期化する場合、または非静的クラスの静的変数を初期化する場合は、静的コンストラクターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="664e5-104">To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you must define a static constructor.</span></span> <span data-ttu-id="664e5-105">詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="664e5-105">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
 <span data-ttu-id="664e5-106">次に示すのは、インスタンス コンストラクターの例です。</span><span class="sxs-lookup"><span data-stu-id="664e5-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="664e5-107">わかりやすくするため、このクラスにはパブリック フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="664e5-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="664e5-108">パブリック フィールドを使うと、プログラム内の任意の場所にある任意のメソッドが、制限も検証もなしにオブジェクトの内部動作にアクセスできるため、パブリック フィールドは推奨されるプログラミング手法ではありません。</span><span class="sxs-lookup"><span data-stu-id="664e5-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="664e5-109">データ メンバーは、一般にプライベートにする必要があり、クラスのメソッドとプロパティを介してのみアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="664e5-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="664e5-110">このインスタンス コンストラクターは、`CoOrds` クラスに基づくオブジェクトが作成されるたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="664e5-110">This instance constructor is called whenever an object based on the `CoOrds` class is created.</span></span> <span data-ttu-id="664e5-111">引数を受け取らないこのようなコンストラクターは、*既定のコンストラクター*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="664e5-111">A constructor like this one, which takes no arguments, is called a *default constructor*.</span></span> <span data-ttu-id="664e5-112">ただし、コンストラクターを追加すると便利な場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="664e5-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="664e5-113">たとえば、データ メンバーの初期値を指定できるコンストラクターを `CoOrds` クラスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="664e5-113">For example, we can add a constructor to the `CoOrds` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 <span data-ttu-id="664e5-114">これにより、次のように、既定値または特定の初期値で `CoOrd` オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="664e5-114">This allows `CoOrd` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 <span data-ttu-id="664e5-115">クラスにコンストラクターがない場合は、既定のコンストラクターが自動的に生成され、既定値を使ってオブジェクトのフィールドが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="664e5-115">If a class does not have a constructor, a default constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="664e5-116">たとえば、[int](../../../csharp/language-reference/keywords/int.md) は 0 に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="664e5-116">For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0.</span></span> <span data-ttu-id="664e5-117">既定値について詳しくは、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="664e5-117">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="664e5-118">したがって、`CoOrds` クラスの既定のコンストラクターは、すべてのデータ メンバーをゼロに初期化するため、クラスの動作を変更することなくまとめて削除することができます。</span><span class="sxs-lookup"><span data-stu-id="664e5-118">Therefore, because the `CoOrds` class default constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="664e5-119">複数のコンストラクターを使う完全な例は後の例 1 で、自動的に生成されたコンストラクターの例は例 2 で示します。</span><span class="sxs-lookup"><span data-stu-id="664e5-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="664e5-120">インスタンス コンストラクターを使って、基底クラスのインスタンス コンストラクターを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="664e5-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="664e5-121">次のように、クラスのコンストラクターは、初期化子を使って基底クラスのコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="664e5-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 <span data-ttu-id="664e5-122">この例では、`Circle` クラスは、半径と高さを表す値を、`Circle` の派生元である `Shape` によって提供されるコンストラクターに渡しています。</span><span class="sxs-lookup"><span data-stu-id="664e5-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="664e5-123">`Shape` と `Circle` を使う完全な例は、例 3 をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="664e5-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="664e5-124">例 1</span><span class="sxs-lookup"><span data-stu-id="664e5-124">Example 1</span></span>  
 <span data-ttu-id="664e5-125">次の例で示すクラスには、引数を持たないクラス コンストラクターと、2 つの引数を持つクラス コンストラクターがあります。</span><span class="sxs-lookup"><span data-stu-id="664e5-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="664e5-126">例 2</span><span class="sxs-lookup"><span data-stu-id="664e5-126">Example 2</span></span>  
 <span data-ttu-id="664e5-127">この例の `Person` クラスにはコンストラクターがありません。このような場合は、既定のコンストラクターが自動的に提供され、フィールドは既定値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="664e5-127">In this example, the class `Person` does not have any constructors, in which case, a default constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 <span data-ttu-id="664e5-128">`age` の既定値は `0`、`name` の既定値は `null` であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="664e5-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="664e5-129">既定値について詳しくは、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="664e5-129">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="664e5-130">例 3</span><span class="sxs-lookup"><span data-stu-id="664e5-130">Example 3</span></span>  
 <span data-ttu-id="664e5-131">次の例では、基底クラスの初期化子の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="664e5-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="664e5-132">`Circle` クラスは汎用クラス `Shape` から派生し、`Cylinder` クラスは `Circle` クラスから派生しています。</span><span class="sxs-lookup"><span data-stu-id="664e5-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="664e5-133">各派生クラスのコンストラクターでは、その基底クラスの初期化子が使われています。</span><span class="sxs-lookup"><span data-stu-id="664e5-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 <span data-ttu-id="664e5-134">基底クラスのコンストラクターの呼び出しに関する他の例については、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、「[override](../../../csharp/language-reference/keywords/override.md)」、「[base](../../../csharp/language-reference/keywords/base.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="664e5-134">For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664e5-135">参照</span><span class="sxs-lookup"><span data-stu-id="664e5-135">See Also</span></span>  
 [<span data-ttu-id="664e5-136">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="664e5-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="664e5-137">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="664e5-137">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="664e5-138">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="664e5-138">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="664e5-139">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="664e5-139">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="664e5-140">static</span><span class="sxs-lookup"><span data-stu-id="664e5-140">static</span></span>](../../../csharp/language-reference/keywords/static.md)
