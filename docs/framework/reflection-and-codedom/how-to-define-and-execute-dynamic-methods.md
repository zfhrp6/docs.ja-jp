---
title: '方法: 動的メソッドを定義および実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53142ffa38bda036dd558dd6d23912ebd2e393ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="e95f2-102">方法: 動的メソッドを定義および実行する</span><span class="sxs-lookup"><span data-stu-id="e95f2-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="e95f2-103">ここでは、単純な動的メソッドと、クラスのインスタンスにバインドされた動的メソッドを定義し、実行する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="e95f2-104">動的メソッドの詳細については、<xref:System.Reflection.Emit.DynamicMethod> クラスに関するトピックと「[Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)」(リフレクション出力による動的メソッドのシナリオ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="e95f2-105">動的メソッドを定義および実行するには</span><span class="sxs-lookup"><span data-stu-id="e95f2-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="e95f2-106">メソッドを実行するために、デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="e95f2-107">汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="e95f2-108">次のコードでは、`SquareIt` メソッドで使用できる 2 つのデリゲート型 (1 つはジェネリック) を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="e95f2-109">動的メソッドのパラメーターの型を指定する配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="e95f2-110">この例では、唯一のパラメーターが `int` (Visual Basic では `Integer`) であるため、配列には要素は 1 つしかありません。</span><span class="sxs-lookup"><span data-stu-id="e95f2-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="e95f2-111"><xref:System.Reflection.Emit.DynamicMethod> を作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="e95f2-112">この例では、メソッドの名前は `SquareIt` です。</span><span class="sxs-lookup"><span data-stu-id="e95f2-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e95f2-113">動的メソッドに名前を付ける必要はありません。動的メソッドは名前で呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e95f2-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="e95f2-114">複数の動的メソッドに同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="e95f2-115">ただし、名前は呼び出し履歴に表示されるため、デバッグの際に役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="e95f2-116">戻り値の型は、`long` として指定します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="e95f2-117">プログラム例を格納する `Example` クラスを含むモジュールにメソッドを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="e95f2-118">読み込むモジュールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-118">Any loaded module could be specified.</span></span> <span data-ttu-id="e95f2-119">動的メソッドは、モジュール レベルの `static` メソッド (Visual Basic では `Shared`) と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="e95f2-120">メソッド本体を出力します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-120">Emit the method body.</span></span> <span data-ttu-id="e95f2-121">この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL (Microsoft Intermediate Language) を出力します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e95f2-122">また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="e95f2-123">この例の MSIL は、`int` である引数をスタックに読み込み、これを `long` に変換します。次に、`long` を複製し、2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="e95f2-124">これにより、スタックには 2 乗された結果が残され、メソッドで実行する必要のあるすべてが返されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="e95f2-125"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを呼び出して、動的メソッドを表す (手順 1 で宣言した) デリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="e95f2-126">デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても (MSIL の追加など) 無視されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="e95f2-127">次のコードでは、汎用デリゲートを使用して、デリゲートを作成し呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="e95f2-128">オブジェクトにバインドされた動的メソッドを定義および実行するには</span><span class="sxs-lookup"><span data-stu-id="e95f2-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="e95f2-129">メソッドを実行するために、デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="e95f2-130">汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e95f2-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="e95f2-131">次のコードでは、1 つのパラメーターと戻り値を持つ任意のメソッド、またはデリゲートがオブジェクトにバインドされている場合は 2 つのパラメーターと戻り値を持つメソッドの実行に使用できる汎用デリゲート型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="e95f2-132">動的メソッドのパラメーターの型を指定する配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="e95f2-133">メソッドを表すデリゲートをオブジェクトにバインドする場合、1 つ目のパラメーターは、デリゲートのバインド先となる型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="e95f2-134">この例では、`Example` 型と `int` 型 (Visual Basic では `Integer`) の 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="e95f2-135"><xref:System.Reflection.Emit.DynamicMethod> を作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="e95f2-136">この例では、メソッドに名前はありません。</span><span class="sxs-lookup"><span data-stu-id="e95f2-136">In this example the method has no name.</span></span> <span data-ttu-id="e95f2-137">戻り値の型は、`int` (Visual Basic では `Integer`) として指定します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="e95f2-138">このメソッドは、`Example` クラスのプライベート メンバーとプロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="e95f2-139">メソッド本体を出力します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-139">Emit the method body.</span></span> <span data-ttu-id="e95f2-140">この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL (Microsoft Intermediate Language) を出力します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="e95f2-141">また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="e95f2-142">この例の MSIL は、`Example` クラスのインスタンスである 1 つ目の引数を読み込み、この引数を使用して、`int` 型のプライベート インスタンス フィールドの値を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="e95f2-143">2 つ目の引数が読み込まれ、この 2 つの数値が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="e95f2-144">この結果が `int` よりも大きい場合、値は切り捨てられ、最上位ビットは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="e95f2-145">戻り値がスタックに配置されて、メソッドが返されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="e95f2-146"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> メソッド オーバーロードを呼び出して、動的メソッドを表す (手順 1 で宣言した) デリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="e95f2-147">デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても (MSIL の追加など) 無視されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e95f2-148"><xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを複数回呼び出して、対象の型の他のインスタンスにバインドされたデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="e95f2-149">次のコードでは、プライベート テスト フィールドが 42 に設定された `Example` クラスの新しいインスタンスにメソッドをバインドします。</span><span class="sxs-lookup"><span data-stu-id="e95f2-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="e95f2-150">つまり、デリゲートが呼び出されるたびに、`Example` のインスタンスがメソッドの 1 つ目のパラメーターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="e95f2-151">メソッドの 1 つ目のパラメーターは、常に `Example` のインスタンスを受け取るため、`OneParameter` デリゲートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="e95f2-152">デリゲートの呼び出し時には、2 つ目のパラメーターだけが必要となります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="e95f2-153">例</span><span class="sxs-lookup"><span data-stu-id="e95f2-153">Example</span></span>  
 <span data-ttu-id="e95f2-154">単純な動的メソッドおよびクラスのインスタンスにバインドされた動的メソッドを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="e95f2-155">この単純な動的メソッドは、32 ビット整数である引数を 1 つ受け取り、その整数の 2 乗を 64 ビットで返します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="e95f2-156">汎用デリゲートを使用して、メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="e95f2-157">2 つ目の動的メソッドには、`Example` 型と `int` 型 (Visual Basic では `Integer`) の 2 つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="e95f2-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="e95f2-158">動的メソッドが作成されると、`int` 型の引数を 1 つ持つ汎用デリゲートを使用して、`Example` のインスタンスにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="e95f2-159">メソッドの 1 つ目のパラメーターは、常に `Example` のバインドされたインスタンスを受け取るため、デリゲートは `Example` 型の引数を持ちません。</span><span class="sxs-lookup"><span data-stu-id="e95f2-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="e95f2-160">デリゲートの呼び出し時には、`int` 型の引数だけが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e95f2-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="e95f2-161">動的メソッドは、`Example` クラスのプライベート フィールドにアクセスし、プライベート フィールドと `int` 型の引数の積を返します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="e95f2-162">メソッドの実行に使用できるデリゲートを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e95f2-163">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e95f2-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e95f2-164">このコードには、コンパイルに必要な C# の `using` ステートメント (Visual Basic では `Imports`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e95f2-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="e95f2-165">追加のアセンブリ参照は不要です。</span><span class="sxs-lookup"><span data-stu-id="e95f2-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="e95f2-166">コマンド ラインで csc.exe、vbc.exe、または cl.exe を使用して、コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="e95f2-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="e95f2-167">Visual Studio でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="e95f2-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95f2-168">参照</span><span class="sxs-lookup"><span data-stu-id="e95f2-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="e95f2-169">リフレクション出力の使用</span><span class="sxs-lookup"><span data-stu-id="e95f2-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="e95f2-170">リフレクション出力による動的メソッドのシナリオ</span><span class="sxs-lookup"><span data-stu-id="e95f2-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
