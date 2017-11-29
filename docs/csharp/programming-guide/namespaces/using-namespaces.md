---
title: "名前空間の使用 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f485992f5d4b7bc16aaefeec8c7c76ce39f48ef0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-namespaces-c-programming-guide"></a><span data-ttu-id="232c5-102">名前空間の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="232c5-102">Using Namespaces (C# Programming Guide)</span></span>
<span data-ttu-id="232c5-103">C# プログラム内では名前空間が 2 つの方法でよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="232c5-103">Namespaces are heavily used within C# programs in two ways.</span></span> <span data-ttu-id="232c5-104">最初の方法では、.NET Framework クラスで名前空間を使用して、その多くのクラスを整理します。</span><span class="sxs-lookup"><span data-stu-id="232c5-104">Firstly, the .NET Framework classes use namespaces to organize its many classes.</span></span> <span data-ttu-id="232c5-105">2 つ目の方法では、独自の名前空間を宣言します。これは、より大きなプログラミング プロジェクトでクラス名とメソッド名のスコープを制御するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="232c5-105">Secondly, declaring your own namespaces can help control the scope of class and method names in larger programming projects.</span></span>  
  
## <a name="accessing-namespaces"></a><span data-ttu-id="232c5-106">名前空間へのアクセス</span><span class="sxs-lookup"><span data-stu-id="232c5-106">Accessing Namespaces</span></span>  
 <span data-ttu-id="232c5-107">ほとんどの C# アプリケーションは `using` ディレクティブのセクションから始まります。</span><span class="sxs-lookup"><span data-stu-id="232c5-107">Most C# applications begin with a section of `using` directives.</span></span> <span data-ttu-id="232c5-108">このセクションには、アプリケーションが頻繁に使用する名前空間がリストされ、包含されているメソッドが使用されるたびにプログラマが完全修飾名を指定しなくても済むようにします。</span><span class="sxs-lookup"><span data-stu-id="232c5-108">This section lists the namespaces that the application will be using frequently, and saves the programmer from specifying a fully qualified name every time that a method that is contained within is used.</span></span>  
  
 <span data-ttu-id="232c5-109">たとえば、次の行を記述したとします。</span><span class="sxs-lookup"><span data-stu-id="232c5-109">For example, by including the line:</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 <span data-ttu-id="232c5-110">この場合、プログラムの開始位置で、以下のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="232c5-110">At the start of a program, the programmer can use the code:</span></span>  
  
 [!code-csharp[csProgGuide#31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 <span data-ttu-id="232c5-111">これは次のコードの代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="232c5-111">Instead of:</span></span>  
  
 [!code-csharp[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a><span data-ttu-id="232c5-112">名前空間エイリアス</span><span class="sxs-lookup"><span data-stu-id="232c5-112">Namespace Aliases</span></span>  
 <span data-ttu-id="232c5-113">[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)を使用して、[名前空間](../../../csharp/language-reference/keywords/namespace.md)のエイリアスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="232c5-113">The [using Directive](../../../csharp/language-reference/keywords/using-directive.md) can also be used to create an alias for a [namespace](../../../csharp/language-reference/keywords/namespace.md).</span></span> <span data-ttu-id="232c5-114">たとえば、入れ子になった名前空間を含む、以前に作成した名前空間を使用する場合は、次の例のようにエイリアスを宣言して、特定の名前空間を簡単に参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="232c5-114">For example, if you are using a previously written namespace that contains nested namespaces, you might want to declare an alias to provide a shorthand way of referencing one in particular, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a><span data-ttu-id="232c5-115">名前空間を使用するスコープの制御</span><span class="sxs-lookup"><span data-stu-id="232c5-115">Using Namespaces to control scope</span></span>  
 <span data-ttu-id="232c5-116">`namespace` キーワードを使用して、スコープを宣言します。</span><span class="sxs-lookup"><span data-stu-id="232c5-116">The `namespace` keyword is used to declare a scope.</span></span> <span data-ttu-id="232c5-117">プロジェクト内でスコープを作成すると、コードの編成が容易になり、グローバルに一意の型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="232c5-117">The ability to create scopes within your project helps organize code and lets you create globally-unique types.</span></span> <span data-ttu-id="232c5-118">次の例では、入れ子関係にある 2 つの名前空間で `SampleClass` というクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="232c5-118">In the following example, a class titled `SampleClass` is defined in two namespaces, one nested inside the other.</span></span> <span data-ttu-id="232c5-119">[。演算子](../../../csharp/language-reference/operators/member-access-operator.md)を使用して、呼び出されるメソッドを区別します。</span><span class="sxs-lookup"><span data-stu-id="232c5-119">The [. Operator](../../../csharp/language-reference/operators/member-access-operator.md) is used to differentiate which method gets called.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a><span data-ttu-id="232c5-120">完全修飾名</span><span class="sxs-lookup"><span data-stu-id="232c5-120">Fully Qualified Names</span></span>  
 <span data-ttu-id="232c5-121">名前空間と型には、論理階層を示す完全修飾名で表された一意のタイトルが割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="232c5-121">Namespaces and types have unique titles described by fully qualified names that indicate a logical hierarchy.</span></span> <span data-ttu-id="232c5-122">たとえば、ステートメント `A.B` は、`A` が名前空間または型の名前であり、`B` はその内部で入れ子になっていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="232c5-122">For example, the statement `A.B` implies that `A` is the name of the namespace or type, and `B` is nested inside it.</span></span>  
  
 <span data-ttu-id="232c5-123">入れ子になっているクラスと名前空間を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="232c5-123">In the following example, there are nested classes and namespaces.</span></span> <span data-ttu-id="232c5-124">完全修飾名は、各エンティティの後のコメントとして示されています。</span><span class="sxs-lookup"><span data-stu-id="232c5-124">The fully qualified name is indicated as a comment following each entity.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 <span data-ttu-id="232c5-125">上のコード セグメントの各要素の意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="232c5-125">In the previous code segment:</span></span>  
  
-   <span data-ttu-id="232c5-126">名前空間 `N1` はグローバル名前空間のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="232c5-126">The namespace `N1` is a member of the global namespace.</span></span> <span data-ttu-id="232c5-127">その完全修飾名は `N1` です。</span><span class="sxs-lookup"><span data-stu-id="232c5-127">Its fully qualified name is `N1`.</span></span>  
  
-   <span data-ttu-id="232c5-128">名前空間 `N2` は `N1` のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="232c5-128">The namespace `N2` is a member of `N1`.</span></span> <span data-ttu-id="232c5-129">その完全修飾名は `N1.N2` です。</span><span class="sxs-lookup"><span data-stu-id="232c5-129">Its fully qualified name is `N1.N2`.</span></span>  
  
-   <span data-ttu-id="232c5-130">クラス `C1` は `N1` のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="232c5-130">The class `C1` is a member of `N1`.</span></span> <span data-ttu-id="232c5-131">その完全修飾名は `N1.C1` です。</span><span class="sxs-lookup"><span data-stu-id="232c5-131">Its fully qualified name is `N1.C1`.</span></span>  
  
-   <span data-ttu-id="232c5-132">クラス名 `C2` は、このコードでは 2 回使用されています。</span><span class="sxs-lookup"><span data-stu-id="232c5-132">The class name `C2` is used two times in this code.</span></span> <span data-ttu-id="232c5-133">ただし、完全修飾名は異なります。</span><span class="sxs-lookup"><span data-stu-id="232c5-133">However, the fully qualified names are unique.</span></span> <span data-ttu-id="232c5-134">`C2` の最初のインスタンスは `C1` 内で宣言されているため、その完全修飾名は `N1.C1.C2` となります。</span><span class="sxs-lookup"><span data-stu-id="232c5-134">The first instance of `C2` is declared inside `C1`; therefore, its fully qualified name is: `N1.C1.C2`.</span></span> <span data-ttu-id="232c5-135">`C2` の 2 つ目のインスタンスは名前空間 `N2` 内で宣言されているため、その完全修飾名は `N1.N2.C2` となります。</span><span class="sxs-lookup"><span data-stu-id="232c5-135">The second instance of `C2` is declared inside a namespace `N2`; therefore, its fully qualified name is `N1.N2.C2`.</span></span>  
  
 <span data-ttu-id="232c5-136">上のコード セグメントを使用して、次のように新しいクラス メンバー `C3` を名前空間 `N1.N2` に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="232c5-136">Using the previous code segment, you can add a new class member, `C3`, to the namespace `N1.N2` as follows:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 <span data-ttu-id="232c5-137">通常、`::` は名前空間エイリアスを参照する際に使用し、`global::` はグローバル名前空間を参照する際に使用します。`.` は型またはメンバーを修飾する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="232c5-137">In general, use `::` to reference a namespace alias or `global::` to reference the global namespace and `.` to qualify types or members.</span></span>  
  
 <span data-ttu-id="232c5-138">名前空間ではなく型を参照するエイリアスで `::` を使用するのは誤りです。</span><span class="sxs-lookup"><span data-stu-id="232c5-138">It is an error to use `::` with an alias that references a type instead of a namespace.</span></span> <span data-ttu-id="232c5-139">例:</span><span class="sxs-lookup"><span data-stu-id="232c5-139">For example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 <span data-ttu-id="232c5-140">`global` という語は定義済みのエイリアスではないため、`global.X` には特別な意味がないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="232c5-140">Remember that the word `global` is not a predefined alias; therefore, `global.X` does not have any special meaning.</span></span> <span data-ttu-id="232c5-141">`::` と共に使用したときにのみ特別な意味が与えられます。</span><span class="sxs-lookup"><span data-stu-id="232c5-141">It acquires a special meaning only when it is used with `::`.</span></span>  
  
 <span data-ttu-id="232c5-142">`global::` は常にグローバル名前空間を参照し、エイリアスを参照しないので、global という名前のエイリアスを定義すると、コンパイラ警告 CS0440 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="232c5-142">Compiler warning CS0440 is generated if you define an alias named global because `global::` always references the global namespace and not an alias.</span></span> <span data-ttu-id="232c5-143">たとえば、次のコード行では警告が生成されます。</span><span class="sxs-lookup"><span data-stu-id="232c5-143">For example, the following line generates the warning:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 <span data-ttu-id="232c5-144">エイリアスで `::` を使用することをお勧めします。そうすれば、追加の型が予想外に導入されることを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="232c5-144">Using `::` with aliases is a good idea and protects against the unexpected introduction of additional types.</span></span> <span data-ttu-id="232c5-145">たとえば、次の例について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="232c5-145">For example, consider this example:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 <span data-ttu-id="232c5-146">このコードは動作しますが、`Alias` という名前の型が後で導入された場合、`Alias.` は代わりにその型にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="232c5-146">This works, but if a type named `Alias` were to subsequently be introduced, `Alias.` would bind to that type instead.</span></span> <span data-ttu-id="232c5-147">`Alias::Exception` を使用すれば、`Alias` は名前空間エイリアスとして扱われ、型と間違われることがなくなります。</span><span class="sxs-lookup"><span data-stu-id="232c5-147">Using `Alias::Exception` insures that `Alias` is treated as a namespace alias and not mistaken for a type.</span></span>  
  
 <span data-ttu-id="232c5-148">`global` エイリアスの詳細については、「[方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="232c5-148">See the topic [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) for more information regarding the `global` alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232c5-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="232c5-149">See Also</span></span>  
 [<span data-ttu-id="232c5-150">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="232c5-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="232c5-151">名前空間</span><span class="sxs-lookup"><span data-stu-id="232c5-151">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="232c5-152">名前空間キーワード</span><span class="sxs-lookup"><span data-stu-id="232c5-152">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="232c5-153">。演算子</span><span class="sxs-lookup"><span data-stu-id="232c5-153">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="232c5-154">:: 演算子</span><span class="sxs-lookup"><span data-stu-id="232c5-154">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="232c5-155">extern</span><span class="sxs-lookup"><span data-stu-id="232c5-155">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
