---
title: コンストラクターの使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 5fe6f10e3842c0c0aac4b2669f8ca367fa8c3be2
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="6c962-102">コンストラクターの使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6c962-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="6c962-103">[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)を作成する際には、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="6c962-104">コンストラクターの名前はクラスまたは構造体と同じで、通常は、このコンストラクターによって、新しいオブジェクトのデータ メンバーが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="6c962-105">次の例では、`Taxi` というクラスが、簡単なコンストラクターを使用して定義された後、</span><span class="sxs-lookup"><span data-stu-id="6c962-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="6c962-106">[new](../../../csharp/language-reference/keywords/new.md) 演算子によってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="6c962-107">`Taxi` コンストラクターは、新しいオブジェクトに対してメモリが割り当てられるとすぐに、`new` 演算子によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="6c962-108">パラメーターを取らないコンストラクターを "*既定のコンストラクター*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="6c962-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="6c962-109">`new` 演算子を使用してオブジェクトがインスタンス化される際に `new` に引数が渡されないと、この既定のコンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="6c962-110">詳細については、「[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="6c962-111">クラスが[静的](../../../csharp/language-reference/keywords/static.md)である場合を除き、コンストラクターが存在しないクラスには、クラスをインスタンス化できるように、パブリックな既定のコンストラクターが C# コンパイラによって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="6c962-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="6c962-112">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="6c962-113">次のようにコンストラクターをプライベートにすれば、クラスがインスタンス化されないようにできます。</span><span class="sxs-lookup"><span data-stu-id="6c962-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="6c962-114">詳細については、「[プライベート コンストラクター](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="6c962-115">[struct](../../../csharp/language-reference/keywords/struct.md) 型のコンストラクターはクラス コンストラクターに似ていますが、`structs` には、明示的な既定のコンストラクターを含めることができません。既定のコンストラクターは、コンパイラによって自動的に提供されるためです。</span><span class="sxs-lookup"><span data-stu-id="6c962-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="6c962-116">このコンストラクターは、`struct` 内の各フィールドを既定値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="6c962-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="6c962-117">詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="6c962-118">ただし、この既定のコンストラクターは、`struct` が `new` によってインスタンス化される場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="6c962-119">たとえば、次のコードでは、<xref:System.Int32> の既定のコンストラクターが使用されるため、整数が確実に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="6c962-120">ただし、次のコードでは `new` が使用されておらず、コードは初期化されていないオブジェクトの使用を試みるため、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6c962-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="6c962-121">これに対して、`structs` をベースにしたオブジェクト (組み込みのすべての数値型など) は、次の例のように、初期化または代入してから使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="6c962-122">このため、値型の既定のコンストラクターを呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c962-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="6c962-123">クラスと `structs` のどちらも、パラメーターを受け取るコンストラクターを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="6c962-124">パラメーターを受け取るコンストラクターは、`new` ステートメントまたは [base](../../../csharp/language-reference/keywords/base.md) ステートメントを使用して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c962-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="6c962-125">クラスと `structs` は複数のコンストラクターを定義することもできます。また、どちらも、既定のコンストラクターの定義には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="6c962-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="6c962-126">例:</span><span class="sxs-lookup"><span data-stu-id="6c962-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="6c962-127">このクラスは、次のいずれかのステートメントを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="6c962-128">コンストラクターでは、`base` キーワードを使用して、基底クラスのコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6c962-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="6c962-129">例:</span><span class="sxs-lookup"><span data-stu-id="6c962-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="6c962-130">この例では、コンストラクターのブロックを実行する前に、基底クラスのコンストラクターを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="6c962-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="6c962-131">`base` キーワードは、パラメーターの有無に関係なく使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="6c962-132">コンストラクターのパラメーターは、`base` のパラメーターまたは式の一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="6c962-133">詳細については、「[base](../../../csharp/language-reference/keywords/base.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="6c962-134">派生クラスで基底クラスのコンストラクターが `base` キーワードを使用して明示的に呼び出されていない場合、既定のコンストラクター (存在する場合) は暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="6c962-135">つまり、次に示すコンストラクターの宣言は実質的に同じです。</span><span class="sxs-lookup"><span data-stu-id="6c962-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="6c962-136">基底クラスが既定のコンストラクターを提供しない場合、派生クラスでは、`base` を使って基本コンストラクターを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c962-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="6c962-137">コンストラクターで [this](../../../csharp/language-reference/keywords/this.md) キーワードを使用すると、同じオブジェクトで別のコンストラクターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6c962-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="6c962-138">`base` と同様、`this` もパラメーターの有無に関係なく使用でき、コンストラクターのパラメーターはいずれも `this` のパラメーターとしても、式の一部としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="6c962-139">たとえば、上の例の 2 番目のコンストラクターは `this` を使用して次のように書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="6c962-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="6c962-140">上の例で `this` キーワードを使用すると、このコンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="6c962-141">コンストラクターは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) または [private protected](../../../csharp/language-reference/keywords/private-protected.md) としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="6c962-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="6c962-142">こうしたアクセス修飾子により、クラスのユーザーによるクラスの作成方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="6c962-143">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="6c962-144">コンストラクターは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6c962-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="6c962-145">静的コンストラクターは、静的フィールドがアクセスされる直前に自動的に呼び出され、通常は静的なクラス メンバーを初期化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6c962-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="6c962-146">詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c962-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6c962-147">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6c962-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c962-148">参照</span><span class="sxs-lookup"><span data-stu-id="6c962-148">See Also</span></span>  
 [<span data-ttu-id="6c962-149">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6c962-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c962-150">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="6c962-150">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="6c962-151">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="6c962-151">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="6c962-152">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="6c962-152">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
