---
title: C# のステートメント - C# 言語のツアー
description: ステートメントを使用して C# プログラムの処理を作成します
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351980"
---
# <a name="statements"></a><span data-ttu-id="42849-103">ステートメント</span><span class="sxs-lookup"><span data-stu-id="42849-103">Statements</span></span>

<span data-ttu-id="42849-104">プログラムの処理は、"*ステートメント*" を使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="42849-104">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="42849-105">C# はさまざまな種類のステートメントをサポートしており、その多くは埋め込みステートメントとして定義されています。</span><span class="sxs-lookup"><span data-stu-id="42849-105">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="42849-106">"*ブロック*" を使用すると、1 つのステートメントしか使用できないコンテキストで複数のステートメントを記述できます。</span><span class="sxs-lookup"><span data-stu-id="42849-106">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="42849-107">ブロックは、区切り記号 `{` と `}` の間に記述されたステートメントのリストから成ります。</span><span class="sxs-lookup"><span data-stu-id="42849-107">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="42849-108">"*宣言ステートメント*" は、ローカル変数および定数の宣言に使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-108">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="42849-109">"*式ステートメント*" は、式の評価に使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-109">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="42849-110">ステートメントとして使用できる式には、メソッドの呼び出し、`new` 演算子を使用したオブジェクトの割り当て、`=` 演算子と複合代入演算子を使用した代入、`++` 演算子と `--` 演算子を使用したインクリメント演算とデクリメント演算、および `await` 式があります。</span><span class="sxs-lookup"><span data-stu-id="42849-110">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="42849-111">"*選択ステートメント*" は、式の値に基づいて、実行できる多数のステートメントから 1 つを選択するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-111">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="42849-112">このグループには `if` および `switch` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42849-112">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="42849-113">"*繰り返しステートメント*" は、埋め込みステートメントを繰り返し実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-113">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="42849-114">このグループには、`while`、`do`、`for`、および `foreach` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42849-114">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="42849-115">"*ジャンプ ステートメント*" は、制御を移すために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-115">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="42849-116">このグループには、`break`、`continue`、`goto`、`throw`、`return`、および `yield` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42849-116">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="42849-117">`try`...`catch` ステートメントはブロックの実行中に発生した例外をキャッチするために使用し、`try`...`finally` ステートメントは例外が発生したかどうかにかかわらず常に実行される終了処理コードを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-117">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="42849-118">`checked` および `unchecked` ステートメントは、整数型の算術演算および変換に対するオーバーフロー チェック コンテキストを制御するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-118">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="42849-119">`lock` ステートメントは、指定のオブジェクトに対する相互排他ロックを取得し、ステートメントを実行してからロックを解放するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-119">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="42849-120">`using` ステートメントは、リソースを取得し、ステートメントを実行してからそのリソースを破棄するために使用します。</span><span class="sxs-lookup"><span data-stu-id="42849-120">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="42849-121">以下に、使用できるさまざまなステートメントの一覧とそれぞれの例を示します。</span><span class="sxs-lookup"><span data-stu-id="42849-121">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="42849-122">ローカル変数の宣言:</span><span class="sxs-lookup"><span data-stu-id="42849-122">Local variable declaration:</span></span>

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]

* <span data-ttu-id="42849-123">ローカル定数の宣言:</span><span class="sxs-lookup"><span data-stu-id="42849-123">Local constant declaration:</span></span>

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]

* <span data-ttu-id="42849-124">式ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-124">Expression statement:</span></span>

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]

* <span data-ttu-id="42849-125">`if` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-125">`if` statement:</span></span>

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]

* <span data-ttu-id="42849-126">`switch` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-126">`switch` statement:</span></span>

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]

* <span data-ttu-id="42849-127">`while` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-127">`while` statement:</span></span>

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]

* <span data-ttu-id="42849-128">`do` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-128">`do` statement:</span></span>

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]

* <span data-ttu-id="42849-129">`for` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-129">`for` statement:</span></span>

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]

* <span data-ttu-id="42849-130">`foreach` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-130">`foreach` statement:</span></span>

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]

* <span data-ttu-id="42849-131">`break` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-131">`break` statement:</span></span>

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]

* <span data-ttu-id="42849-132">`continue` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-132">`continue` statement:</span></span>

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]

* <span data-ttu-id="42849-133">`goto` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-133">`goto` statement:</span></span>

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]

* <span data-ttu-id="42849-134">`return` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-134">`return` statement:</span></span>

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]

* <span data-ttu-id="42849-135">`yield` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-135">`yield` statement:</span></span>

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]

* <span data-ttu-id="42849-136">`throw` ステートメントと `try` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-136">`throw` statements and `try` statements:</span></span>

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]

* <span data-ttu-id="42849-137">`checked` ステートメントと `unchecked` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-137">`checked` and `unchecked` statements:</span></span>

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]

* <span data-ttu-id="42849-138">`lock` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-138">`lock` statement:</span></span>

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]

* <span data-ttu-id="42849-139">`using` ステートメント:</span><span class="sxs-lookup"><span data-stu-id="42849-139">`using` statement:</span></span>

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]

>[!div class="step-by-step"]
<span data-ttu-id="42849-140">[前へ](expressions.md)
[次へ](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="42849-140">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>
