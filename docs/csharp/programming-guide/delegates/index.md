---
title: "デリゲート (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: 30
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
ms.openlocfilehash: 1d3dc2252b086f9df9e64a059a53ec8792e11b45
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="e1f6d-102">デリゲート (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e1f6d-102">Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="e1f6d-103">[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、特定のパラメーター リストおよび戻り値の型を使用して、メソッドへの参照を表す型です。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="e1f6d-104">デリゲートをインスタンス化するときは、互換性のあるシグネチャと戻り値の型を持つ任意のメソッドにそのインスタンスを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-104">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="e1f6d-105">メソッドは、デリゲート インスタンスを使用して起動する (呼び出す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-105">You can invoke (or call) the method through the delegate instance.</span></span>  
  
 <span data-ttu-id="e1f6d-106">デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-106">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="e1f6d-107">イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-107">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="e1f6d-108">カスタム メソッドを作成して、特定のイベントの発生時に、作成したメソッドが Windows コントロールなどのクラスから呼び出されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-108">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="e1f6d-109">次の例にデリゲート宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-109">The following example shows a delegate declaration:</span></span>  
  
 <span data-ttu-id="e1f6d-110">[!code-cs[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e1f6d-110">[!code-cs[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]</span></span>  
  
 <span data-ttu-id="e1f6d-111">デリゲート型と一致するアクセス可能なクラスまたは構造体のメソッドはすべて、デリゲートに代入できます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-111">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="e1f6d-112">メソッドは、静的メソッドとインスタンス メソッドのいずれかにできます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-112">The method can be either static or an instance method.</span></span> <span data-ttu-id="e1f6d-113">このため、メソッド呼び出しをプログラムによって変更でき、また新しいコードを既存のクラスに接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-113">This makes it possible to programmatically change method calls, and also plug new code into existing classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1f6d-114">メソッドのオーバーロードのコンテキストでは、メソッドのシグネチャに戻り値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-114">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="e1f6d-115">しかしデリゲートのコンテキストでは、シグネチャに戻り値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-115">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="e1f6d-116">つまり、メソッドにはデリゲートと同じ戻り値の型が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-116">In other words, a method must have the same return type as the delegate.</span></span>  
  
 <span data-ttu-id="e1f6d-117">このようにメソッドをパラメーターとして参照できるため、デリゲートはコールバック メソッドを定義するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-117">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="e1f6d-118">たとえば、2 つのオブジェクトを比較するメソッドへの参照は、並べ替えのアルゴリズムへの引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-118">For example, a reference to a method that compares two objects could be passed as an argument to a sort algorithm.</span></span> <span data-ttu-id="e1f6d-119">比較を行うコードは独立したプロシージャであるため、並べ替えのアルゴリズムはより一般的な方法で記述できます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-119">Because the comparison code is in a separate procedure, the sort algorithm can be written in a more general way.</span></span>  
  
## <a name="delegates-overview"></a><span data-ttu-id="e1f6d-120">デリゲートの概要</span><span class="sxs-lookup"><span data-stu-id="e1f6d-120">Delegates Overview</span></span>  
 <span data-ttu-id="e1f6d-121">デリゲートには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-121">Delegates have the following properties:</span></span>  
  
-   <span data-ttu-id="e1f6d-122">デリゲートは、C++ の関数ポインターに似ていますが、タイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-122">Delegates are like C++ function pointers but are type safe.</span></span>  
  
-   <span data-ttu-id="e1f6d-123">デリゲートを使用すると、メソッドをパラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-123">Delegates allow methods to be passed as parameters.</span></span>  
  
-   <span data-ttu-id="e1f6d-124">デリゲートは、コールバック メソッドを定義するのに使用できます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-124">Delegates can be used to define callback methods.</span></span>  
  
-   <span data-ttu-id="e1f6d-125">デリゲートは連結でき、たとえば、複数のメソッドを 1 つのイベントで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-125">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>  
  
-   <span data-ttu-id="e1f6d-126">メソッドは、デリゲート型に正確に一致する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-126">Methods do not have to match the delegate type exactly.</span></span> <span data-ttu-id="e1f6d-127">詳細については、「[デリゲートの分散の使用](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-127">For more information, see [Using Variance in Delegates](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
-   <span data-ttu-id="e1f6d-128">C# Version 2.0 で、[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)の概念が導入され、別個に定義されたメソッドの代わりにコード ブロックをパラメーターとして渡せるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-128">C# version 2.0 introduced the concept of [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), which allow code blocks to be passed as parameters in place of a separately defined method.</span></span> <span data-ttu-id="e1f6d-129">C# 3.0 ではラムダ式が導入され、インライン コード ブロックをより簡潔に記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-129">C# 3.0 introduced lambda expressions as a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="e1f6d-130">匿名メソッドと (特定のコンテキストにおける) ラムダ式はどちらも、デリゲート型にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-130">Both anonymous methods and lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="e1f6d-131">これらの機能は総称して、匿名関数と呼ばれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-131">Together, these features are now known as anonymous functions.</span></span> <span data-ttu-id="e1f6d-132">ラムダ式について詳しくは、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e1f6d-132">For more information about lambda expressions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1f6d-133">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e1f6d-133">In This Section</span></span>  
  
-   [<span data-ttu-id="e1f6d-134">デリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="e1f6d-134">Using Delegates</span></span>](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [<span data-ttu-id="e1f6d-135">インターフェイス (c# プログラミング ガイド) ではなくデリゲートを使用する場合</span><span class="sxs-lookup"><span data-stu-id="e1f6d-135">When to Use Delegates Instead of Interfaces (C# Programming Guide)</span></span>](http://msdn.microsoft.com/en-us/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [<span data-ttu-id="e1f6d-136">名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート</span><span class="sxs-lookup"><span data-stu-id="e1f6d-136">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [<span data-ttu-id="e1f6d-137">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="e1f6d-137">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [<span data-ttu-id="e1f6d-138">デリゲートの分散の使用</span><span class="sxs-lookup"><span data-stu-id="e1f6d-138">Using Variance in Delegates</span></span>](../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)  
  
-   [<span data-ttu-id="e1f6d-139">方法: デリゲートを結合する (マルチキャスト デリゲート)</span><span class="sxs-lookup"><span data-stu-id="e1f6d-139">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [<span data-ttu-id="e1f6d-140">方法: デリゲートを宣言し、インスタンス化して使用する</span><span class="sxs-lookup"><span data-stu-id="e1f6d-140">How to: Declare, Instantiate, and Use a Delegate</span></span>](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="e1f6d-141">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e1f6d-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="e1f6d-142">参考書籍の該当する章</span><span class="sxs-lookup"><span data-stu-id="e1f6d-142">Featured Book Chapters</span></span>  
 <span data-ttu-id="e1f6d-143">[Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式) (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](http://go.microsoft.com/fwlink/?LinkId=195395) の [Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](http://go.microsoft.com/fwlink/?LinkId=195369)</span><span class="sxs-lookup"><span data-stu-id="e1f6d-143">[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)</span></span>  
  
 <span data-ttu-id="e1f6d-144">「[Learn」の「g C# 3.0: Master the Fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](http://go.microsoft.com/fwlink/?LinkId=195418) 」の「 [Learn」の「g C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)」</span><span class="sxs-lookup"><span data-stu-id="e1f6d-144">[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) in [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f6d-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1f6d-145">See Also</span></span>  
 <span data-ttu-id="e1f6d-146"><xref:System.Delegate></span><span class="sxs-lookup"><span data-stu-id="e1f6d-146"><xref:System.Delegate></span></span>   
 <span data-ttu-id="e1f6d-147">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e1f6d-147">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="e1f6d-148">イベント</span><span class="sxs-lookup"><span data-stu-id="e1f6d-148">Events</span></span>](../../../csharp/programming-guide/events/index.md)

