---
title: "switch キーワード (C# リファレンス)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
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
ms.sourcegitcommit: 387c8c7e44ab818ca97e686330746f50df091bb9
ms.openlocfilehash: 5c151e3bbd46212f1234d46ff05d389f2384ca0e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/01/2017

---
# <a name="switch-c-reference"></a><span data-ttu-id="ccaca-102">switch (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ccaca-102">switch (C# Reference)</span></span>
<span data-ttu-id="ccaca-103">`switch` ステートメントは選択ステートメントです。このステートメントは、実行する 1 つの "*switch セクション*" を候補のリストから "*match 式*" によるパターン マッチに基づいて選択します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 <span data-ttu-id="ccaca-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span></span>  

<span data-ttu-id="ccaca-105">`switch` ステートメントは、1 つの式が 3 つ以上の条件に対してテストされる場合に、[if-else](if-else.md) コンストラクトの代わりとしてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-105">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="ccaca-106">たとえば、次の `switch` ステートメントは、`Color` 型の変数に 3 つの値のいずれかが含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-106">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

<span data-ttu-id="ccaca-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span></span> 

<span data-ttu-id="ccaca-108">これは、`if`-`else` コンストラクトを使用する次の例に相当します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-108">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

<span data-ttu-id="ccaca-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span></span> 

## <a name="the-match-expression"></a><span data-ttu-id="ccaca-110">match 式</span><span class="sxs-lookup"><span data-stu-id="ccaca-110">The match expression</span></span>

<span data-ttu-id="ccaca-111">match 式は、`case` ラベルのパターンと照合する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="ccaca-112">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="ccaca-113">C# 6 では、match 式は、次の型の値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-113">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="ccaca-114">[char](char.md)。</span><span class="sxs-lookup"><span data-stu-id="ccaca-114">a [char](char.md).</span></span>
- <span data-ttu-id="ccaca-115">[string](string.md)。</span><span class="sxs-lookup"><span data-stu-id="ccaca-115">a [string](string.md).</span></span>
- <span data-ttu-id="ccaca-116">[bool](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="ccaca-116">a [bool](bool.md).</span></span> 
- <span data-ttu-id="ccaca-117">整数値。[int](int.md)、[long](long.md) など。</span><span class="sxs-lookup"><span data-stu-id="ccaca-117">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="ccaca-118">[enum](enum.md)値。</span><span class="sxs-lookup"><span data-stu-id="ccaca-118">an [enum](enum.md) value.</span></span>

<span data-ttu-id="ccaca-119">C# 7 以降は、match 式は NULL 以外の式にできます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-119">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="ccaca-120">switch セクション</span><span class="sxs-lookup"><span data-stu-id="ccaca-120">The switch section</span></span>
 
 <span data-ttu-id="ccaca-121">`switch` ステートメントには、1 つ以上の switch セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="ccaca-122">各 switch セクションには、1 つ以上の "*case ラベル*" と、その後に続く 1 つ以上のステートメントのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-122">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="ccaca-123">次の例に、3 つの switch セクションを持つ簡単な `switch` ステートメントを示します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-123">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="ccaca-124">各 switch セクションには、`case 1:` のような case ラベルと、2 つのステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-124">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="ccaca-125">`switch` ステートメントには、任意の数の switch セクションを含めることができます。また、次の例に示すように、各セクションに 1 つ以上の case ラベルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="ccaca-126">ただし、複数の case ラベルで同じ式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-126">However, no two case labels may contain the same expression.</span></span>  

 <span data-ttu-id="ccaca-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span></span>  

 <span data-ttu-id="ccaca-128">1 つの switch ステートメントでは、1 つの switch セクションのみが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="ccaca-129">C# では 1 つの switch セクションから次のセクションへ実行が連続することが許可されません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-129">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="ccaca-130">このため、次のコードでは、コンパイラ エラー CS0163 "コントロールはひとつの case ラベル (<case label>) から別のラベルへ流れ落ちることはできません" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>   

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
<span data-ttu-id="ccaca-131">この要件は、通常、[break](break.md) ステートメント、[goto](goto.md) ステートメント、または [return](return.md) ステートメントを使用して、switch セクションを明示的に終了することによって満たされます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="ccaca-132">ただし、次のコードも有効です。このコードでは、プログラムの制御が `default` switch セクションにフォール スルー (流れ落ちる、case ラベルを超えてコードを実行することが) できないためです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-132">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 <span data-ttu-id="ccaca-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span></span>    
  
 <span data-ttu-id="ccaca-134">match 式に一致する case ラベルが含まれた switch セクションにおけるステートメント リストの実行は、ステートメント リストに沿って最初のステートメントから順に開始され、通常は、`break`、`goto case`、`goto label`、`return`、または`throw` などのジャンプ ステートメントに達するまで続きます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-134">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="ccaca-135">この時点で、制御は `switch` ステートメントの外側、または他の case ラベルに移動します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-135">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="ccaca-136">`goto` ステートメントを使用する場合は、制御を constant ラベルに転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-136">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="ccaca-137">この制約が必要になるのは、非 constant ラベルに制御を転送しようとすると望ましくない副作用 (コード内の意図しない場所に制御を転送してしまったり、無限ループを作成してしまったりなど) が生じる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-137">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="ccaca-138">case ラベル</span><span class="sxs-lookup"><span data-stu-id="ccaca-138">Case labels</span></span>

 <span data-ttu-id="ccaca-139">各 case ラベルで、match 式と比較するためのパターンを指定します (前の例では `caseSwitch` 変数)。</span><span class="sxs-lookup"><span data-stu-id="ccaca-139">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="ccaca-140">一致すると、**最初の**一致 case を含む switch セクションに制御が移ります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-140">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="ccaca-141">match 式と一致する case ラベル パターンがない場合は、`default` case ラベルがあれば、制御はそのラベルを含むセクションに移ります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-141">If no case label pattern matches the match expression, control is transfered to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="ccaca-142">`default` case がない場合は、どの switch セクションのステートメントも実行されず、制御は `switch` ステートメント外に移ります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-142">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="ccaca-143">`switch` ステートメントとパターン マッチングの詳細については、「[`switch` ステートメントによるパターン マッチング](#pattern)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccaca-143">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="ccaca-144">C# 6 でサポートされるのは定数パターンのみで、定数値の繰り返しは許可されません。このため、case ラベルでは相互に排他的な値が定義され、match 式と一致するのは 1 つのパターンだけです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-144">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="ccaca-145">そのため、`case` ステートメントが表示される順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-145">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="ccaca-146">一方、C# 7 では他のパターンがサポートされているため、case ラベルで定義する値が相互に排他的である必要はなく、match 式と一致するパターンが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-146">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="ccaca-147">最初に一致するパターンが含まれた switch セクションのステートメントのみが実行されるので、ここでは、`case` ステートメントが表示される順序が重要になってきます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-147">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="ccaca-148">C# によって switch セクションが検出され、その switch セクションの case ステートメントが前のステートメントと同じだったり、そのステートメントのサブセットだったりすると、コンパイラ エラー CS8120 "switch case は既に以前のケースで処理されています" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-148">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="ccaca-149">次の例は、相互に排他的でない各種パターンを使用する `switch` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-149">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="ccaca-150">`case 0:` switch セクションを移動し、そのセクションが `switch` ステートメントの最初のセクションでなくなると、C# によってコンパイラ エラーが生成されます。値がゼロの整数は、整数すべてのサブセットであるためです。これは、`case int val` ステートメントで定義されているパターンです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-150">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 <span data-ttu-id="ccaca-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span></span>    

<span data-ttu-id="ccaca-152">この問題を修正し、コンパイラの警告が表示されないようにするには、次の 2 つのいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-152">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="ccaca-153">switch セクションの順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="ccaca-153">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="ccaca-154">`case` ラベルで </a name="when">when 句</a> を使用する。</span><span class="sxs-lookup"><span data-stu-id="ccaca-154">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="ccaca-155">`default` case</span><span class="sxs-lookup"><span data-stu-id="ccaca-155">The `default` case</span></span>

<span data-ttu-id="ccaca-156">`default` case では、match 式がどの `case` ラベルとも一致しない場合に実行する switch セクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-156">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="ccaca-157">`default` case を指定しない場合、match 式がどの `case` ラベルとも一致しないと、プログラム フローが `switch` ステートメントにフォール スルーします。</span><span class="sxs-lookup"><span data-stu-id="ccaca-157">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="ccaca-158">`default` case は、`switch` ステートメントで任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-158">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="ccaca-159">この case は、ソース コード内での順序に関係なく、すべての `case` ラベルが評価された後、最後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-159">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="ccaca-160">`switch` ステートメントによる <a name="pattern" /> パターン マッチング</span><span class="sxs-lookup"><span data-stu-id="ccaca-160"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="ccaca-161">各 `case` ステートメントで定義されたパターンが match 式と一致した場合に、switch セクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-161">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="ccaca-162">定数パターンは、すべてのバージョンの C# でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-162">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="ccaca-163">それ以外のパターンは、C# 7 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-163">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="ccaca-164">定数パターン</span><span class="sxs-lookup"><span data-stu-id="ccaca-164">Constant pattern</span></span> 

<span data-ttu-id="ccaca-165">定数パターンでは、match 式が、指定された定数と等しいかどうかがテストされます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-165">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="ccaca-166">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-166">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="ccaca-167">ここで *constant* はテスト対象の値です。</span><span class="sxs-lookup"><span data-stu-id="ccaca-167">where *constant* is the value to test for.</span></span> <span data-ttu-id="ccaca-168">*constant* には、次のいずれかの定数式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-168">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="ccaca-169">[bool](bool.md) リテラル。`true` または `false`。</span><span class="sxs-lookup"><span data-stu-id="ccaca-169">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="ccaca-170">任意の整数定数。[int](int.md)、[long](long.md)、[byte](byte.md) など。</span><span class="sxs-lookup"><span data-stu-id="ccaca-170">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="ccaca-171">宣言された `const` 変数の名前。</span><span class="sxs-lookup"><span data-stu-id="ccaca-171">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="ccaca-172">列挙定数。</span><span class="sxs-lookup"><span data-stu-id="ccaca-172">An enumeration constant.</span></span>
- <span data-ttu-id="ccaca-173">[char](char.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="ccaca-173">A [char](char.md) literal.</span></span>
- <span data-ttu-id="ccaca-174">[string](string.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="ccaca-174">A [string](string.md) literal.</span></span>

<span data-ttu-id="ccaca-175">定数式は以下のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-175">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="ccaca-176">*expr* と *constant* が整数型の場合、式から `true` が返されるかどうか (つまり、`expr == constant` であるかどうか) が C# の等値演算子によって判定されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-176">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="ccaca-177">それ以外の場合、式の値は静的 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) メソッドの呼び出しによって判定されます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-177">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="ccaca-178">次の例では、定数パターンを使用して、特定の日付が、週末か、週の開始日または最終日か、週の途中かを判断します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-178">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="ccaca-179">つまり、現在の日付の [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) プロパティを、@System.DayOfWeek 列挙のメンバーと照合します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-179">It evaluates the [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) property of the current day against the members of the @System.DayOfWeek enumeration.</span></span> 

<span data-ttu-id="ccaca-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span></span>

<span data-ttu-id="ccaca-181">次の例では、定数パターンを使用して、自動コーヒー メーカーをシミュレートするコンソール アプリケーションのユーザー入力を処理します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-181">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 <span data-ttu-id="ccaca-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span></span>  

### <a name="type-pattern"></a><span data-ttu-id="ccaca-183">型パターン</span><span class="sxs-lookup"><span data-stu-id="ccaca-183">Type pattern</span></span>

<span data-ttu-id="ccaca-184">型パターンを使用すると、型の評価と変換を簡潔に記述できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-184">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="ccaca-185">`switch` ステートメントと共に使用してパターン マッチングを実行すると、指定された型に式を変換できるかどうかがテストされ、変換できる場合は、その型の変数にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-185">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="ccaca-186">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-186">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="ccaca-187">ここで *type* は、*expr* の結果が変換される型の名前、*varname* は、一致した場合に *expr* の結果が変換されるオブジェクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-187">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="ccaca-188">以下のいずれかの条件が true である場合に `case` 式は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-188">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="ccaca-189">*expr* が *type* と同じ型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="ccaca-189">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="ccaca-190">*expr* が *type* から派生した型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="ccaca-190">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="ccaca-191">つまり、*expr* の結果を *type* のインスタンスにアップキャストできる。</span><span class="sxs-lookup"><span data-stu-id="ccaca-191">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="ccaca-192">*expr* のコンパイル時の型が *type* の基底クラスであり、*expr* の実行時の型が *type* または *type* から派生した型である。</span><span class="sxs-lookup"><span data-stu-id="ccaca-192">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="ccaca-193">変数の "*コンパイル時の型*" とは、その変数の型宣言で定義されている型です。</span><span class="sxs-lookup"><span data-stu-id="ccaca-193">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="ccaca-194">変数の "*実行時の型*" とは、その変数に代入されているインスタンスの型です。</span><span class="sxs-lookup"><span data-stu-id="ccaca-194">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="ccaca-195">*expr* が、*type* インターフェイスを実装する型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="ccaca-195">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="ccaca-196">case 式が true の場合は、*varname* が確実に割り当てられ、switch セクションにのみローカル スコープが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-196">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="ccaca-197">`null` は型とは一致しません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-197">Note that `null` does not match a type.</span></span> <span data-ttu-id="ccaca-198">`null` を一致させるには、次の `case` ラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-198">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="ccaca-199">次の例では、型パターンを使用して、さまざまな種類のコレクション型に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ccaca-199">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

<span data-ttu-id="ccaca-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span></span>

<span data-ttu-id="ccaca-201">パターン マッチングを使用しない場合、このコードは次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-201">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="ccaca-202">型パターン マッチングを使用することにより、変換結果が `null` であるかどうかをテストしたり、キャストを繰り返したりする必要がなくなるため、コードがよりコンパクトで読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="ccaca-202">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

<span data-ttu-id="ccaca-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span></span>

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="ccaca-204">`case` ステートメントおよび `when` 句</span><span class="sxs-lookup"><span data-stu-id="ccaca-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="ccaca-205">C# 7 以降では、case ステートメントは相互に排他的である必要がないため、`when` 句を追加して、case ステートメントを true に評価するために満たされなければならない条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-205">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="ccaca-206">`when` 句には、ブール値を返す任意の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ccaca-206">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="ccaca-207">`when` 句を使用すると、match 式の値が `null` のときに、switch セクションが実行されないようにできます。これは、この句の一般的な使用方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="ccaca-207">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="ccaca-208">次の例では、`Shape` 基底クラス、`Shape` から派生する `Rectangle` クラス、および `Rectangle` から派生する `Square` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="ccaca-209">ここでは `when` 句を使用して、同じ長さと幅が割り当てられている `Rectangle` オブジェクトが、`Square` オブジェクトとしてインスタンス化されていなくても、`ShowShapeInfo` によって確実に `Square` として処理されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="ccaca-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="ccaca-210">このメソッドは、`null` オブジェクトの情報や、面積がゼロの図形の情報を表示しようとしません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-210">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

<span data-ttu-id="ccaca-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ccaca-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span></span>
  
<span data-ttu-id="ccaca-212">この例で、`Shape`オブジェクトが `null` かどうかをテストしようとする `when` 句は実行されません。</span><span class="sxs-lookup"><span data-stu-id="ccaca-212">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="ccaca-213">`null` をテストするための正しい型パターンは `case null:` です。</span><span class="sxs-lookup"><span data-stu-id="ccaca-213">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ccaca-214">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ccaca-214">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccaca-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccaca-215">See Also</span></span>  

 <span data-ttu-id="ccaca-216">[C# リファレンス](../index.md) </span><span class="sxs-lookup"><span data-stu-id="ccaca-216">[C# Reference](../index.md) </span></span>  
 <span data-ttu-id="ccaca-217">[C# プログラミング ガイド](../../programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ccaca-217">[C# Programming Guide](../../programming-guide/index.md) </span></span>  
 <span data-ttu-id="ccaca-218">[C# のキーワード](index.md) </span><span class="sxs-lookup"><span data-stu-id="ccaca-218">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="ccaca-219">[if-else](if-else.md) </span><span class="sxs-lookup"><span data-stu-id="ccaca-219">[if-else](if-else.md) </span></span>  
 [<span data-ttu-id="ccaca-220">パターン一致</span><span class="sxs-lookup"><span data-stu-id="ccaca-220">Pattern Matching</span></span>](../../pattern-matching.md)   
 

 

