---
title: "for (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="5d29c-102">for (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5d29c-102">for (C# Reference)</span></span>
<span data-ttu-id="5d29c-103">`for` ループを使うと、指定した式が `false` と評価されるまで、ステートメントまたはステートメント ブロックを繰り返し実行することができます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="5d29c-104">この種類のループは、配列の反復処理などループの反復回数が事前にわかっている用途に使用します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d29c-105">例</span><span class="sxs-lookup"><span data-stu-id="5d29c-105">Example</span></span>  
 <span data-ttu-id="5d29c-106">次の例では、`i` の値をコンソールに出力し、ループの反復ごとにその値を 1 ずつインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="5d29c-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="5d29c-107">前の例で `for` ステートメントによって実行されている処理は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5d29c-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="5d29c-108">まず、変数 `i` の初期値が確立されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="5d29c-109">ループの反復回数に関係なく、このステップが実行されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="5d29c-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="5d29c-110">この初期化は、ループ処理プロセスの外で実行されると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="5d29c-111">条件 (`i <= 5`) を評価するために、`i` の値が 5 と比較されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="5d29c-112">`i` が 5 以下である場合、条件が `true` に評価され、次の処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="5d29c-113">ループ本体にある `Console.WriteLine` ステートメントによって `i` の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="5d29c-114">`i` の値が 1 ずつインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="5d29c-115">ループがステップ 2 の最初に戻り、再度条件が評価されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="5d29c-116">`i` が 5 より大きい場合、条件が `false` に評価され、ループが終了します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="5d29c-117">`i` の初期値が 5 より大きい場合、ループの本体は一度も実行されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5d29c-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="5d29c-118">すべての `for` ステートメントには、初期化子、条件、反復子のセクションが定義されています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="5d29c-119">通常、ループの反復回数は、これらのセクションによって決まります。</span><span class="sxs-lookup"><span data-stu-id="5d29c-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="5d29c-120">各セクションには次の目的があります。</span><span class="sxs-lookup"><span data-stu-id="5d29c-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="5d29c-121">初期化子セクションによって初期条件が設定されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="5d29c-122">ループに入る前に、このセクションのステートメントが 1 回だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="5d29c-123">このセクションには、次の 2 つの項目のうち、いずれか一方のみを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="5d29c-124">ローカル ループ変数の宣言と初期化。冒頭の例 (`int i = 1`) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d29c-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="5d29c-125">この変数はループに対してローカルであり、ループ外からアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5d29c-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="5d29c-126">次に列挙した 0 個以上のステートメント式 (コンマ区切り)。</span><span class="sxs-lookup"><span data-stu-id="5d29c-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="5d29c-127">[代入](../../../csharp/language-reference/operators/assignment-operator.md)ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d29c-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="5d29c-128">メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="5d29c-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="5d29c-129">前置または後置の[インクリメント](../../../csharp/language-reference/operators/increment-operator.md)式 (`++i`、`i++` など)</span><span class="sxs-lookup"><span data-stu-id="5d29c-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="5d29c-130">前置または後置の[デクリメント](../../../csharp/language-reference/operators/decrement-operator.md)式 (`--i`、`i--` など)</span><span class="sxs-lookup"><span data-stu-id="5d29c-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="5d29c-131">[new](../../../csharp/language-reference/keywords/new-operator.md) を使用したオブジェクト作成</span><span class="sxs-lookup"><span data-stu-id="5d29c-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="5d29c-132">[await](../../../csharp/language-reference/keywords/await.md) 式</span><span class="sxs-lookup"><span data-stu-id="5d29c-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="5d29c-133">条件セクションには、ループを終了するか再度実行するかを判断する際に評価されるブール式を記述します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="5d29c-134">ループ本体の反復処理が終わるたびに実行される処理を反復子セクションで定義します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="5d29c-135">反復子セクションには、次のステートメント式を 0 個以上、コンマで区切って記述します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="5d29c-136">[代入](../../../csharp/language-reference/operators/assignment-operator.md)ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d29c-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="5d29c-137">メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="5d29c-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="5d29c-138">前置または後置の[インクリメント](../../../csharp/language-reference/operators/increment-operator.md)式 (`++i`、`i++` など)</span><span class="sxs-lookup"><span data-stu-id="5d29c-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="5d29c-139">前置または後置の[デクリメント](../../../csharp/language-reference/operators/decrement-operator.md)式 (`--i`、`i--` など)</span><span class="sxs-lookup"><span data-stu-id="5d29c-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="5d29c-140">[new](../../../csharp/language-reference/keywords/new-operator.md) を使用したオブジェクト作成</span><span class="sxs-lookup"><span data-stu-id="5d29c-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="5d29c-141">[await](../../../csharp/language-reference/keywords/await.md) 式</span><span class="sxs-lookup"><span data-stu-id="5d29c-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="5d29c-142">ループの本体は、単一のステートメント、空のステートメント、またはステートメント ブロックで構成され、0 個以上のステートメントを中かっこで囲んで記述します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="5d29c-143">[break](../../../csharp/language-reference/keywords/break.md) キーワードを使って `for` ループを抜けたり、[continue](../../../csharp/language-reference/keywords/continue.md) キーワードを使って次の反復処理にステップ実行したりできます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="5d29c-144">また、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、[throw](../../../csharp/language-reference/keywords/throw.md) のいずれかのステートメントを使ってループを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d29c-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="5d29c-145">このトピックの冒頭の例は、きわめて標準的な `for` ループで、各セクションには次の内容が記述されています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="5d29c-146">初期化子では、ループの反復回数を保持するローカル ループ変数 `i` を宣言して初期化しています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="5d29c-147">条件では、既知の最終値 (5) と照らし合わせてループ変数の値をチェックしています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="5d29c-148">反復子セクションでは、後置インクリメント ステートメント (`i++`) を使って、ループの反復回数をカウントしています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="5d29c-149">次のコードはやや特殊な例です。初期化子セクションで外部ループ変数に値を代入し、初期化子セクションと反復子セクションの両方で `Console.WriteLine` メソッドを呼び出しています。さらに、反復子セクションで 2 つの変数の値を変更しています。</span><span class="sxs-lookup"><span data-stu-id="5d29c-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="5d29c-150">`for` ステートメントを定義する式はすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="5d29c-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="5d29c-151">たとえば次のステートメントは無限ループを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d29c-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d29c-152">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="5d29c-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d29c-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d29c-153">See Also</span></span>  
 [<span data-ttu-id="5d29c-154">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="5d29c-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5d29c-155">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5d29c-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d29c-156">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="5d29c-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5d29c-157">foreach、in</span><span class="sxs-lookup"><span data-stu-id="5d29c-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="5d29c-158">for ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="5d29c-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="5d29c-159">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="5d29c-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
