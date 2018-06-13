---
title: 例外の作成とスロー (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 91676830d88ddee79c72211ab43b7be32fa8724e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336057"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a><span data-ttu-id="87885-102">例外の作成とスロー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="87885-102">Creating and Throwing Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="87885-103">例外は、プログラムの実行中にエラーが発生したことを示すために使われます。</span><span class="sxs-lookup"><span data-stu-id="87885-103">Exceptions are used to indicate that an error has occurred while running the program.</span></span> <span data-ttu-id="87885-104">エラーを説明する例外オブジェクトが作成された後、[throw](../../../csharp/language-reference/keywords/throw.md) キーワードで "*スロー*" されます。</span><span class="sxs-lookup"><span data-stu-id="87885-104">Exception objects that describe an error are created and then *thrown* with the [throw](../../../csharp/language-reference/keywords/throw.md) keyword.</span></span> <span data-ttu-id="87885-105">そのとき、ランタイムは最も互換性のある例外ハンドラーを検索します。</span><span class="sxs-lookup"><span data-stu-id="87885-105">The runtime then searches for the most compatible exception handler.</span></span>  
  
 <span data-ttu-id="87885-106">プログラマは、以下の条件が 1 つでも該当するときは、例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-106">Programmers should throw exceptions when one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="87885-107">メソッドは、定義されている機能を完了できません。</span><span class="sxs-lookup"><span data-stu-id="87885-107">The method cannot complete its defined functionality.</span></span>  
  
     <span data-ttu-id="87885-108">たとえば、メソッドへのパラメーターに無効な値が設定されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="87885-108">For example, if a parameter to a method has an invalid value:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   <span data-ttu-id="87885-109">オブジェクトの状態に基づくと、オブジェクトに対して行われた呼び出しが不適切です。</span><span class="sxs-lookup"><span data-stu-id="87885-109">An inappropriate call to an object is made, based on the object state.</span></span>  
  
     <span data-ttu-id="87885-110">たとえば、読み取り専用ファイルに書き込もうとしたような場合です。</span><span class="sxs-lookup"><span data-stu-id="87885-110">One example might be trying to write to a read-only file.</span></span> <span data-ttu-id="87885-111">オブジェクトの状態により操作が許可されない場合は、<xref:System.InvalidOperationException> のインスタンスまたはこのクラスの派生に基づくオブジェクトをスローします。</span><span class="sxs-lookup"><span data-stu-id="87885-111">In cases where an object state does not allow an operation, throw an instance of <xref:System.InvalidOperationException> or an object based on a derivation of this class.</span></span> <span data-ttu-id="87885-112"><xref:System.InvalidOperationException> オブジェクトをスローするメソッドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="87885-112">This is an example of a method that throws an <xref:System.InvalidOperationException> object:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   <span data-ttu-id="87885-113">メソッドへの引数が原因で例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="87885-113">When an argument to a method causes an exception.</span></span>  
  
     <span data-ttu-id="87885-114">この場合は、元の例外をキャッチして、<xref:System.ArgumentException> のインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-114">In this case, the original exception should be caught and an <xref:System.ArgumentException> instance should be created.</span></span> <span data-ttu-id="87885-115">元の例外は、<xref:System.Exception.InnerException%2A> パラメーターとして <xref:System.ArgumentException> のコンストラクターに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-115">The original exception should be passed to the constructor of the <xref:System.ArgumentException> as the <xref:System.Exception.InnerException%2A> parameter:</span></span>  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 <span data-ttu-id="87885-116">例外には、<xref:System.Exception.StackTrace%2A> というプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87885-116">Exceptions contain a property named <xref:System.Exception.StackTrace%2A>.</span></span> <span data-ttu-id="87885-117">この文字列には、現在の呼び出し履歴でのメソッドの名前と、各メソッドの例外がスローされたファイル名と行番号が含まれます。</span><span class="sxs-lookup"><span data-stu-id="87885-117">This string contains the name of the methods on the current call stack, together with the file name and line number where the exception was thrown for each method.</span></span> <span data-ttu-id="87885-118">スタック トレースを開始するポイントから例外をスローする必要があるため、共通言語ランタイム (CLR) によって `throw` ステートメントのポイントから <xref:System.Exception.StackTrace%2A> オブジェクトが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="87885-118">A <xref:System.Exception.StackTrace%2A> object is created automatically by the common language runtime (CLR) from the point of the `throw` statement, so that exceptions must be thrown from the point where the stack trace should begin.</span></span>  
  
 <span data-ttu-id="87885-119">すべての例外には、<xref:System.Exception.Message%2A> というプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87885-119">All exceptions contain a property named <xref:System.Exception.Message%2A>.</span></span> <span data-ttu-id="87885-120">例外の原因を説明するには、この文字列を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-120">This string should be set to explain the reason for the exception.</span></span> <span data-ttu-id="87885-121">機密性の高い情報はメッセージ テキストに入れないようにする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="87885-121">Note that information that is sensitive to security should not be put in the message text.</span></span> <span data-ttu-id="87885-122"><xref:System.ArgumentException> には、<xref:System.Exception.Message%2A> に加え、例外がスローされる原因となる引数の名前に設定される <xref:System.ArgumentException.ParamName%2A> というプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="87885-122">In addition to <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contains a property named <xref:System.ArgumentException.ParamName%2A> that should be set to the name of the argument that caused the exception to be thrown.</span></span> <span data-ttu-id="87885-123">プロパティ セッターの場合、<xref:System.ArgumentException.ParamName%2A> は `value` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-123">In the case of a property setter, <xref:System.ArgumentException.ParamName%2A> should be set to `value`.</span></span>  
  
 <span data-ttu-id="87885-124">パブリックのプロテクト メソッド メンバーは、意図された機能を完了できない場合は常に例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-124">Public and protected methods members should throw exceptions whenever they cannot complete their intended functions.</span></span> <span data-ttu-id="87885-125">スローされる例外クラスは、エラー状態に適合する使用可能な例外の中で最も具体的なものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-125">The exception class that is thrown should be the most specific exception available that fits the error conditions.</span></span> <span data-ttu-id="87885-126">これらの例外はクラスの機能の一部として文書化する必要があり、派生クラスまたは元のクラスの更新では、旧バージョンとの互換性のために同じ動作を維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-126">These exceptions should be documented as part of the class functionality, and derived classes or updates to the original class should retain the same behavior for backward compatibility.</span></span>  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a><span data-ttu-id="87885-127">例外をスローするときに避ける必要があること</span><span class="sxs-lookup"><span data-stu-id="87885-127">Things to Avoid When Throwing Exceptions</span></span>  
 <span data-ttu-id="87885-128">次の一覧は、例外をスローするときに避ける必要があることです。</span><span class="sxs-lookup"><span data-stu-id="87885-128">The following list identifies practices to avoid when throwing exceptions:</span></span>  
  
-   <span data-ttu-id="87885-129">通常の実行の一部として、例外を使ってプログラムのフローを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="87885-129">Exceptions should not be used to change the flow of a program as part of ordinary execution.</span></span> <span data-ttu-id="87885-130">例外は、エラー状態の報告と処理のためだけに使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-130">Exceptions should only be used to report and handle error conditions.</span></span>  
  
-   <span data-ttu-id="87885-131">スローする代わりに、戻り値またはパラメーターとして例外を返さないでください。</span><span class="sxs-lookup"><span data-stu-id="87885-131">Exceptions should not be returned as a return value or parameter instead of being thrown.</span></span>  
  
-   <span data-ttu-id="87885-132">自作のソース コードからは、意図的に <xref:System.Exception?displayProperty=nameWithType>、<xref:System.SystemException?displayProperty=nameWithType>、<xref:System.NullReferenceException?displayProperty=nameWithType>、または <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> をスローしないでください。</span><span class="sxs-lookup"><span data-stu-id="87885-132">Do not throw <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, or <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> intentionally from your own source code.</span></span>  
  
-   <span data-ttu-id="87885-133">デバッグ モードではスローでき、リリース モードではスローできない例外は、作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="87885-133">Do not create exceptions that can be thrown in debug mode but not release mode.</span></span> <span data-ttu-id="87885-134">開発フェーズ中に実行時エラーを識別するには、代わりにデバッグ アサートを使ってください。</span><span class="sxs-lookup"><span data-stu-id="87885-134">To identify run-time errors during the development phase, use Debug Assert instead.</span></span>  
  
## <a name="defining-exception-classes"></a><span data-ttu-id="87885-135">例外クラスの定義</span><span class="sxs-lookup"><span data-stu-id="87885-135">Defining Exception Classes</span></span>  
 <span data-ttu-id="87885-136">プログラムでは、<xref:System> 名前空間で事前定義された例外クラスをスローするか (上記の場合を除きます)、<xref:System.Exception> から派生することで独自の例外クラスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="87885-136">Programs can throw a predefined exception class in the <xref:System> namespace (except where previously noted), or create their own exception classes by deriving from <xref:System.Exception>.</span></span> <span data-ttu-id="87885-137">派生クラスでは、少なくとも 4 つのコンストラクターを定義する必要があります。既定のコンストラクター、メッセージ プロパティを設定するコンストラクター、<xref:System.Exception.Message%2A> プロパティと <xref:System.Exception.InnerException%2A> プロパティの両方を設定するコンストラクター、</span><span class="sxs-lookup"><span data-stu-id="87885-137">The derived classes should define at least four constructors: one default constructor, one that sets the message property, and one that sets both the <xref:System.Exception.Message%2A> and <xref:System.Exception.InnerException%2A> properties.</span></span> <span data-ttu-id="87885-138">そして 4 番目は例外のシリアル化に使われるコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="87885-138">The fourth constructor is used to serialize the exception.</span></span> <span data-ttu-id="87885-139">新しい例外クラスは、シリアル化可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-139">New exception classes should be serializable.</span></span> <span data-ttu-id="87885-140">例:</span><span class="sxs-lookup"><span data-stu-id="87885-140">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 <span data-ttu-id="87885-141">例外クラスへの新しいプロパティの追加は、プロパティによって提供されるデータが例外の解決に役立つ場合にのみ行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-141">New properties should only be added to the exception class when the data they provide is useful to resolving the exception.</span></span> <span data-ttu-id="87885-142">派生例外クラスに新しいプロパティを追加する場合は、`ToString()` をオーバーライドして追加情報を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="87885-142">If new properties are added to the derived exception class, `ToString()` should be overridden to return the added information.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="87885-143">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="87885-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="87885-144">参照</span><span class="sxs-lookup"><span data-stu-id="87885-144">See Also</span></span>  
 [<span data-ttu-id="87885-145">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="87885-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="87885-146">例外と例外処理</span><span class="sxs-lookup"><span data-stu-id="87885-146">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)  
 [<span data-ttu-id="87885-147">例外階層</span><span class="sxs-lookup"><span data-stu-id="87885-147">Exception Hierarchy</span></span>](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [<span data-ttu-id="87885-148">例外処理</span><span class="sxs-lookup"><span data-stu-id="87885-148">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)
