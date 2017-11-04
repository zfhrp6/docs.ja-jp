---
title: "switch キーワード (C# リファレンス)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66528c9804b74b0bba088627b3116be804c65eb0
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="switch-c-reference"></a><span data-ttu-id="e62d2-102">switch (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e62d2-102">switch (C# Reference)</span></span>
<span data-ttu-id="e62d2-103">`switch` ステートメントは選択ステートメントです。このステートメントは、実行する 1 つの "*switch セクション*" を候補のリストから "*match 式*" によるパターン マッチに基づいて選択します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 [!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

<span data-ttu-id="e62d2-104">`switch` ステートメントは、1 つの式が 3 つ以上の条件に対してテストされる場合に、[if-else](if-else.md) コンストラクトの代わりとしてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="e62d2-105">たとえば、次の `switch` ステートメントは、`Color` 型の変数に 3 つの値のいずれかが含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

<span data-ttu-id="e62d2-106">これは、`if`-`else` コンストラクトを使用する次の例に相当します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a><span data-ttu-id="e62d2-107">match 式</span><span class="sxs-lookup"><span data-stu-id="e62d2-107">The match expression</span></span>

<span data-ttu-id="e62d2-108">match 式は、`case` ラベルのパターンと照合する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="e62d2-109">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="e62d2-110">C# 6 では、match 式は、次の型の値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="e62d2-111">[char](char.md)。</span><span class="sxs-lookup"><span data-stu-id="e62d2-111">a [char](char.md).</span></span>
- <span data-ttu-id="e62d2-112">[string](string.md)。</span><span class="sxs-lookup"><span data-stu-id="e62d2-112">a [string](string.md).</span></span>
- <span data-ttu-id="e62d2-113">[bool](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="e62d2-113">a [bool](bool.md).</span></span> 
- <span data-ttu-id="e62d2-114">整数値。[int](int.md)、[long](long.md) など。</span><span class="sxs-lookup"><span data-stu-id="e62d2-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="e62d2-115">[enum](enum.md)値。</span><span class="sxs-lookup"><span data-stu-id="e62d2-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="e62d2-116">C# 7 以降は、match 式は NULL 以外の式にできます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-116">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="e62d2-117">switch セクション</span><span class="sxs-lookup"><span data-stu-id="e62d2-117">The switch section</span></span>
 
 <span data-ttu-id="e62d2-118">`switch` ステートメントには、1 つ以上の switch セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="e62d2-119">各 switch セクションには、1 つ以上の "*case ラベル*" と、その後に続く 1 つ以上のステートメントのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-119">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="e62d2-120">次の例に、3 つの switch セクションを持つ簡単な `switch` ステートメントを示します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-120">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="e62d2-121">各 switch セクションには、`case 1:` のような case ラベルと、2 つのステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-121">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="e62d2-122">`switch` ステートメントには、任意の数の switch セクションを含めることができます。また、次の例に示すように、各セクションに 1 つ以上の case ラベルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-122">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="e62d2-123">ただし、複数の case ラベルで同じ式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-123">However, no two case labels may contain the same expression.</span></span>  

 [!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 <span data-ttu-id="e62d2-124">1 つの switch ステートメントでは、1 つの switch セクションのみが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-124">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="e62d2-125">C# では 1 つの switch セクションから次のセクションへ実行が連続することが許可されません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-125">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="e62d2-126">このため、次のコードでは、コンパイラ エラー CS0163 "コントロールはひとつの case ラベル (<case label>) から別のラベルへ流れ落ちることはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-126">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>   

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
<span data-ttu-id="e62d2-127">この要件は、通常、[break](break.md) ステートメント、[goto](goto.md) ステートメント、または [return](return.md) ステートメントを使用して、switch セクションを明示的に終了することによって満たされます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-127">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="e62d2-128">ただし、次のコードも有効です。このコードでは、プログラムの制御が `default` switch セクションにフォール スルー (流れ落ちる、case ラベルを超えてコードを実行することが) できないためです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-128">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 [!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 <span data-ttu-id="e62d2-129">match 式に一致する case ラベルが含まれた switch セクションにおけるステートメント リストの実行は、ステートメント リストに沿って最初のステートメントから順に開始され、通常は、`break`、`goto case`、`goto label`、`return`、または`throw` などのジャンプ ステートメントに達するまで続きます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-129">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="e62d2-130">この時点で、制御は `switch` ステートメントの外側、または他の case ラベルに移動します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-130">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="e62d2-131">`goto` ステートメントを使用する場合は、制御を constant ラベルに転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-131">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="e62d2-132">この制約が必要になるのは、非 constant ラベルに制御を転送しようとすると望ましくない副作用 (コード内の意図しない場所に制御を転送してしまったり、無限ループを作成してしまったりなど) が生じる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-132">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="e62d2-133">case ラベル</span><span class="sxs-lookup"><span data-stu-id="e62d2-133">Case labels</span></span>

 <span data-ttu-id="e62d2-134">各 case ラベルで、match 式と比較するためのパターンを指定します (前の例では `caseSwitch` 変数)。</span><span class="sxs-lookup"><span data-stu-id="e62d2-134">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="e62d2-135">一致すると、**最初の**一致 case を含む switch セクションに制御が移ります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-135">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="e62d2-136">match 式と一致する case ラベル パターンがない場合は、`default` case ラベルがあれば、制御はそのラベルを含むセクションに移ります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-136">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="e62d2-137">`default` case がない場合は、どの switch セクションのステートメントも実行されず、制御は `switch` ステートメント外に移ります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-137">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="e62d2-138">`switch` ステートメントとパターン マッチングの詳細については、「[`switch` ステートメントによるパターン マッチング](#pattern)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e62d2-138">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="e62d2-139">C# 6 でサポートされるのは定数パターンのみで、定数値の繰り返しは許可されません。このため、case ラベルでは相互に排他的な値が定義され、match 式と一致するのは 1 つのパターンだけです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-139">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="e62d2-140">そのため、`case` ステートメントが表示される順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-140">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="e62d2-141">一方、C# 7 では他のパターンがサポートされているため、case ラベルで定義する値が相互に排他的である必要はなく、match 式と一致するパターンが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-141">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="e62d2-142">最初に一致するパターンが含まれた switch セクションのステートメントのみが実行されるので、ここでは、`case` ステートメントが表示される順序が重要になってきます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-142">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="e62d2-143">C# によって switch セクションが検出され、その switch セクションの case ステートメントが前のステートメントと同じだったり、そのステートメントのサブセットだったりすると、コンパイラ エラー CS8120 "switch case は既に以前のケースで処理されています" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-143">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="e62d2-144">次の例は、相互に排他的でない各種パターンを使用する `switch` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-144">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="e62d2-145">`case 0:` switch セクションを移動し、そのセクションが `switch` ステートメントの最初のセクションでなくなると、C# によってコンパイラ エラーが生成されます。値がゼロの整数は、整数すべてのサブセットであるためです。これは、`case int val` ステートメントで定義されているパターンです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-145">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 [!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

<span data-ttu-id="e62d2-146">この問題を修正し、コンパイラの警告が表示されないようにするには、次の 2 つのいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-146">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="e62d2-147">switch セクションの順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="e62d2-147">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="e62d2-148">`case` ラベルで </a name="when">when 句</a> を使用する。</span><span class="sxs-lookup"><span data-stu-id="e62d2-148">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="e62d2-149">`default` case</span><span class="sxs-lookup"><span data-stu-id="e62d2-149">The `default` case</span></span>

<span data-ttu-id="e62d2-150">`default` case では、match 式がどの `case` ラベルとも一致しない場合に実行する switch セクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-150">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="e62d2-151">`default` case を指定しない場合、match 式がどの `case` ラベルとも一致しないと、プログラム フローが `switch` ステートメントにフォール スルーします。</span><span class="sxs-lookup"><span data-stu-id="e62d2-151">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="e62d2-152">`default` case は、`switch` ステートメントで任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-152">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="e62d2-153">この case は、ソース コード内での順序に関係なく、すべての `case` ラベルが評価された後、最後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-153">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="e62d2-154">`switch` ステートメントによる <a name="pattern" /> パターン マッチング</span><span class="sxs-lookup"><span data-stu-id="e62d2-154"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="e62d2-155">各 `case` ステートメントで定義されたパターンが match 式と一致した場合に、switch セクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-155">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="e62d2-156">定数パターンは、すべてのバージョンの C# でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-156">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="e62d2-157">それ以外のパターンは、C# 7 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-157">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="e62d2-158">定数パターン</span><span class="sxs-lookup"><span data-stu-id="e62d2-158">Constant pattern</span></span> 

<span data-ttu-id="e62d2-159">定数パターンでは、match 式が、指定された定数と等しいかどうかがテストされます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-159">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="e62d2-160">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-160">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="e62d2-161">ここで *constant* はテスト対象の値です。</span><span class="sxs-lookup"><span data-stu-id="e62d2-161">where *constant* is the value to test for.</span></span> <span data-ttu-id="e62d2-162">*constant* には、次のいずれかの定数式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-162">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="e62d2-163">[bool](bool.md) リテラル。`true` または `false`。</span><span class="sxs-lookup"><span data-stu-id="e62d2-163">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="e62d2-164">任意の整数定数。[int](int.md)、[long](long.md)、[byte](byte.md) など。</span><span class="sxs-lookup"><span data-stu-id="e62d2-164">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="e62d2-165">宣言された `const` 変数の名前。</span><span class="sxs-lookup"><span data-stu-id="e62d2-165">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="e62d2-166">列挙定数。</span><span class="sxs-lookup"><span data-stu-id="e62d2-166">An enumeration constant.</span></span>
- <span data-ttu-id="e62d2-167">[char](char.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="e62d2-167">A [char](char.md) literal.</span></span>
- <span data-ttu-id="e62d2-168">[string](string.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="e62d2-168">A [string](string.md) literal.</span></span>

<span data-ttu-id="e62d2-169">定数式は以下のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-169">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="e62d2-170">*expr* と *constant* が整数型の場合、式から `true` が返されるかどうか (つまり、`expr == constant` であるかどうか) が C# の等値演算子によって判定されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-170">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="e62d2-171">それ以外の場合、式の値は静的 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) メソッドの呼び出しによって判定されます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-171">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="e62d2-172">次の例では、定数パターンを使用して、特定の日付が、週末か、週の開始日または最終日か、週の途中かを判断します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-172">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="e62d2-173">つまり、現在の日付の <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> プロパティを、<xref:System.DayOfWeek> 列挙のメンバーと照合します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-173">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span> 

[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="e62d2-174">次の例では、定数パターンを使用して、自動コーヒー メーカーをシミュレートするコンソール アプリケーションのユーザー入力を処理します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-174">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 [!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a><span data-ttu-id="e62d2-175">型パターン</span><span class="sxs-lookup"><span data-stu-id="e62d2-175">Type pattern</span></span>

<span data-ttu-id="e62d2-176">型パターンを使用すると、型の評価と変換を簡潔に記述できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-176">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="e62d2-177">`switch` ステートメントと共に使用してパターン マッチングを実行すると、指定された型に式を変換できるかどうかがテストされ、変換できる場合は、その型の変数にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-177">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="e62d2-178">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-178">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="e62d2-179">ここで *type* は、*expr* の結果が変換される型の名前、*varname* は、一致した場合に *expr* の結果が変換されるオブジェクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-179">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="e62d2-180">以下のいずれかの条件が true である場合に `case` 式は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-180">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="e62d2-181">*expr* が *type* と同じ型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="e62d2-181">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="e62d2-182">*expr* が *type* から派生した型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="e62d2-182">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="e62d2-183">つまり、*expr* の結果を *type* のインスタンスにアップキャストできる。</span><span class="sxs-lookup"><span data-stu-id="e62d2-183">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="e62d2-184">*expr* のコンパイル時の型が *type* の基底クラスであり、*expr* の実行時の型が *type* または *type* から派生した型である。</span><span class="sxs-lookup"><span data-stu-id="e62d2-184">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="e62d2-185">変数の "*コンパイル時の型*" とは、その変数の型宣言で定義されている型です。</span><span class="sxs-lookup"><span data-stu-id="e62d2-185">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="e62d2-186">変数の "*実行時の型*" とは、その変数に代入されているインスタンスの型です。</span><span class="sxs-lookup"><span data-stu-id="e62d2-186">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="e62d2-187">*expr* が、*type* インターフェイスを実装する型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="e62d2-187">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="e62d2-188">case 式が true の場合は、*varname* が確実に割り当てられ、switch セクションにのみローカル スコープが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-188">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="e62d2-189">`null` は型とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-189">Note that `null` does not match a type.</span></span> <span data-ttu-id="e62d2-190">`null` を一致させるには、次の `case` ラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-190">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="e62d2-191">次の例では、型パターンを使用して、さまざまな種類のコレクション型に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e62d2-191">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="e62d2-192">パターン マッチングを使用しない場合、このコードは次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-192">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="e62d2-193">型パターン マッチングを使用することにより、変換結果が `null` であるかどうかをテストしたり、キャストを繰り返したりする必要がなくなるため、コードがよりコンパクトで読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="e62d2-193">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="e62d2-194">`case` ステートメントおよび `when` 句</span><span class="sxs-lookup"><span data-stu-id="e62d2-194">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="e62d2-195">C# 7 以降では、case ステートメントは相互に排他的である必要がないため、`when` 句を追加して、case ステートメントを true に評価するために満たされなければならない条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-195">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="e62d2-196">`when` 句には、ブール値を返す任意の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e62d2-196">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="e62d2-197">`when` 句を使用すると、match 式の値が `null` のときに、switch セクションが実行されないようにできます。これは、この句の一般的な使用方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="e62d2-197">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="e62d2-198">次の例では、`Shape` 基底クラス、`Shape` から派生する `Rectangle` クラス、および `Rectangle` から派生する `Square` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="e62d2-199">ここでは `when` 句を使用して、同じ長さと幅が割り当てられている `Rectangle` オブジェクトが、`Square` オブジェクトとしてインスタンス化されていなくても、`ShowShapeInfo` によって確実に `Square` として処理されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="e62d2-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="e62d2-200">このメソッドは、`null` オブジェクトの情報や、面積がゼロの図形の情報を表示しようとしません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
<span data-ttu-id="e62d2-201">この例で、`Shape`オブジェクトが `null` かどうかをテストしようとする `when` 句は実行されません。</span><span class="sxs-lookup"><span data-stu-id="e62d2-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="e62d2-202">`null` をテストするための正しい型パターンは `case null:` です。</span><span class="sxs-lookup"><span data-stu-id="e62d2-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e62d2-203">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e62d2-203">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e62d2-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="e62d2-204">See Also</span></span>  

 <span data-ttu-id="e62d2-205">[C# リファレンス](../index.md) </span><span class="sxs-lookup"><span data-stu-id="e62d2-205">[C# Reference](../index.md) </span></span>  
 <span data-ttu-id="e62d2-206">[C# プログラミング ガイド](../../programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e62d2-206">[C# Programming Guide](../../programming-guide/index.md) </span></span>  
 <span data-ttu-id="e62d2-207">[C# のキーワード](index.md) </span><span class="sxs-lookup"><span data-stu-id="e62d2-207">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="e62d2-208">[if-else](if-else.md) </span><span class="sxs-lookup"><span data-stu-id="e62d2-208">[if-else](if-else.md) </span></span>  
 [<span data-ttu-id="e62d2-209">パターン一致</span><span class="sxs-lookup"><span data-stu-id="e62d2-209">Pattern Matching</span></span>](../../pattern-matching.md)   
 

 
