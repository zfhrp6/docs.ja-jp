---
title: 純粋関数 (Visual Basic) へのリファクタリング
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 207b77ff50cd2aaeede758db69b48c8f29a16ab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654262"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="d08d1-102">純粋関数 (Visual Basic) へのリファクタリング</span><span class="sxs-lookup"><span data-stu-id="d08d1-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="d08d1-103">純粋関数型変換で重要なのは、純粋関数を使用してコードをリファクターする方法を理解することです。</span><span class="sxs-lookup"><span data-stu-id="d08d1-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="d08d1-104">このセクションで既に説明したように、純粋関数には 2 つの実用的な特性があります。</span><span class="sxs-lookup"><span data-stu-id="d08d1-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="d08d1-105">副作用がありません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-105">It has no side effects.</span></span> <span data-ttu-id="d08d1-106">この関数は、関数の外部にある変数やあらゆる型のデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="d08d1-107">一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="d08d1-107">It is consistent.</span></span> <span data-ttu-id="d08d1-108">同じ入力データを与えられると、常に同じ出力値を返します。</span><span class="sxs-lookup"><span data-stu-id="d08d1-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="d08d1-109">関数型プログラミングに移行するには、既存のコードをリファクターして不要な副作用や外部依存関係を排除するのが 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="d08d1-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="d08d1-110">この方法で、既存のコードの純粋関数バージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d08d1-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="d08d1-111">このトピックでは、純粋関数の特徴とそれ以外の関数の特徴について説明します。</span><span class="sxs-lookup"><span data-stu-id="d08d1-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="d08d1-112">[チュートリアル: WordprocessingML ドキュメント (Visual Basic の場合) 内のコンテンツの操作](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)チュートリアル、WordprocessingML ドキュメントを操作する方法を示していて、純粋関数を使用してリファクターする方法の 2 つの例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d08d1-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="d08d1-113">副作用と外部依存関係の排除</span><span class="sxs-lookup"><span data-stu-id="d08d1-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="d08d1-114">次の例に示す 2 つの非純粋関数と 1 つの純粋関数を参照して、その違いを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d08d1-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="d08d1-115">クラス メンバーを変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="d08d1-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="d08d1-116">次のコードの `HypenatedConcat` 関数は、クラス内の `aMember` データ メンバーを変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d08d1-117">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d08d1-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="d08d1-118">無関係に変更されるデータがあるかどうか注意`public`または`private`にアクセスするか、`shared`メンバーまたはインスタンス メンバーです。</span><span class="sxs-lookup"><span data-stu-id="d08d1-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="d08d1-119">純粋関数は、関数の外部にあるデータを一切変更しません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="d08d1-120">引数を変更する非純粋関数</span><span class="sxs-lookup"><span data-stu-id="d08d1-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="d08d1-121">同じ関数の次のバージョンは、そのパラメーターである `sb` の内容を変更するため、純粋関数ではありません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d08d1-122">このバージョンのプログラムは、最初のバージョンと同じ出力を生成します。これは、`HypenatedConcat` 関数が <xref:System.Text.StringBuilder.Append%2A> メンバー関数を呼び出して最初のパラメーターの値 (状態) を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="d08d1-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="d08d1-123">`HypenatedConcat` はパラメーターを値で渡しますが、それでもこの変更は行われるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="d08d1-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d08d1-124">参照型の場合、パラメーターを値で渡すと、渡されるオブジェクトへの参照がコピーされて渡されます。</span><span class="sxs-lookup"><span data-stu-id="d08d1-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="d08d1-125">このコピーは、参照変数が新しいオブジェクトに割り当てられるまで、元の参照と同じインスタンス データに関連付けられたままとなります。</span><span class="sxs-lookup"><span data-stu-id="d08d1-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="d08d1-126">パラメーターを変更する場合に、必ずしも関数に参照を渡す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d08d1-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="d08d1-127">純粋関数</span><span class="sxs-lookup"><span data-stu-id="d08d1-127">Pure Function</span></span>  
 <span data-ttu-id="d08d1-128">次のバージョンのプログラムは、`HypenatedConcat` 関数を純粋関数として実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d08d1-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
```vb  
Module Module1  
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String  
        Return (s & "-" & appendStr)  
    End Function  
  
    Sub Main()  
        Dim s1 As String = "StringOne"  
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")  
        Console.WriteLine(s2)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d08d1-129">このバージョンも、同じ出力行 `StringOne-StringTwo` を生成します。</span><span class="sxs-lookup"><span data-stu-id="d08d1-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="d08d1-130">この連結された値を保持するために、中間変数 `s2` が使用されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d08d1-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="d08d1-131">ローカルには純粋ではないが (つまりローカル変数を宣言して変更する)、グローバルには純粋である関数を作成すると、非常に便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="d08d1-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="d08d1-132">このような関数は、必要に応じて構成できる特性を多く備えていますが、関数型プログラミングの複雑な表現方法の一部 (単純なループによる処理を行う場合は再帰を使用する必要があるなど) が省かれています。</span><span class="sxs-lookup"><span data-stu-id="d08d1-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="d08d1-133">標準クエリ演算子</span><span class="sxs-lookup"><span data-stu-id="d08d1-133">Standard Query Operators</span></span>  
 <span data-ttu-id="d08d1-134">標準クエリ演算子の重要な特性は、純粋関数として実装される点です。</span><span class="sxs-lookup"><span data-stu-id="d08d1-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="d08d1-135">詳細については、次を参照してください。[標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="d08d1-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08d1-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="d08d1-136">See Also</span></span>  
 [<span data-ttu-id="d08d1-137">純粋関数型変換 (Visual Basic) の概要</span><span class="sxs-lookup"><span data-stu-id="d08d1-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="d08d1-138">関数型プログラミングと命令型プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d08d1-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
