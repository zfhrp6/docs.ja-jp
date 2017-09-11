---
title: "方法 : 文字列を比較する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
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
ms.openlocfilehash: 494b9ef1a1e6c8958dd3df2edb44debf32690eeb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-compare-strings-c-programming-guide"></a><span data-ttu-id="e0154-102">方法 : 文字列を比較する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e0154-102">How to: Compare Strings (C# Programming Guide)</span></span>
<span data-ttu-id="e0154-103">文字列を比較する場合、1 つの文字列がその他の文字列よりも大きいか小さいか、または 2 つの文字列が等しいことを示す結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="e0154-103">When you compare strings, you are producing a result that says one string is greater than or less than the other, or that the two strings are equal.</span></span> <span data-ttu-id="e0154-104">*序数に基づく比較*か、*カルチャで区別される比較*のいずれを実行しているかに応じて、結果を決定する規則は異なります。</span><span class="sxs-lookup"><span data-stu-id="e0154-104">The rules by which the result is determined are different depending on whether you are performing *ordinal comparison* or *culture-sensitive comparison*.</span></span> <span data-ttu-id="e0154-105">特定のタスクに正しい種類の比較を使用することが重要です。</span><span class="sxs-lookup"><span data-stu-id="e0154-105">It is important to use the correct kind of comparison for the specific task.</span></span>  
  
 <span data-ttu-id="e0154-106">言語の規則に関係なく、2 つの文字列の値を比較または並べ替える必要がある場合、基本の序数に基づく比較を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0154-106">Use basic ordinal comparisons when you have to compare or sort the values of two strings without regard to linguistic conventions.</span></span> <span data-ttu-id="e0154-107">基本の序数に基づく比較 (`System.StringComparison.Ordinal`) は、大文字と小文字を区別します。つまり、2 つの文字列は、文字レベルで一致している必要があります ("and" は、"And" や "AND" と等しくありません)。</span><span class="sxs-lookup"><span data-stu-id="e0154-107">A basic ordinal comparison (`System.StringComparison.Ordinal`) is case-sensitive, which means that the two strings must match character for character: "and" does not equal "And" or "AND".</span></span> <span data-ttu-id="e0154-108">頻繁に使用される変数の `System.StringComparison.OrdinalIgnoreCase` では、"and"、"And"、および "AND" は一致と見なされます。</span><span class="sxs-lookup"><span data-stu-id="e0154-108">A frequently-used variation is `System.StringComparison.OrdinalIgnoreCase`, which will match "and", "And", and "AND".</span></span> <span data-ttu-id="e0154-109">`StringComparison.OrdinalIgnoreCase` は、ファイル名、パス名、ネットワーク パス、およびユーザーのコンピューターのロケールに基づいて変更されない値を持つその他の文字列を比較するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0154-109">`StringComparison.OrdinalIgnoreCase` is often used to compare file names, path names, network paths, and any other string whose value does not change based on the locale of the user's computer.</span></span> <span data-ttu-id="e0154-110">詳細については、「<xref:System.StringComparison?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0154-110">For more information, see <xref:System.StringComparison?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="e0154-111">通常、文字および文字列の並べ替え規則は、ユーザーのコンピューターのロケールによって異なる可能性があるため、カルチャで区別される比較は、エンド ユーザーが入力する文字列を比較および並べ替えるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0154-111">Culture-sensitive comparisons are typically used to compare and sort strings that are input by end users, because the characters and sorting conventions of these strings might vary depending on the locale of the user's computer.</span></span> <span data-ttu-id="e0154-112">同一の文字を含む文字列でも、現在のスレッドのカルチャに応じて、異なる方法で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e0154-112">Even strings that contain identical characters might sort differently depending on the culture of the current thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0154-113">文字列を比較する場合、実行する比較の種類を明示的に指定するメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0154-113">When you compare strings, you should use the methods that explicitly specify what kind of comparison you intend to perform.</span></span> <span data-ttu-id="e0154-114">これらのメソッドを使用すると、コードを保守しやすく、読みやすくすることができます。</span><span class="sxs-lookup"><span data-stu-id="e0154-114">This makes your code much more maintainable and readable.</span></span> <span data-ttu-id="e0154-115">可能な限り、<xref:System.StringComparison> 列挙型のパラメーターを取る、<xref:System.String?displayProperty=fullName> と <xref:System.Array?displayProperty=fullName> クラスのメソッドのオーバーロードを使用し、どの種類の比較を実行するか指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e0154-115">Whenever possible, use the overloads of the methods of the <xref:System.String?displayProperty=fullName> and <xref:System.Array?displayProperty=fullName> classes that take a <xref:System.StringComparison> enumeration parameter, so that you can specify which type of comparison to perform.</span></span> <span data-ttu-id="e0154-116">文字列を比較する場合、`==` 演算子と `!=` 演算子を使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e0154-116">It is best to avoid using the `==` and `!=` operators when you compare strings.</span></span> <span data-ttu-id="e0154-117">なお、いずれのオーバーロードも <xref:System.StringComparison> を取ることはないため、ここでは <xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドは使用しません。</span><span class="sxs-lookup"><span data-stu-id="e0154-117">Also, avoid using the <xref:System.String.CompareTo%2A?displayProperty=fullName> instance methods because none of the overloads takes a <xref:System.StringComparison>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0154-118">例</span><span class="sxs-lookup"><span data-stu-id="e0154-118">Example</span></span>  
 <span data-ttu-id="e0154-119">次の例では、ユーザーのコンピューターのロケールに基づいて、値が変更されない文字列を正しく比較する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0154-119">The following example shows how to correctly compare strings whose values will not change based on the locale of the user's computer.</span></span> <span data-ttu-id="e0154-120">さらに、C# の*文字列のインターン*機能も示しています。</span><span class="sxs-lookup"><span data-stu-id="e0154-120">In addition, it also demonstrates the *string interning* feature of C#.</span></span> <span data-ttu-id="e0154-121">プログラムで 2 つ以上の同じ文字列変数を宣言すると、コンパイラはそれらをすべて同じ場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="e0154-121">When a program declares two or more identical string variables, the compiler stores them all in the same location.</span></span> <span data-ttu-id="e0154-122"><xref:System.Object.ReferenceEquals%2A> メソッドを呼び出すと、2 つの文字列がメモリ内の同じオブジェクトを実際に参照していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e0154-122">By calling the <xref:System.Object.ReferenceEquals%2A> method, you can see that the two strings actually refer to the same object in memory.</span></span> <span data-ttu-id="e0154-123">インターンを回避するには、次の例のように、<xref:System.String.Copy%2A?displayProperty=fullName> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e0154-123">Use the <xref:System.String.Copy%2A?displayProperty=fullName> method to avoid interning, as shown in the example.</span></span>  
  
 <span data-ttu-id="e0154-124">[!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e0154-124">[!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0154-125">例</span><span class="sxs-lookup"><span data-stu-id="e0154-125">Example</span></span>  
 <span data-ttu-id="e0154-126">次の例では、<xref:System.StringComparison> 列挙型を取る <xref:System.String?displayProperty=fullName> メソッドを使用して、推奨の方法で文字列を比較する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e0154-126">The following example shows how to compare strings the preferred way by using the <xref:System.String?displayProperty=fullName> methods that take a <xref:System.StringComparison> enumeration.</span></span> <span data-ttu-id="e0154-127">なお、いずれのオーバーロードも <xref:System.StringComparison> を取ることはないため、ここでは <xref:System.String.CompareTo%2A?displayProperty=fullName> インスタンス メソッドは使用していません。</span><span class="sxs-lookup"><span data-stu-id="e0154-127">Note that the <xref:System.String.CompareTo%2A?displayProperty=fullName> instance methods are not used here, because none of the overloads takes a <xref:System.StringComparison>.</span></span>  
  
 <span data-ttu-id="e0154-128">[!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e0154-128">[!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0154-129">例</span><span class="sxs-lookup"><span data-stu-id="e0154-129">Example</span></span>  
 <span data-ttu-id="e0154-130">次の例では、<xref:System.StringComparer?displayProperty=fullName> パラメーターを受け取る静的 <xref:System.Array> メソッドを使用したカルチャで区別される手法で、配列内の文字列を検索および並べ替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0154-130">The following example shows how to sort and search for strings in an array in a culture-sensitive manner by using the static <xref:System.Array> methods that take a <xref:System.StringComparer?displayProperty=fullName> parameter.</span></span>  
  
 <span data-ttu-id="e0154-131">[!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e0154-131">[!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]</span></span>  
  
 <span data-ttu-id="e0154-132"><xref:System.Collections.Hashtable?displayProperty=fullName>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>、および <xref:System.Collections.Generic.List%601?displayProperty=fullName> などのコレクション クラスには、要素またはキーの種類が `string` の場合、<xref:System.StringComparer?displayProperty=fullName> パラメーターを取るコンストラクターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e0154-132">Collection classes such as <xref:System.Collections.Hashtable?displayProperty=fullName>, <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>, and <xref:System.Collections.Generic.List%601?displayProperty=fullName> have constructors that take a <xref:System.StringComparer?displayProperty=fullName> parameter when the type of the elements or keys is `string`.</span></span> <span data-ttu-id="e0154-133">通常は、これらのコンストラクターをできるだけ使用し、`Ordinal` または `OrdinalIgnoreCase` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0154-133">In general, you should use these constructors whenever possible, and specify either `Ordinal` or `OrdinalIgnoreCase`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0154-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0154-134">See Also</span></span>  
 <span data-ttu-id="e0154-135"><xref:System.Globalization.CultureInfo?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e0154-135"><xref:System.Globalization.CultureInfo?displayProperty=fullName></span></span>   
 <span data-ttu-id="e0154-136"><xref:System.StringComparer?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e0154-136"><xref:System.StringComparer?displayProperty=fullName></span></span>   
 <span data-ttu-id="e0154-137">[文字列](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="e0154-137">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="e0154-138">[文字列の比較](../../../standard/base-types/comparing.md) </span><span class="sxs-lookup"><span data-stu-id="e0154-138">[Comparing Strings](../../../standard/base-types/comparing.md) </span></span>  
 [<span data-ttu-id="e0154-139">アプリケーションのグローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="e0154-139">Globalizing and Localizing Applications</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

