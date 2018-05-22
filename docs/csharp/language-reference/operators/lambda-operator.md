---
title: =&gt; 演算子 (C# リファレンス)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: d1565e262fbd3ebcee2d1576a2a0c8ed3ba8ce38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="4267d-102">=&gt; 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4267d-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="4267d-103">C# では、`=>` 演算子を 2 通りの方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4267d-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="4267d-104">[ラムダ式](../../lambda-expressions.md)の[ラムダ演算子](#lamba-operator)として使用する場合、入力変数とラムダ本体が切り離されます。</span><span class="sxs-lookup"><span data-stu-id="4267d-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="4267d-105">[式本体の定義](#expression-body-definition)で、メンバー名とメンバー実装が切り離されます。</span><span class="sxs-lookup"><span data-stu-id="4267d-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="4267d-106">ラムダ演算子</span><span class="sxs-lookup"><span data-stu-id="4267d-106">Lambda operator</span></span>

<span data-ttu-id="4267d-107">`=>` トークンはラムダ演算子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4267d-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="4267d-108">これは、左側の入力変数を右側のラムダ本体から分けるために*ラムダ式*で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4267d-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="4267d-109">ラムダ式はインライン式の一種で匿名メソッドと似ていますが、それよりも柔軟性があります。この式はメソッド構文で表される LINQ クエリで広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="4267d-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="4267d-110">詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4267d-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="4267d-111">次の例では、文字列の配列の最も短い文字列の長さを検索して表示する 2 とおりの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4267d-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="4267d-112">この例の最初の部分では、`words` の配列の各要素にラムダ式 (`w => w.Length`) を適用し、<xref:System.Linq.Enumerable.Min%2A> メソッドを使用して最小の長さを検索します。</span><span class="sxs-lookup"><span data-stu-id="4267d-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="4267d-113">比較のために、例の 2 番目の部分では、同じ機能を実行するためにクエリ構文を使用する長いソリューションを示します。</span><span class="sxs-lookup"><span data-stu-id="4267d-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
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
  
### <a name="remarks"></a><span data-ttu-id="4267d-114">コメント</span><span class="sxs-lookup"><span data-stu-id="4267d-114">Remarks</span></span>  
 <span data-ttu-id="4267d-115">`=>` 演算子と代入演算子 (`=`) は優先順位が同じで、結合規則が右から左です。</span><span class="sxs-lookup"><span data-stu-id="4267d-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="4267d-116">入力変数の型を明示的に指定することができます。また、コンパイラで型を推測することもできます。いずれの場合も、変数はコンパイル時に厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="4267d-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="4267d-117">型を指定する場合は、次の例のように、型名と変数名をかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4267d-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="4267d-118">例</span><span class="sxs-lookup"><span data-stu-id="4267d-118">Example</span></span>  
 <span data-ttu-id="4267d-119">次の例は、2 つの引数を受け取る標準クエリ演算子 <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> のオーバーロードのラムダ式を記述する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4267d-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="4267d-120">ラムダ式には複数のパラメーターがあるため、パラメーターをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4267d-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="4267d-121">2 番目のパラメーター `index` は、コレクション内の現在の要素のインデックスを表します。</span><span class="sxs-lookup"><span data-stu-id="4267d-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="4267d-122">`Where` 式は、長さが配列内のインデックスの位置より短い文字列をすべて返します。</span><span class="sxs-lookup"><span data-stu-id="4267d-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
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
## <a name="expression-body-definition"></a><span data-ttu-id="4267d-123">式本体の定義</span><span class="sxs-lookup"><span data-stu-id="4267d-123">Expression body definition</span></span>

<span data-ttu-id="4267d-124">式本体の定義を使用すると、メンバーの実装が簡潔でわかりやすい形式になります。</span><span class="sxs-lookup"><span data-stu-id="4267d-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="4267d-125">一般的な構文は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4267d-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="4267d-126">この *expression* には有効な式を指定します。</span><span class="sxs-lookup"><span data-stu-id="4267d-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="4267d-127">メンバーの戻り値の型が `void` の場合か、メンバーがコンストラクターかファイナライザーの場合にのみ、*式*は*ステートメント式*になります。</span><span class="sxs-lookup"><span data-stu-id="4267d-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="4267d-128">メソッドとプロパティの get ステートメントの場合、C# 6 以降で式本体の定義を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4267d-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="4267d-129">コンストラクター、ファイナライザー、プロパティの set ステートメント、インデクサーの場合、C# 7 以降で式本体の定義を利用できます。</span><span class="sxs-lookup"><span data-stu-id="4267d-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="4267d-130">`Person.ToString` メソッドの式本体の定義は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4267d-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="4267d-131">次のメソッド定義を短くしたものです。</span><span class="sxs-lookup"><span data-stu-id="4267d-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="4267d-132">式本体の定義の詳細については、[式形式メンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4267d-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4267d-133">参照</span><span class="sxs-lookup"><span data-stu-id="4267d-133">See Also</span></span>  
<span data-ttu-id="4267d-134">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4267d-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="4267d-135">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4267d-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="4267d-136">[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="4267d-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="4267d-137">[式形式のメンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)</span><span class="sxs-lookup"><span data-stu-id="4267d-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>