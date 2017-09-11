---
title: "C# のステートメント - C# 言語のツアー"
description: "ステートメントを使用して C# プログラムの処理を作成します"
keywords: ".NET, シーシャープ, ステートメント, 構文"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="statements"></a><span data-ttu-id="04449-104">ステートメント</span><span class="sxs-lookup"><span data-stu-id="04449-104">Statements</span></span>

<span data-ttu-id="04449-105">プログラムの処理は、"*ステートメント*" を使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="04449-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="04449-106">C# はさまざまな種類のステートメントをサポートしており、その多くは埋め込みステートメントとして定義されています。</span><span class="sxs-lookup"><span data-stu-id="04449-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="04449-107">"*ブロック*" を使用すると、1 つのステートメントしか使用できないコンテキストで複数のステートメントを記述できます。</span><span class="sxs-lookup"><span data-stu-id="04449-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="04449-108">ブロックは、区切り記号 `{` と `}` の間に記述されたステートメントのリストから成ります。</span><span class="sxs-lookup"><span data-stu-id="04449-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="04449-109">"*宣言ステートメント*" は、ローカル変数および定数の宣言に使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="04449-110">"*式ステートメント*" は、式の評価に使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="04449-111">ステートメントとして使用できる式には、メソッドの呼び出し、`new` 演算子を使用したオブジェクトの割り当て、`=` 演算子と複合代入演算子を使用した代入、`++` 演算子と `--` 演算子を使用したインクリメント演算とデクリメント演算、および `await` 式があります。</span><span class="sxs-lookup"><span data-stu-id="04449-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="04449-112">"*選択ステートメント*" は、式の値に基づいて、実行できる多数のステートメントから 1 つを選択するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="04449-113">このグループには `if` および `switch` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04449-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="04449-114">"*繰り返しステートメント*" は、埋め込みステートメントを繰り返し実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="04449-115">このグループには、`while`、`do`、`for`、および `foreach` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04449-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="04449-116">"*ジャンプ ステートメント*" は、制御を移すために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="04449-117">このグループには、`break`、`continue`、`goto`、`throw`、`return`、および `yield` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="04449-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="04449-118">`try`...`catch` ステートメントはブロックの実行中に発生した例外をキャッチするために使用し、`try`...`finally` ステートメントは例外が発生したかどうかにかかわらず常に実行される終了処理コードを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="04449-119">`checked` および `unchecked` ステートメントは、整数型の算術演算および変換に対するオーバーフロー チェック コンテキストを制御するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="04449-120">`lock` ステートメントは、指定のオブジェクトに対する相互排他ロックを取得し、ステートメントを実行してからロックを解放するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="04449-121">`using` ステートメントは、リソースを取得し、ステートメントを実行してからそのリソースを破棄するために使用します。</span><span class="sxs-lookup"><span data-stu-id="04449-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="04449-122">以下に、使用できるさまざまなステートメントの一覧とそれぞれの例を示します。</span><span class="sxs-lookup"><span data-stu-id="04449-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="04449-123">ローカル変数の宣言:</span><span class="sxs-lookup"><span data-stu-id="04449-123">Local variable declaration:</span></span>

 <span data-ttu-id="04449-124">[!code-csharp[宣言](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span><span class="sxs-lookup"><span data-stu-id="04449-124">[!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span></span>

* <span data-ttu-id="04449-125">ローカル定数の宣言:</span><span class="sxs-lookup"><span data-stu-id="04449-125">Local constant declaration:</span></span>

 <span data-ttu-id="04449-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span><span class="sxs-lookup"><span data-stu-id="04449-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span></span>

* <span data-ttu-id="04449-127">式ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-127">Expression statement:</span></span>

 <span data-ttu-id="04449-128">[!code-csharp[式](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span><span class="sxs-lookup"><span data-stu-id="04449-128">[!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span></span>

* <span data-ttu-id="04449-129">`if` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-129">`if` statement:</span></span>

 <span data-ttu-id="04449-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span><span class="sxs-lookup"><span data-stu-id="04449-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span></span>

* <span data-ttu-id="04449-131">`switch` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-131">`switch` statement:</span></span>

 <span data-ttu-id="04449-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span><span class="sxs-lookup"><span data-stu-id="04449-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span></span>

* <span data-ttu-id="04449-133">`while` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-133">`while` statement:</span></span>

 <span data-ttu-id="04449-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span><span class="sxs-lookup"><span data-stu-id="04449-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span></span>

* <span data-ttu-id="04449-135">`do` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-135">`do` statement:</span></span>

 <span data-ttu-id="04449-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span><span class="sxs-lookup"><span data-stu-id="04449-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span></span>

* <span data-ttu-id="04449-137">`for` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-137">`for` statement:</span></span>

 <span data-ttu-id="04449-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span><span class="sxs-lookup"><span data-stu-id="04449-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span></span>

* <span data-ttu-id="04449-139">`foreach` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-139">`foreach` statement:</span></span>

 <span data-ttu-id="04449-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span><span class="sxs-lookup"><span data-stu-id="04449-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span></span>

* <span data-ttu-id="04449-141">`break` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-141">`break` statement:</span></span>

 <span data-ttu-id="04449-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span><span class="sxs-lookup"><span data-stu-id="04449-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span></span>

* <span data-ttu-id="04449-143">`continue` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-143">`continue` statement:</span></span>

 <span data-ttu-id="04449-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span><span class="sxs-lookup"><span data-stu-id="04449-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span></span>

* <span data-ttu-id="04449-145">`goto` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-145">`goto` statement:</span></span>

 <span data-ttu-id="04449-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span><span class="sxs-lookup"><span data-stu-id="04449-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span></span>

* <span data-ttu-id="04449-147">`return` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-147">`return` statement:</span></span>

 <span data-ttu-id="04449-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span><span class="sxs-lookup"><span data-stu-id="04449-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span></span>

* <span data-ttu-id="04449-149">`yield` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-149">`yield` statement:</span></span>

 <span data-ttu-id="04449-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span><span class="sxs-lookup"><span data-stu-id="04449-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span></span>

* <span data-ttu-id="04449-151">`throw` ステートメントと `try` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-151">`throw` statements and `try` statements:</span></span>

 <span data-ttu-id="04449-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span><span class="sxs-lookup"><span data-stu-id="04449-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span></span>

* <span data-ttu-id="04449-153">`checked` ステートメントと `unchecked` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-153">`checked` and `unchecked` statements:</span></span>

 <span data-ttu-id="04449-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span><span class="sxs-lookup"><span data-stu-id="04449-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span></span>

* <span data-ttu-id="04449-155">`lock` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-155">`lock` statement:</span></span>

 <span data-ttu-id="04449-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span><span class="sxs-lookup"><span data-stu-id="04449-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span></span>

* <span data-ttu-id="04449-157">`using` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="04449-157">`using` statement:</span></span>

 <span data-ttu-id="04449-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span><span class="sxs-lookup"><span data-stu-id="04449-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="04449-159">[前へ](expressions.md)
[次へ](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="04449-159">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>

