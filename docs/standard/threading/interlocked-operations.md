---
title: インタロックされた操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38532228f7a5d07bb1b9fcf7e90d2be53a28b04c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589972"
---
# <a name="interlocked-operations"></a><span data-ttu-id="cdf2d-102">インタロックされた操作</span><span class="sxs-lookup"><span data-stu-id="cdf2d-102">Interlocked Operations</span></span>
<span data-ttu-id="cdf2d-103"><xref:System.Threading.Interlocked> クラスでは、複数のスレッドによって共有されている変数へのアクセスを同期するメソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-103">The <xref:System.Threading.Interlocked> class provides methods that synchronize access to a variable that is shared by multiple threads.</span></span> <span data-ttu-id="cdf2d-104">この変数が共有メモリにある場合、さまざまなプロセスのスレッドがこのメカニズムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-104">The threads of different processes can use this mechanism if the variable is in shared memory.</span></span> <span data-ttu-id="cdf2d-105">インタロックされた操作はアトミックです。つまり、その操作全体が 1 つの単位のため、同じ変数の別のインタロックされた操作によって中断されることはありません。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-105">Interlocked operations are atomic — that is, the entire operation is a unit that cannot be interrupted by another interlocked operation on the same variable.</span></span> <span data-ttu-id="cdf2d-106">これは、メモリ アドレスから値を読み込んだ後、変更して格納できるようになる前にスレッドを中断できるプリエンプティブ マルチスレッドのオペレーティング システムで重要です。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-106">This is important in operating systems with preemptive multithreading, where a thread can be suspended after loading a value from a memory address, but before having the chance to alter it and store it.</span></span>  
  
 <span data-ttu-id="cdf2d-107"><xref:System.Threading.Interlocked> クラスでは次の操作が提供されます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-107">The <xref:System.Threading.Interlocked> class provides the following operations:</span></span>  
  
-   <span data-ttu-id="cdf2d-108">.NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Add%2A> メソッドは変数に整数値を追加して、変数の新しい値を返します。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-108">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Add%2A> method adds an integer value to a variable and returns the new value of the variable.</span></span>  
  
-   <span data-ttu-id="cdf2d-109">.NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Read%2A> メソッドはアトミック操作として 64 ビットの整数値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-109">In the .NET Framework version 2.0, the <xref:System.Threading.Interlocked.Read%2A> method reads a 64-bit integer value as an atomic operation.</span></span> <span data-ttu-id="cdf2d-110">これは、64 ビット整数の読み取りが通常はアトミック操作ではない 32 ビット オペレーティング システムでは有用です。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-110">This is useful on 32-bit operating systems, where reading a 64-bit integer is not ordinarily an atomic operation.</span></span>  
  
-   <span data-ttu-id="cdf2d-111"><xref:System.Threading.Interlocked.Increment%2A> および <xref:System.Threading.Interlocked.Decrement%2A> メソッドは変数をインクリメントまたはデクリメントして、結果の値を返します。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-111">The <xref:System.Threading.Interlocked.Increment%2A> and <xref:System.Threading.Interlocked.Decrement%2A> methods increment or decrement a variable and return the resulting value.</span></span>  
  
-   <span data-ttu-id="cdf2d-112"><xref:System.Threading.Interlocked.Exchange%2A> メソッドは、指定された変数で値をアトミックに変換して値を返し、それを新しい値で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-112">The <xref:System.Threading.Interlocked.Exchange%2A> method performs an atomic exchange of the value in a specified variable, returning that value and replacing it with a new value.</span></span> <span data-ttu-id="cdf2d-113">.NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-113">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="cdf2d-114">「<xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-114">See <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.</span></span>  
  
-   <span data-ttu-id="cdf2d-115"><xref:System.Threading.Interlocked.CompareExchange%2A> メソッドでも 2 つの値を変換しますが、比較結果によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-115">The <xref:System.Threading.Interlocked.CompareExchange%2A> method also exchanges two values, but contingent on the result of a comparison.</span></span> <span data-ttu-id="cdf2d-116">.NET Framework Version 2.0 では、任意の参照型の変数に対してこのメソッドのジェネリック オーバーロードを使用してこの交換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-116">In the .NET Framework version 2.0, a generic overload of this method can be used to perform this exchange on a variable of any reference type.</span></span> <span data-ttu-id="cdf2d-117">「<xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-117">See <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.</span></span>  
  
 <span data-ttu-id="cdf2d-118">最新のプロセッサでは、<xref:System.Threading.Interlocked> クラスのメソッドを単一の命令で実装できる場合もよくあります。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-118">On modern processors, the methods of the <xref:System.Threading.Interlocked> class can often be implemented by a single instruction.</span></span> <span data-ttu-id="cdf2d-119">このため、非常にパフォーマンスの高い同期を行うことができ、それらを使用して、スピン ロックのようなより高レベルの同期メカニズムを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-119">Thus, they provide very high-performance synchronization and can be used to build higher-level synchronization mechanisms, like spin locks.</span></span>  
  
 <span data-ttu-id="cdf2d-120"><xref:System.Threading.Monitor> クラスと <xref:System.Threading.Interlocked> クラスを組み合わせて使用する例については、「[Monitor クラス](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-120">For an example that uses the <xref:System.Threading.Monitor> and <xref:System.Threading.Interlocked> classes in combination, see [Monitors](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="compareexchange-example"></a><span data-ttu-id="cdf2d-121">CompareExchange の例</span><span class="sxs-lookup"><span data-stu-id="cdf2d-121">CompareExchange Example</span></span>  
 <span data-ttu-id="cdf2d-122"><xref:System.Threading.Interlocked.CompareExchange%2A> メソッドを使用して、単純なインクリメントまたはデクリメントよりも複雑な計算を保護できます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-122">The <xref:System.Threading.Interlocked.CompareExchange%2A> method can be used to protect computations that are more complicated than simple increment and decrement.</span></span> <span data-ttu-id="cdf2d-123">次の例は、浮動小数点数として格納されている現在の合計に対して加算を行うスレッドセーフ メソッドを示しています </span><span class="sxs-lookup"><span data-stu-id="cdf2d-123">The following example demonstrates a thread-safe method that adds to a running total stored as a floating point number.</span></span> <span data-ttu-id="cdf2d-124">(整数の場合は、<xref:System.Threading.Interlocked.Add%2A> メソッドがより単純なソリューションとなります)。完全なコード例については、単精度と倍精度浮動小数点引数 (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> と <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>) を受け取る <xref:System.Threading.Interlocked.CompareExchange%2A> のオーバーロードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-124">(For integers, the <xref:System.Threading.Interlocked.Add%2A> method is a simpler solution.) For complete code examples, see the overloads of <xref:System.Threading.Interlocked.CompareExchange%2A> that take single-precision and double-precision floating-point arguments (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> and <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a><span data-ttu-id="cdf2d-125">Exchange および CompareExchange の型指定されていないオーバーロード</span><span class="sxs-lookup"><span data-stu-id="cdf2d-125">Untyped Overloads of Exchange and CompareExchange</span></span>  
 <span data-ttu-id="cdf2d-126"><xref:System.Threading.Interlocked.Exchange%2A> および <xref:System.Threading.Interlocked.CompareExchange%2A>メソッドには、<xref:System.Object> 型の引数を受け取るオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-126">The <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods have overloads that take arguments of type <xref:System.Object>.</span></span> <span data-ttu-id="cdf2d-127">各オーバーロードの最初の引数は `ref Object` (Visual Basic では `ByRef … As Object`) であり、タイプ セーフを確保するために、この引数に渡される変数は <xref:System.Object> のように厳密に型指定される必要があります。これらのメソッドを呼び出すときに、単に最初の引数を型 <xref:System.Object> にキャストするだけでは不十分です。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-127">The first argument of each of these overloads is `ref Object` (`ByRef … As Object` in Visual Basic), and type safety requires the variable passed to this argument to be typed strictly as <xref:System.Object>; you cannot simply cast the first argument to type <xref:System.Object> when calling these methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdf2d-128">.NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.Exchange%2A> および <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドのジェネリック オーバーロードを使用して、厳密に型指定された変数を変換します。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-128">In the .NET Framework version 2.0, use the generic overloads of the <xref:System.Threading.Interlocked.Exchange%2A> and <xref:System.Threading.Interlocked.CompareExchange%2A> methods to exchange strongly typed variables.</span></span>  
  
 <span data-ttu-id="cdf2d-129">一度だけ設定できる `ClassA` 型のプロパティのコード例を次に示します。このプロパティは、.NET Framework Version 1.0 または 1.1 で実装できます。</span><span class="sxs-lookup"><span data-stu-id="cdf2d-129">The following code example shows a property of type `ClassA` that can be set only once, as it might be implemented in the .NET Framework version 1.0 or 1.1.</span></span>  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cdf2d-130">参照</span><span class="sxs-lookup"><span data-stu-id="cdf2d-130">See Also</span></span>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="cdf2d-131">スレッド化</span><span class="sxs-lookup"><span data-stu-id="cdf2d-131">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="cdf2d-132">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="cdf2d-132">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
