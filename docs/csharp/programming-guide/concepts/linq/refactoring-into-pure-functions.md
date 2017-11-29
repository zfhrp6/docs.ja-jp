---
title: "純粋関数へのリファクタリング (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36bb31975523055962fa9572109dab7e2ed47336
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="8e2d9-102">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="8e2d9-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="8e2d9-103">純粋関数型変換で重要なのは、純粋関数を使用してコードをリファクターする方法を理解することです。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e2d9-104">関数型プログラミングでの命名には、一般に純粋関数を使用してプログラムをリファクターする方法が使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="8e2d9-105">Visual Basic および C++ では、この処理がそれぞれの言語の関数を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="8e2d9-106">ただし C# では、関数がメソッドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="8e2d9-107">ここでは、純粋関数が C# のメソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="8e2d9-108">このセクションで既に説明したように、純粋関数には 2 つの実用的な特性があります。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="8e2d9-109">副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-109">It has no side effects.</span></span> <span data-ttu-id="8e2d9-110">この関数は、関数の外部にある変数やあらゆる型のデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="8e2d9-111">一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-111">It is consistent.</span></span> <span data-ttu-id="8e2d9-112">同じ入力データを与えられると、常に同じ出力値を返します。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="8e2d9-113">関数型プログラミングに移行するには、既存のコードをリファクターして不要な副作用や外部依存関係を排除するのが 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="8e2d9-114">この方法で、既存のコードの純粋関数バージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="8e2d9-115">このトピックでは、純粋関数の特徴とそれ以外の関数の特徴について説明します。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="8e2d9-116">「[チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)」チュートリアルでは、WordprocessingML ドキュメントの操作方法を説明し、純粋関数を使用してリファクターする方法を示す 2 つの例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="8e2d9-117">副作用と外部依存関係の排除</span><span class="sxs-lookup"><span data-stu-id="8e2d9-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="8e2d9-118">次の例に示す 2 つの非純粋関数と 1 つの純粋関数を参照して、その違いを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="8e2d9-119">クラス メンバーを変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="8e2d9-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="8e2d9-120">次のコードの `HypenatedConcat` 関数は、クラス内の `aMember` データ メンバーを変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-120">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HypenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HypenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 <span data-ttu-id="8e2d9-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="8e2d9-122">この場合、変更されるデータに `public` アクセスと `private` アクセスのどちらがあるか、またはこのデータが `static` メンバーとインスタンス メンバーのどちらであるかは関係ありません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="8e2d9-123">純粋関数は、関数の外部にあるデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="8e2d9-124">引数を変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="8e2d9-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="8e2d9-125">同じ関数の次のバージョンは、そのパラメーターである `sb` の内容を変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```csharp  
public class Program  
{  
    public static void HypenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HypenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 <span data-ttu-id="8e2d9-126">このバージョンのプログラムは、最初のバージョンと同じ出力を生成します。これは、`HypenatedConcat` 関数が <xref:System.Text.StringBuilder.Append%2A> メンバー関数を呼び出して最初のパラメーターの値 (状態) を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-126">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="8e2d9-127">`HypenatedConcat` はパラメーターを値で渡しますが、それでもこの変更は行われるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-127">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8e2d9-128">参照型の場合、パラメーターを値で渡すと、渡されるオブジェクトへの参照がコピーされて渡されます。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="8e2d9-129">このコピーは、参照変数が新しいオブジェクトに割り当てられるまで、元の参照と同じインスタンス データに関連付けられたままとなります。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="8e2d9-130">パラメーターを変更する場合に、必ずしも関数に参照を渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="8e2d9-131">純粋関数</span><span class="sxs-lookup"><span data-stu-id="8e2d9-131">Pure Function</span></span>  
<span data-ttu-id="8e2d9-132">次のバージョンのプログラムは、`HypenatedConcat` 関数を純粋関数として実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-132">This next version of the program shows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 <span data-ttu-id="8e2d9-133">このバージョンも、同じ出力行 `StringOne-StringTwo` を生成します。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="8e2d9-134">この連結された値を保持するために、中間変数 `s2` が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="8e2d9-135">ローカルには純粋ではないが (つまりローカル変数を宣言して変更する)、グローバルには純粋である関数を作成すると、非常に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="8e2d9-136">このような関数は、必要に応じて構成できる特性を多く備えていますが、関数型プログラミングの複雑な表現方法の一部 (単純なループによる処理を行う場合は再帰を使用する必要があるなど) が省かれています。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="8e2d9-137">標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="8e2d9-137">Standard Query Operators</span></span>  
 <span data-ttu-id="8e2d9-138">標準クエリ演算子の重要な特性は、純粋関数として実装される点です。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="8e2d9-139">詳細については、「[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e2d9-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e2d9-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e2d9-140">See Also</span></span>  
 [<span data-ttu-id="8e2d9-141">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="8e2d9-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="8e2d9-142">関数型プログラミングと命令型プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="8e2d9-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
