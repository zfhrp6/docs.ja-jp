---
title: "=&gt; 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.assetid: 8c899251-dafa-4594-bec7-243b39072880
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 45d4753724ed094408e8cbc5353998a67071b0e4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="d5e80-102">=&gt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d5e80-102">=&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="d5e80-103">`=>` トークンはラムダ演算子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d5e80-103">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="d5e80-104">これは、左側の入力変数を右側のラムダ本体から分けるために*ラムダ式*で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5e80-104">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="d5e80-105">ラムダ式はインライン式の一種で匿名メソッドと似ていますが、それよりも柔軟性があります。この式はメソッド構文で表される LINQ クエリで広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="d5e80-105">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="d5e80-106">詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5e80-106">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="d5e80-107">次の例では、文字列の配列の最も短い文字列の長さを検索して表示する 2 とおりの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d5e80-107">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="d5e80-108">この例の最初の部分では、`words` の配列の各要素にラムダ式 (`w => w.Length`) を適用し、<xref:System.Linq.Enumerable.Min%2A> メソッドを使用して最小の長さを検索します。</span><span class="sxs-lookup"><span data-stu-id="d5e80-108">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="d5e80-109">比較のために、例の 2 番目の部分では、同じ機能を実行するためにクエリ構文を使用する長いソリューションを示します。</span><span class="sxs-lookup"><span data-stu-id="d5e80-109">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5e80-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d5e80-110">Remarks</span></span>  
 <span data-ttu-id="d5e80-111">`=>` 演算子と代入演算子 (`=`) は優先順位が同じで、結合規則が右から左です。</span><span class="sxs-lookup"><span data-stu-id="d5e80-111">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="d5e80-112">入力変数の型を明示的に指定することができます。また、コンパイラで型を推測することもできます。いずれの場合も、変数はコンパイル時に厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="d5e80-112">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="d5e80-113">型を指定する場合は、次の例のように、型名と変数名をかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e80-113">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
## <a name="example"></a><span data-ttu-id="d5e80-114">例</span><span class="sxs-lookup"><span data-stu-id="d5e80-114">Example</span></span>  
 <span data-ttu-id="d5e80-115">次の例は、2 つの引数を受け取る標準クエリ演算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> のオーバーロードのラムダ式を記述する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d5e80-115">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> that takes two arguments.</span></span> <span data-ttu-id="d5e80-116">ラムダ式には複数のパラメーターがあるため、パラメーターをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5e80-116">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="d5e80-117">2 番目のパラメーター `index` は、コレクション内の現在の要素のインデックスを表します。</span><span class="sxs-lookup"><span data-stu-id="d5e80-117">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="d5e80-118">`Where` 式は、長さが配列内のインデックスの位置より短い文字列をすべて返します。</span><span class="sxs-lookup"><span data-stu-id="d5e80-118">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5e80-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5e80-119">See Also</span></span>  
 <span data-ttu-id="d5e80-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5e80-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d5e80-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5e80-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d5e80-122">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="d5e80-122">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

