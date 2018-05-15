---
title: コード コントラクト
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09bfa08589bda68258883e6f080392f534e8c5df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="code-contracts"></a><span data-ttu-id="6ae09-102">コード コントラクト</span><span class="sxs-lookup"><span data-stu-id="6ae09-102">Code Contracts</span></span>
<span data-ttu-id="6ae09-103">コード コントラクトを使用すると、事前条件、事後条件、およびオブジェクト不変条件をコードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-103">Code contracts provide a way to specify preconditions, postconditions, and object invariants in your code.</span></span> <span data-ttu-id="6ae09-104">事前条件とは、メソッドやプロパティに入るときに満たされている必要がある要件です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-104">Preconditions are requirements that must be met when entering a method or property.</span></span> <span data-ttu-id="6ae09-105">事後条件は、メソッドやプロパティのコードが終了するときの予測を表します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-105">Postconditions describe expectations at the time the method or property code exits.</span></span> <span data-ttu-id="6ae09-106">オブジェクト不変条件は、正しい状態のクラスに対して予期される状態を表します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-106">Object invariants describe the expected state for a class that is in a good state.</span></span>  
  
 <span data-ttu-id="6ae09-107">コード コントラクトには、コードをマーク付けするためのクラス、コンパイル時の分析のための静的アナライザー、およびランタイム アナライザーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-107">Code contracts include classes for marking your code, a static analyzer for compile-time analysis, and a runtime analyzer.</span></span> <span data-ttu-id="6ae09-108">コード コントラクトのクラスは <xref:System.Diagnostics.Contracts> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-108">The classes for code contracts can be found in the <xref:System.Diagnostics.Contracts> namespace.</span></span>  
  
 <span data-ttu-id="6ae09-109">コード コントラクトには次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-109">The benefits of code contracts include the following:</span></span>  
  
-   <span data-ttu-id="6ae09-110">テストの強化: コード コントラクトでは、コントラクトの静的検証、ランタイム チェック、およびドキュメントの生成がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-110">Improved testing: Code contracts provide static contract verification, runtime checking, and documentation generation.</span></span>  
  
-   <span data-ttu-id="6ae09-111">自動テスト ツール: コード コントラクトを使用すると、事前条件を満たさない無意味なテスト引数をフィルターで除外して、より意味のある単体テストを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-111">Automatic testing tools: You can use code contracts to generate more meaningful unit tests by filtering out meaningless test arguments that do not satisfy preconditions.</span></span>  
  
-   <span data-ttu-id="6ae09-112">静的検証: 静的チェックにより、コントラクト違反がないかどうかをプログラムを実行せずに確認できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-112">Static verification: The static checker can decide whether there are any contract violations without running the program.</span></span> <span data-ttu-id="6ae09-113">暗黙的なコントラクト (null の逆参照、配列の範囲など) と明示的なコントラクトがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-113">It checks for implicit contracts, such as null dereferences and array bounds, and explicit contracts.</span></span>  
  
-   <span data-ttu-id="6ae09-114">リファレンス ドキュメント: ドキュメント生成機能により、既存の XML ドキュメント ファイルにコントラクトの情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-114">Reference documentation: The documentation generator augments existing XML documentation files with contract information.</span></span> <span data-ttu-id="6ae09-115">生成されるドキュメントのページにコントラクトのセクションが含まれるようにするための、[Sandcastle](https://github.com/EWSoftware/SHFB) で使用できるスタイル シートも用意されています。</span><span class="sxs-lookup"><span data-stu-id="6ae09-115">There are also style sheets that can be used with [Sandcastle](https://github.com/EWSoftware/SHFB) so that the generated documentation pages have contract sections.</span></span>  
  
 <span data-ttu-id="6ae09-116">コントラクトは、すべての .NET Framework 言語ですぐに使用できます。特別なパーサーやコンパイラを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-116">All .NET Framework languages can immediately take advantage of contracts; you do not have to write a special parser or compiler.</span></span> <span data-ttu-id="6ae09-117">実行するコード コントラクト分析のレベルを指定できる Visual Studio アドインや、</span><span class="sxs-lookup"><span data-stu-id="6ae09-117">A Visual Studio add-in lets you specify the level of code contract analysis to be performed.</span></span> <span data-ttu-id="6ae09-118">コントラクトの形式が正しいかどうかを確認したり (型チェックおよび名前解決)、コンパイルされた形式 (MSIL (Microsoft Intermediate Language) 形式) のコントラクトを生成したりできるアナライザーも用意されています。</span><span class="sxs-lookup"><span data-stu-id="6ae09-118">The analyzers can confirm that the contracts are well-formed (type checking and name resolution) and can produce a compiled form of the contracts in Microsoft intermediate language (MSIL) format.</span></span> <span data-ttu-id="6ae09-119">Visual Studio でコントラクトを作成する場合は、Visual Studio の標準の IntelliSense も利用できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-119">Authoring contracts in Visual Studio lets you take advantage of the standard IntelliSense provided by the tool.</span></span>  
  
 <span data-ttu-id="6ae09-120">コントラクト クラスのほとんどのメソッドは、条件付きでコンパイルされます。したがって、それらのメソッドの呼び出しは、`#define` ディレクティブを使用して CONTRACTS_FULL という特別なシンボルを定義した場合にのみコンパイラで生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-120">Most methods in the contract class are conditionally compiled; that is, the compiler emits calls to these methods only when  you define a special symbol, CONTRACTS_FULL, by using the `#define` directive.</span></span> <span data-ttu-id="6ae09-121">CONTRACTS_FULL を使用すると、コードで `#ifdef` ディレクティブを使用せずにコントラクトを記述して、コントラクトを含むものと含まないものなど、さまざまなビルドを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-121">CONTRACTS_FULL lets you write contracts in your code without using `#ifdef` directives; you can produce different builds, some with contracts, and some without.</span></span>  
  
 <span data-ttu-id="6ae09-122">コード コントラクトを使用するためのツールおよび詳細な手順については、MSDN DevLabs Web サイトの「[Code Contracts](http://go.microsoft.com/fwlink/?LinkId=152461)」(コード コントラクト) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ae09-122">For tools and detailed instructions for using code contracts, see [Code Contracts](http://go.microsoft.com/fwlink/?LinkId=152461) on the MSDN DevLabs Web site.</span></span>  
  
## <a name="preconditions"></a><span data-ttu-id="6ae09-123">実行前の状態</span><span class="sxs-lookup"><span data-stu-id="6ae09-123">Preconditions</span></span>  
 <span data-ttu-id="6ae09-124">事前条件を指定するには、<xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-124">You can express preconditions by using the <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6ae09-125">事前条件では、メソッドが呼び出される状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-125">Preconditions specify state when a method is invoked.</span></span> <span data-ttu-id="6ae09-126">通常は、有効なパラメーター値を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-126">They are generally used to specify valid parameter values.</span></span> <span data-ttu-id="6ae09-127">事前条件で参照されるすべてのメンバーは、アクセス レベルが少なくともメソッド自体と同じである必要があります。そうでない場合、メソッドのすべての呼び出し元がその事前条件を理解できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-127">All members that are mentioned in preconditions must be at least as accessible as the method itself; otherwise, the precondition might not be understood by all callers of a method.</span></span> <span data-ttu-id="6ae09-128">また、条件に副作用がないようにする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-128">The condition must have no side-effects.</span></span> <span data-ttu-id="6ae09-129">事前条件が満たされなかった場合の実行時の動作は、ランタイム アナライザーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-129">The run-time behavior of failed preconditions is determined by the runtime analyzer.</span></span>  
  
 <span data-ttu-id="6ae09-130">たとえば、次の事前条件は、パラメーター `x` が null 以外である必要があることを表しています。</span><span class="sxs-lookup"><span data-stu-id="6ae09-130">For example, the following precondition expresses that parameter `x` must be non-null.</span></span>  
  
 `Contract.Requires( x != null );`  
  
 <span data-ttu-id="6ae09-131">事前条件が満たされなかった場合に特定の例外をスローする必要がある場合には、次のように、<xref:System.Diagnostics.Contracts.Contract.Requires%2A> のジェネリック オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-131">If your code must throw a particular exception on failure of a precondition, you can use the generic overload of <xref:System.Diagnostics.Contracts.Contract.Requires%2A> as follows.</span></span>  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a><span data-ttu-id="6ae09-132">レガシ requires ステートメント</span><span class="sxs-lookup"><span data-stu-id="6ae09-132">Legacy Requires Statements</span></span>  
 <span data-ttu-id="6ae09-133">ほとんどのコードには、`if`-`then`-`throw` コードの形式のパラメーター検証が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ae09-133">Most code contains some parameter validation in the form of `if`-`then`-`throw` code.</span></span> <span data-ttu-id="6ae09-134">以下の場合は、それらのステートメントがコントラクト ツールで事前条件として認識されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-134">The contract tools recognize these statements as preconditions in the following cases:</span></span>  
  
-   <span data-ttu-id="6ae09-135">それらのステートメントがメソッド内で他のステートメントより前にある場合。</span><span class="sxs-lookup"><span data-stu-id="6ae09-135">The statements appear before any other statements in a method.</span></span>  
  
-   <span data-ttu-id="6ae09-136">それらのステートメント全体の後に <xref:System.Diagnostics.Contracts.Contract> メソッドの明示的な呼び出し (<xref:System.Diagnostics.Contracts.Contract.Requires%2A>、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>、または <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> のいずれかのメソッドの呼び出しなど) がある場合。</span><span class="sxs-lookup"><span data-stu-id="6ae09-136">The entire set of such statements is followed by an explicit <xref:System.Diagnostics.Contracts.Contract> method call, such as a call to the <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, or <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> method.</span></span>  
  
 <span data-ttu-id="6ae09-137">`if`-`then`-`throw` ステートメントがこのような形式になっている場合、それらのステートメントはレガシ `requires` ステートメントとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-137">When `if`-`then`-`throw` statements appear in this form, the tools recognize them as legacy `requires` statements.</span></span> <span data-ttu-id="6ae09-138">`if`-`then`-`throw` というシーケンスの後に他のコントラクトがない場合は、<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> メソッドでコードを終了します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-138">If no other contracts follow the `if`-`then`-`throw` sequence, end the code with the <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> method.</span></span>  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 <span data-ttu-id="6ae09-139">上のテストの条件は否定の事前条件であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6ae09-139">Note that the condition in the preceding test is a negated precondition.</span></span> <span data-ttu-id="6ae09-140">(実際の事前条件は `x != null` です)。否定の事前条件には多くの制限があり、上の例のように記述する必要があります (`else` 句が含まれていてはならない、`then` 句の本体は 1 つの `throw` ステートメントでなければならないなど)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-140">(The actual precondition would be `x != null`.) A negated precondition is highly restricted: It must be written as shown in the previous example; that is, it should contain no `else` clauses, and the body of the `then` clause must be a single `throw` statement.</span></span> <span data-ttu-id="6ae09-141">`if` テストには純粋性と可視性の両方の規則が適用されますが (「[使用方法のガイドライン](#usage_guidelines)」を参照)、`throw` 式に適用されるのは純粋性の規則だけです。</span><span class="sxs-lookup"><span data-stu-id="6ae09-141">The `if` test is subject to both purity and visibility rules (see [Usage Guidelines](#usage_guidelines)), but the `throw` expression is subject only to purity rules.</span></span> <span data-ttu-id="6ae09-142">ただし、スローされる例外の型には、そのコントラクトが存在するメソッドと同じレベルの可視性が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-142">However, the type of the exception thrown must be as visible as the method in which the contract occurs.</span></span>  
  
## <a name="postconditions"></a><span data-ttu-id="6ae09-143">実行後の状態</span><span class="sxs-lookup"><span data-stu-id="6ae09-143">Postconditions</span></span>  
 <span data-ttu-id="6ae09-144">事後条件は、メソッドの終了時の状態についてのコントラクトで、</span><span class="sxs-lookup"><span data-stu-id="6ae09-144">Postconditions are contracts for the state of a method when it terminates.</span></span> <span data-ttu-id="6ae09-145">メソッドが終了する直前にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-145">The postcondition is checked just before exiting a method.</span></span> <span data-ttu-id="6ae09-146">事後条件が満たされなかった場合の実行時の動作は、ランタイム アナライザーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-146">The run-time behavior of failed postconditions is determined by the runtime analyzer.</span></span>  
  
 <span data-ttu-id="6ae09-147">事後条件では、事前条件とは違って、可視性のレベルがメソッドより低いメンバーも参照できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-147">Unlike preconditions, postconditions may reference members with less visibility.</span></span> <span data-ttu-id="6ae09-148">事後条件でプライベートの状態を使用して指定した情報は、クライアントが理解できなかったり利用できなかったりする場合もありますが、そのためにクライアントがメソッドを正しく使用できなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-148">A client may not be able to understand or make use of some of the information expressed by a postcondition using private state, but this does not affect the client's ability to use the method correctly.</span></span>  
  
### <a name="standard-postconditions"></a><span data-ttu-id="6ae09-149">標準の事後条件</span><span class="sxs-lookup"><span data-stu-id="6ae09-149">Standard Postconditions</span></span>  
 <span data-ttu-id="6ae09-150">標準の事後条件を指定するには、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-150">You can express standard postconditions by using the <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> method.</span></span> <span data-ttu-id="6ae09-151">事後条件は、メソッドが正常に終了した場合に `true` になる必要がある条件を表します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-151">Postconditions express a condition that must be `true` upon normal termination of the method.</span></span>  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a><span data-ttu-id="6ae09-152">例外の事後条件</span><span class="sxs-lookup"><span data-stu-id="6ae09-152">Exceptional Postconditions</span></span>  
 <span data-ttu-id="6ae09-153">例外の事後条件とは、メソッドによって特定の例外がスローされた場合に `true` になる必要がある事後条件です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-153">Exceptional postconditions are postconditions that should be `true` when a particular exception is thrown by a method.</span></span> <span data-ttu-id="6ae09-154">これらの事後条件を指定するには、次の例で示されているように、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-154">You can specify these postconditions by using the <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> method, as the following example shows.</span></span>  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 <span data-ttu-id="6ae09-155">引数は、`T` のサブタイプである例外がスローされた場合に `true` になる必要がある条件です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-155">The argument is the condition that must be `true` whenever an exception that is a subtype of `T` is thrown.</span></span>  
  
 <span data-ttu-id="6ae09-156">例外型の中には、例外の事後条件で使用するのが困難なものもあります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-156">There are some exception types that are difficult to use in an exceptional postcondition.</span></span> <span data-ttu-id="6ae09-157">たとえば、`T` に対して <xref:System.Exception> 型を使用する場合は、指定する条件が、スローされる例外の型に関係なく (スタック オーバーフローなどの制御不可能な例外の場合でも) メソッドによって保証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-157">For example, using the type <xref:System.Exception> for `T` requires the method to guarantee the condition regardless of the type of exception that is thrown, even if it is a stack overflow or other impossible-to-control exception.</span></span> <span data-ttu-id="6ae09-158">例外の事後条件は、メンバーが呼び出されたときにスローされる可能性がある特定の例外に対してのみ使用するようにしてください (<xref:System.TimeZoneInfo> メソッドの呼び出しに対して <xref:System.InvalidTimeZoneException> がスローされる場合など)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-158">You should use exceptional postconditions only for specific exceptions that might be thrown when a member is called, for example, when an <xref:System.InvalidTimeZoneException> is thrown for a <xref:System.TimeZoneInfo> method call.</span></span>  
  
### <a name="special-postconditions"></a><span data-ttu-id="6ae09-159">特殊な事後条件</span><span class="sxs-lookup"><span data-stu-id="6ae09-159">Special Postconditions</span></span>  
 <span data-ttu-id="6ae09-160">次のメソッドは、事後条件の中でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-160">The following methods may be used only within postconditions:</span></span>  
  
-   <span data-ttu-id="6ae09-161">事後条件でメソッドの戻り値を参照するには、`Contract.Result<T>()` という式を使用します。`T` はメソッドの戻り値の型に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-161">You can refer to method return values in postconditions by using the expression `Contract.Result<T>()`, where `T` is replaced by the return type of the method.</span></span> <span data-ttu-id="6ae09-162">コンパイラが型を推論できない場合は明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-162">When the compiler is unable to infer the type, you must explicitly provide it.</span></span> <span data-ttu-id="6ae09-163">たとえば、C# コンパイラでは、引数を受け取らないメソッドの型は推論できないため、`Contract.Ensures(0 <Contract.Result<int>())` という事後条件を使用する必要があります。戻り値の型が `void` のメソッドの事後条件では `Contract.Result<T>()` を参照できません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-163">For example, the C# compiler is unable to infer types for methods that do not take any arguments, so it requires the following postcondition: `Contract.Ensures(0 <Contract.Result<int>())` Methods with a return type of `void` cannot refer to `Contract.Result<T>()` in their postconditions.</span></span>  
  
-   <span data-ttu-id="6ae09-164">事後条件の前の状態の値は、メソッドまたはプロパティの開始時の式の値を表します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-164">A prestate value in a postcondition refers to the value of an expression at the start of a method or property.</span></span> <span data-ttu-id="6ae09-165">使用される式は `Contract.OldValue<T>(e)` で、`T` は `e` の型です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-165">It uses the expression `Contract.OldValue<T>(e)`, where `T` is the type of `e`.</span></span> <span data-ttu-id="6ae09-166">その型をコンパイラが推論できる場合は、このジェネリック型引数を省略できます</span><span class="sxs-lookup"><span data-stu-id="6ae09-166">You can omit the generic type argument whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="6ae09-167">(たとえば、この式は引数を受け取るため、C# コンパイラでは常に型が推論されます)。`e` に使用できる値と、古い式を使用できるコンテキストについては、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-167">(For example, the C# compiler always infers the type because it takes an argument.) There are several restrictions on what can occur in `e` and the contexts in which an old expression may appear.</span></span> <span data-ttu-id="6ae09-168">まず、古い式に別の古い式を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-168">An old expression cannot contain another old expression.</span></span> <span data-ttu-id="6ae09-169">また、最も重要な点として、古い式で参照する値は、メソッドの事前条件の状態に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-169">Most importantly, an old expression must refer to a value that existed in the method's precondition state.</span></span> <span data-ttu-id="6ae09-170">つまり、古い式は、メソッドの事前条件が `true` であれば評価できる式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-170">In other words, it must be an expression that can be evaluated as long as the method's precondition is `true`.</span></span> <span data-ttu-id="6ae09-171">この規則のいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-171">Here are several instances of that rule.</span></span>  
  
    -   <span data-ttu-id="6ae09-172">値がメソッドの事前条件の状態に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-172">The value must exist in the method's precondition state.</span></span> <span data-ttu-id="6ae09-173">オブジェクトのフィールドを参照するには、オブジェクトが常に null 以外であることが事前条件によって保証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-173">In order to reference a field on an object, the preconditions must guarantee that that object is always non-null.</span></span>  
  
    -   <span data-ttu-id="6ae09-174">古い式でメソッドの戻り値を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-174">You cannot refer to the method's return value in an old expression:</span></span>  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   <span data-ttu-id="6ae09-175">古い式で `out` パラメーターを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-175">You cannot refer to `out` parameters in an old expression.</span></span>  
  
    -   <span data-ttu-id="6ae09-176">量指定子の範囲がメソッドの戻り値に依存する場合は、量指定子のバインド変数に依存する古い式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-176">An old expression cannot depend on the bound variable of a quantifier if the range of the quantifier depends on the return value of the method:</span></span>  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   <span data-ttu-id="6ae09-177">古い式で <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> または <xref:System.Diagnostics.Contracts.Contract.Exists%2A> の呼び出しの匿名デリゲートのパラメーターを参照することはできません (メソッド呼び出しのインデクサーまたは引数として使用されている場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-177">An old expression cannot refer to the parameter of the anonymous delegate in a <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> call unless it is used as an indexer or argument to a method call:</span></span>  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   <span data-ttu-id="6ae09-178">古い式の値が匿名デリゲートのパラメーターに依存している場合、古い式をその匿名デリゲートの本体に含めることはできません (匿名デリゲートが <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> メソッドまたは <xref:System.Diagnostics.Contracts.Contract.Exists%2A> メソッドの引数である場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-178">An old expression cannot occur in the body of an anonymous delegate if the value of the old expression depends on any of the parameters of the anonymous delegate, unless the anonymous delegate is an argument to the <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> method:</span></span>  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   <span data-ttu-id="6ae09-179">コントラクトはメソッド本体の前にあるため、`Out` パラメーターは問題になります。ほとんどのコンパイラでは、事後条件で `out` パラメーターを参照することは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-179">`Out` parameters present a problem because contracts appear before the body of the method, and most compilers do not allow references to `out` parameters in postconditions.</span></span> <span data-ttu-id="6ae09-180">この問題を解決するために、<xref:System.Diagnostics.Contracts.Contract> クラスには <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> メソッドが用意されています。このメソッドを使用すると、`out` パラメーターに基づく事後条件を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-180">To solve this problem, the <xref:System.Diagnostics.Contracts.Contract> class provides the <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method, which allows a postcondition based on an `out` parameter.</span></span>  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         <span data-ttu-id="6ae09-181"><xref:System.Diagnostics.Contracts.Contract.OldValue%2A> メソッドと同様に、コンパイラが型を推論できる場合はジェネリック型パラメーターを省略できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-181">As with the <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> method, you can omit the generic type parameter whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="6ae09-182">このメソッドの呼び出しは、コントラクト リライターによって `out` パラメーターの値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-182">The contract rewriter replaces the method call with the value of the `out` parameter.</span></span> <span data-ttu-id="6ae09-183"><xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> メソッドは事後条件でしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-183">The <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method may appear only in postconditions.</span></span> <span data-ttu-id="6ae09-184">このメソッドの引数は、`out` パラメーターか、構造体の `out` パラメーターのフィールド</span><span class="sxs-lookup"><span data-stu-id="6ae09-184">The argument to the method must be an `out` parameter or a field of a structure `out` parameter.</span></span> <span data-ttu-id="6ae09-185">(構造体コンストラクターの事後条件でフィールドを参照する場合にも便利です) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-185">The latter is also useful when referring to fields in the postcondition of a structure constructor.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ae09-186">現在、コード コントラクト分析ツールでは、`out` パラメーターが正しく初期化されているかどうかはチェックされません。事後条件に含まれていても無視されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-186">Currently, the code contract analysis tools do not check whether `out` parameters are initialized properly and disregard their mention in the postcondition.</span></span> <span data-ttu-id="6ae09-187">したがって、前の例で、コントラクトの後の行で `x` に整数を代入せずにこの値をそのまま使用しても、コンパイラで適切なエラーが生成されません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-187">Therefore, in the previous example, if the line after the contract had used the value of `x` instead of assigning an integer to it, a compiler would not issue the correct error.</span></span> <span data-ttu-id="6ae09-188">ただし、CONTRACTS_FULL プリプロセッサ シンボルが定義されていないビルド (リリース ビルドなど) では、コンパイラでエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-188">However, on a build where the CONTRACTS_FULL preprocessor symbol is not defined (such asa release build), the compiler will issue an error.</span></span>  
  
## <a name="invariants"></a><span data-ttu-id="6ae09-189">インバリアント</span><span class="sxs-lookup"><span data-stu-id="6ae09-189">Invariants</span></span>  
 <span data-ttu-id="6ae09-190">オブジェクト不変条件とは、そのオブジェクトがクライアントに表示される場合に常にクラスの各インスタンスに対して true になる必要があり、</span><span class="sxs-lookup"><span data-stu-id="6ae09-190">Object invariants are conditions that should be true for each instance of a class whenever that object is visible to a client.</span></span> <span data-ttu-id="6ae09-191">オブジェクトが正しいと見なされる条件を表します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-191">They express the conditions under which the object is considered to be correct.</span></span>  
  
 <span data-ttu-id="6ae09-192">インバリアントなメソッドは、<xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> 属性でマークされることによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-192">The invariant methods are identified by being marked with the <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> attribute.</span></span> <span data-ttu-id="6ae09-193">インバリアントなメソッドには、<xref:System.Diagnostics.Contracts.Contract.Invariant%2A> メソッドの一連の呼び出し以外のコードが含まれていない必要があります。それらの呼び出しでは、次の例のように、個々の不変式を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-193">The invariant methods must contain no code except for a sequence of calls to the <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> method, each of which specifies an individual invariant, as shown in the following example.</span></span>  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 <span data-ttu-id="6ae09-194">不変式は、CONTRACTS_FULL プリプロセッサ シンボルによって条件付きで定義され、</span><span class="sxs-lookup"><span data-stu-id="6ae09-194">Invariants are conditionally defined by the CONTRACTS_FULL preprocessor symbol.</span></span> <span data-ttu-id="6ae09-195">ランタイム チェックで各パブリック メソッドの最後にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-195">During run-time checking, invariants are checked at the end of each public method.</span></span> <span data-ttu-id="6ae09-196">不変式が同じクラスのパブリック メソッドを参照している場合は、通常ならそのパブリック メソッドの最後に実行される不変式のチェックが無効になり、</span><span class="sxs-lookup"><span data-stu-id="6ae09-196">If an invariant mentions a public method in the same class, the invariant check that would normally happen at the end of that public method is disabled.</span></span> <span data-ttu-id="6ae09-197">そのクラスの一番外側のメソッド呼び出しの最後にのみチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-197">Instead, the check occurs only at the end of the outermost method call to that class.</span></span> <span data-ttu-id="6ae09-198">別のクラスのメソッドの呼び出しのためにクラスへの再入がなされる場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-198">This also happens if the class is re-entered because of a call to a method on another class.</span></span> <span data-ttu-id="6ae09-199">不変式のチェックは、オブジェクト ファイナライザーや、<xref:System.IDisposable.Dispose%2A> メソッドを実装するメソッドに対しては実行されません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-199">Invariants are not checked for object finalizers or for any methods that implement the <xref:System.IDisposable.Dispose%2A> method.</span></span>  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a><span data-ttu-id="6ae09-200">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="6ae09-200">Usage Guidelines</span></span>  
  
### <a name="contract-ordering"></a><span data-ttu-id="6ae09-201">コントラクトの順序</span><span class="sxs-lookup"><span data-stu-id="6ae09-201">Contract Ordering</span></span>  
 <span data-ttu-id="6ae09-202">メソッドのコントラクトを記述する際に使用する必要がある要素の順序を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-202">The following table shows the order of elements you should use when you write method contracts.</span></span>  
  
|`If-then-throw statements`|<span data-ttu-id="6ae09-203">下位互換性のあるパブリックな事前条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-203">Backward-compatible public preconditions</span></span>|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|<span data-ttu-id="6ae09-204">すべてのパブリックな事前条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-204">All public preconditions.</span></span>|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="6ae09-205">すべてのパブリックな (標準の) 事後条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-205">All public (normal) postconditions.</span></span>|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="6ae09-206">すべてのパブリックな例外の事後条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-206">All public exceptional postconditions.</span></span>|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="6ae09-207">すべてのプライベートな/内部の (標準の) 事後条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-207">All private/internal (normal) postconditions.</span></span>|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="6ae09-208">すべてのプライベートな/内部の例外の事後条件。</span><span class="sxs-lookup"><span data-stu-id="6ae09-208">All private/internal exceptional postconditions.</span></span>|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|<span data-ttu-id="6ae09-209">`if`-`then`-`throw` スタイルの事前条件を他のコントラクトなしで使用する場合は、<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> を呼び出して、前の if チェックがすべて事前条件であることを示します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-209">If using `if`-`then`-`throw` style preconditions without any other contracts, place a call to <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> to indicate that all previous if checks are preconditions.</span></span>|  
  
<a name="purity"></a>   
### <a name="purity"></a><span data-ttu-id="6ae09-210">純粋性</span><span class="sxs-lookup"><span data-stu-id="6ae09-210">Purity</span></span>  
 <span data-ttu-id="6ae09-211">コントラクトの中で呼び出されるメソッドは、すべて純粋である (既存の状態を更新しない) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ae09-211">All methods that are called within a contract must be pure; that is, they must not update any preexisting state.</span></span> <span data-ttu-id="6ae09-212">メソッドに入った後に作成されたオブジェクトは、そのピュア メソッドによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-212">A pure method is allowed to modify objects that have been created after entry into the pure method.</span></span>  
  
 <span data-ttu-id="6ae09-213">コード コントラクト ツールでは、現在、次のコード要素が純粋と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-213">Code contract tools currently assume that the following code elements are pure:</span></span>  
  
-   <span data-ttu-id="6ae09-214"><xref:System.Diagnostics.Contracts.PureAttribute> でマークされたメソッド。</span><span class="sxs-lookup"><span data-stu-id="6ae09-214">Methods that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span>  
  
-   <span data-ttu-id="6ae09-215"><xref:System.Diagnostics.Contracts.PureAttribute> でマークされた型 (この属性はその型のすべてのメソッドに適用されます)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-215">Types that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute> (the attribute applies to all the type's methods).</span></span>  
  
-   <span data-ttu-id="6ae09-216">プロパティの get アクセサー。</span><span class="sxs-lookup"><span data-stu-id="6ae09-216">Property get accessors.</span></span>  
  
-   <span data-ttu-id="6ae09-217">演算子 (名前が "op" で始まり、1 つか 2 つのパラメーターを持ち、戻り値の型が void ではない静的メソッド)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-217">Operators (static methods whose names start with "op", and that have one or two parameters and a non-void return type).</span></span>  
  
-   <span data-ttu-id="6ae09-218">完全修飾名が "System.Diagnostics.Contracts.Contract"、"System.String"、"System.IO.Path"、または "System.Type" で始まるメソッド。</span><span class="sxs-lookup"><span data-stu-id="6ae09-218">Any method whose fully qualified name begins with "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path", or "System.Type".</span></span>  
  
-   <span data-ttu-id="6ae09-219">呼び出されたデリゲート (デリゲート型自体に <xref:System.Diagnostics.Contracts.PureAttribute> 属性が設定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="6ae09-219">Any invoked delegate, provided that the delegate type itself is attributed with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span> <span data-ttu-id="6ae09-220">デリゲート型の <xref:System.Predicate%601?displayProperty=nameWithType> と <xref:System.Comparison%601?displayProperty=nameWithType> は純粋と見なされます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-220">The delegate types <xref:System.Predicate%601?displayProperty=nameWithType> and <xref:System.Comparison%601?displayProperty=nameWithType> are considered pure.</span></span>  
  
<a name="visibility"></a>   
### <a name="visibility"></a><span data-ttu-id="6ae09-221">可視性</span><span class="sxs-lookup"><span data-stu-id="6ae09-221">Visibility</span></span>  
 <span data-ttu-id="6ae09-222">コントラクトで参照されるすべてのメンバーには、少なくとも親のメソッドと同じレベルの可視性が必要です。</span><span class="sxs-lookup"><span data-stu-id="6ae09-222">All members mentioned in a contract must be at least as visible as the method in which they appear.</span></span> <span data-ttu-id="6ae09-223">たとえば、パブリック メソッドの事前条件でプライベート フィールドを参照することはできません。そのようなコントラクトは、クライアントがメソッドの呼び出しの前に検証できません。</span><span class="sxs-lookup"><span data-stu-id="6ae09-223">For example, a private field cannot be mentioned in a precondition for a public method; clients cannot validate such a contract before they call the method.</span></span> <span data-ttu-id="6ae09-224">ただし、そのフィールドが <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute> でマークされている場合は、これらの規則から除外されます。</span><span class="sxs-lookup"><span data-stu-id="6ae09-224">However, if the field is marked with the <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, it is exempt from these rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ae09-225">例</span><span class="sxs-lookup"><span data-stu-id="6ae09-225">Example</span></span>  
 <span data-ttu-id="6ae09-226">次に、コード コントラクトの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ae09-226">The following example shows the use of code contracts.</span></span>  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
