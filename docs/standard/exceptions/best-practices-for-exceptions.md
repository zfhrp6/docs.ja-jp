---
title: "例外の推奨事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87f9287c3714416ee5d6b63f3c9db311bb97b131
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2017
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="25d81-102">例外の推奨事項</span><span class="sxs-lookup"><span data-stu-id="25d81-102">Best practices for exceptions</span></span>

<span data-ttu-id="25d81-103">適切にデザインされたアプリケーションは、アプリケーションのクラッシュを防ぐために、例外やエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="25d81-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="25d81-104">このセクションでは、例外の処理と作成のためのベスト プラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="25d81-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="25d81-105">try/catch/finally ブロックを使用する</span><span class="sxs-lookup"><span data-stu-id="25d81-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="25d81-106">`try`/`catch`/`finally` ブロックを使用して、例外を生成する可能性のあるコードを囲みます。</span><span class="sxs-lookup"><span data-stu-id="25d81-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="25d81-107">`catch` ブロックでは、常に特定の例外から一般的な例外の順に例外を配置します。</span><span class="sxs-lookup"><span data-stu-id="25d81-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="25d81-108">回復できるかどうかに関わらず、`finally` ブロックを使用してリソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="25d81-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="25d81-109">例外をスローせずに一般的な状態を処理する</span><span class="sxs-lookup"><span data-stu-id="25d81-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="25d81-110">発生する可能性があり、例外をトリガーする可能性がある状態に対し、例外を回避する方法で処理することを検討します。</span><span class="sxs-lookup"><span data-stu-id="25d81-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="25d81-111">たとえば、既に終了している接続を終了しようとすると、`InvalidOperationException` を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="25d81-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="25d81-112">`if` ステートメントを使用して、終了しようとする前に接続状態を確認することで、これを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="25d81-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="25d81-113">終了する前に接続状態を確認しない場合は、`InvalidOperationException` 例外をキャッチする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="25d81-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="25d81-114">選択するメソッドは、予期されるイベント発生頻度によって決まります。</span><span class="sxs-lookup"><span data-stu-id="25d81-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="25d81-115">イベントが頻繁には発生しない場合、つまり、イベントが本当に例外的であり、エラー (予期しないファイルの終端の検出など) を示す場合に、例外処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="25d81-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="25d81-116">例外処理を使用すると、通常の状況では、実行されるコードが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="25d81-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="25d81-117">イベントが定期的に発生し、通常の実行の一部であると見なせる場合は、コード内でエラー条件をチェックします。</span><span class="sxs-lookup"><span data-stu-id="25d81-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="25d81-118">一般的なエラー条件をチェックするときに、例外を回避するためにより少ないコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="25d81-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="25d81-119">例外を回避するようにクラスを設計する</span><span class="sxs-lookup"><span data-stu-id="25d81-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="25d81-120">クラスは、例外をトリガーする呼び出しを行うことを回避できるようにするメソッドとプロパティを提供できます。</span><span class="sxs-lookup"><span data-stu-id="25d81-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="25d81-121">たとえば、<xref:System.IO.FileStream> クラスには、ファイルの終端に到達したかどうかを判別するために役立つメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="25d81-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="25d81-122">これらは、ファイルの終端を越えて読み取りを実行しようとした場合にも例外がスローされないようにするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="25d81-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="25d81-123">次の例では、例外をトリガーすることなく、ファイルの末尾まで読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25d81-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="25d81-124">例外が返されるのを回避するもう 1 つの方法は、非常に一般的なエラーの場合に、例外をスローする代わりに null を返すことです。</span><span class="sxs-lookup"><span data-stu-id="25d81-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="25d81-125">非常に一般的なエラーは、通常の制御の流れと見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="25d81-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="25d81-126">このような場合は、null を返すことによって、アプリケーションのパフォーマンスへの影響を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="25d81-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="25d81-127">エラー コードを返す代わりに、例外をスローする</span><span class="sxs-lookup"><span data-stu-id="25d81-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="25d81-128">呼び出しのコードはリターン コードを確認しないので、例外によって、エラーを見過ごさないようにします。</span><span class="sxs-lookup"><span data-stu-id="25d81-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="25d81-129">事前定義済みの .NET の例外の種類を使用する</span><span class="sxs-lookup"><span data-stu-id="25d81-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="25d81-130">事前定義の例外クラスが適用されない場合に限り、新しい例外クラスを導入します。</span><span class="sxs-lookup"><span data-stu-id="25d81-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="25d81-131">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="25d81-131">For example:</span></span>

- <span data-ttu-id="25d81-132">オブジェクトの現在の状態に対して、プロパティの設定またはメソッドの呼び出しが適切でない場合は、<xref:System.InvalidOperationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="25d81-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="25d81-133"><xref:System.ArgumentException> 例外または <xref:System.ArgumentException> から派生する定義済みのクラスの 1 つをスローします。</span><span class="sxs-lookup"><span data-stu-id="25d81-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="25d81-134">例外クラス名の末尾に `Exception` という単語を付加する</span><span class="sxs-lookup"><span data-stu-id="25d81-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="25d81-135">カスタム例外が必要な場合は、適切に名前を付け、<xref:System.Exception> クラスから派生させます。</span><span class="sxs-lookup"><span data-stu-id="25d81-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="25d81-136">例:</span><span class="sxs-lookup"><span data-stu-id="25d81-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="25d81-137">カスタム例外クラスに 3 つのコンストラクターを含める</span><span class="sxs-lookup"><span data-stu-id="25d81-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="25d81-138">独自の例外クラスを作成するときに、少なくとも 3 つの共通コンストラクターを使用します。それらは、既定のコンストラクター、文字列メッセージを受け取るコンストラクター、および文字列メッセージと内部例外を受け取るコンストラクターです。</span><span class="sxs-lookup"><span data-stu-id="25d81-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="25d81-139"><xref:System.Exception.%23ctor>、既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="25d81-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="25d81-140">文字列メッセージを受け取る <xref:System.Exception.%23ctor%28System.String%29>。</span><span class="sxs-lookup"><span data-stu-id="25d81-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="25d81-141">文字列メッセージと内部例外を受け取る <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>。</span><span class="sxs-lookup"><span data-stu-id="25d81-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="25d81-142">例については、「[方法: ユーザー定義の例外を作成する](how-to-create-user-defined-exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25d81-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="25d81-143">コードがリモートで実行されるときに、例外データが利用できるようにする</span><span class="sxs-lookup"><span data-stu-id="25d81-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="25d81-144">ユーザー定義例外を作成するときには、リモートで実行されるコードで例外のメタデータを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="25d81-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="25d81-145">たとえば、アプリ ドメインをサポートする .NET 実装にはアプリ ドメイン全体で例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="25d81-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="25d81-146">アプリ ドメイン A が、例外をスローするコードを実行するアプリ ドメイン B を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="25d81-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="25d81-147">アプリ ドメイン A が例外を適切にキャッチして処理するには、アプリ ドメイン B によりスローされた例外が含まれているアセンブリを検出できる必要があります。アプリ ドメイン B が、アプリ ドメイン A のアプリケーション ベースではなく、自身のアプリケーション ベースの下のアセンブリに含まれている例外をスローする場合、アプリ ドメイン A は、例外を検出できなくなり、共通言語ランタイムが <xref:System.IO.FileNotFoundException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="25d81-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="25d81-148">このような状況を回避するには、例外情報が格納されているアセンブリを次のいずれかの方法で配置します。</span><span class="sxs-lookup"><span data-stu-id="25d81-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="25d81-149">2 つのアプリ ドメインが共有する共通アプリケーション ベースにアセンブリを配置する。</span><span class="sxs-lookup"><span data-stu-id="25d81-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="25d81-150">\- または</span><span class="sxs-lookup"><span data-stu-id="25d81-150">\- or -</span></span>

- <span data-ttu-id="25d81-151">ドメインが共通アプリケーション ベースを共有していない場合には、例外情報が格納されているアセンブリに厳密な名前で署名し、グローバル アセンブリ キャッシュにこのアセンブリを配置する。</span><span class="sxs-lookup"><span data-stu-id="25d81-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="include-a-localized-description-string-in-every-exception"></a><span data-ttu-id="25d81-152">すべての例外に、ローカライズした説明文字列を含める</span><span class="sxs-lookup"><span data-stu-id="25d81-152">Include a localized description string in every exception</span></span>

<span data-ttu-id="25d81-153">ユーザーに対して表示されるエラー メッセージは、例外クラスの名前ではなく、スローされた例外の説明文字列から派生されます。</span><span class="sxs-lookup"><span data-stu-id="25d81-153">The error message that the user sees is derived from the description string of the exception that was thrown, and not from the name of the exception class.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="25d81-154">文法的に正しいエラー メッセージを使用する</span><span class="sxs-lookup"><span data-stu-id="25d81-154">Use grammatically correct error messages</span></span>

<span data-ttu-id="25d81-155">明確な文を記述し、末尾に句点を含めます。</span><span class="sxs-lookup"><span data-stu-id="25d81-155">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="25d81-156">例外の説明文字列の文の末尾には、必ず句点を使用します。</span><span class="sxs-lookup"><span data-stu-id="25d81-156">Each sentence in a description string of an exception should end in a period.</span></span> <span data-ttu-id="25d81-157">たとえば、「ログ テーブルがオーバーフローしました。」</span><span class="sxs-lookup"><span data-stu-id="25d81-157">For example, "The log table has overflowed."</span></span> <span data-ttu-id="25d81-158">適切な説明文字列です。</span><span class="sxs-lookup"><span data-stu-id="25d81-158">would be an appropriate description string.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="25d81-159">カスタム例外で、必要に応じて追加のプロパティを提供する</span><span class="sxs-lookup"><span data-stu-id="25d81-159">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="25d81-160">プログラミングの点で追加情報が役立つ場合にだけ、(説明文字列以外の) 例外の追加プロパティを含めてください。</span><span class="sxs-lookup"><span data-stu-id="25d81-160">Provide additional properties for an exception (in addition to the description string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="25d81-161">たとえば、<xref:System.IO.FileNotFoundException> には <xref:System.IO.FileNotFoundException.FileName> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="25d81-161">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="25d81-162">スタック トレースが役に立つように throw ステートメントを配置する</span><span class="sxs-lookup"><span data-stu-id="25d81-162">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="25d81-163">例外がスローされたステートメントからスタック トレースが開始され、例外をキャッチした `catch` ステートメントでトレースが終了します。</span><span class="sxs-lookup"><span data-stu-id="25d81-163">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="25d81-164">例外ビルダー メソッドを使用する</span><span class="sxs-lookup"><span data-stu-id="25d81-164">Use exception builder methods</span></span>

<span data-ttu-id="25d81-165">一般に、クラスはクラス実装内の複数の位置で同一の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="25d81-165">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="25d81-166">コードが長くなることを防ぐため、例外を作成して返すヘルパー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="25d81-166">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="25d81-167">例:</span><span class="sxs-lookup"><span data-stu-id="25d81-167">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="25d81-168">場合によっては、例外のコンストラクターを使用して例外を作成する方が適切な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="25d81-168">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="25d81-169">例など、グローバル例外クラスは、<xref:System.ArgumentException>です。</span><span class="sxs-lookup"><span data-stu-id="25d81-169">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="25d81-170">例外をスローするときに、中間結果を削除する</span><span class="sxs-lookup"><span data-stu-id="25d81-170">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="25d81-171">呼び出し元が、メソッドから例外がスローされるときに副作用が発生しないと仮定できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="25d81-171">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="25d81-172">たとえば、ある口座から現金を引き出して別の口座に預金することで送金を行うコードがあって、預金の実行中に例外がスローされた場合、引き出しが有効のままにしておきたくはないはずです。</span><span class="sxs-lookup"><span data-stu-id="25d81-172">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="25d81-173">この状況に対処する方法の 1 つは、預金トランザクションによってスローされた例外をキャッチし、引き出しをロールバックすることです。</span><span class="sxs-lookup"><span data-stu-id="25d81-173">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

<span data-ttu-id="25d81-174">この例では、`throw` を使用して、元の例外を再スローすることを示しています。これにより、呼び出し元が <xref:System.Exception.InnerException> プロパティを確認することなく、問題の本当の原因を容易に確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="25d81-174">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="25d81-175">別の方法は、新しい例外をスローして元の例外を内部例外として含めることです。</span><span class="sxs-lookup"><span data-stu-id="25d81-175">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="25d81-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="25d81-176">See Also</span></span>  
[<span data-ttu-id="25d81-177">例外</span><span class="sxs-lookup"><span data-stu-id="25d81-177">Exceptions</span></span>](index.md)
