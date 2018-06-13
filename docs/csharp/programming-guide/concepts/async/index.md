---
title: Async および Await を使用した非同期プログラミング (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: b1797a6d37728021820f5dfa5c01a7ee0c972f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339100"
---
# <a name="asynchronous-programming-with-async-and-await-c"></a><span data-ttu-id="e0c2b-102">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-102">Asynchronous programming with async and await (C#)</span></span>
<span data-ttu-id="e0c2b-103">パフォーマンスのボトルネックを回避しアプリケーション全体の応答性を向上させるために、非同期プログラミングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-103">You can avoid performance bottlenecks and enhance the overall responsiveness of your application by using asynchronous programming.</span></span> <span data-ttu-id="e0c2b-104">ただ、非同期アプリケーションを作成する従来の方法は複雑で、プログラムの作成、デバッグ、保守が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-104">However, traditional techniques for writing asynchronous applications can be complicated, making them difficult to write, debug, and maintain.</span></span>  
  
<span data-ttu-id="e0c2b-105">[C# 5](../../../whats-new/index.md#previous-versions) では、.NET Framework 4.5 以降、.NET Core および Windows ランタイムの非同期サポートを利用した "非同期プログラミング" と呼ばれる簡単な方法が導入されました。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-105">[C# 5](../../../whats-new/index.md#previous-versions) introduced a simplified approach, async programming, that leverages asynchronous support in the .NET Framework 4.5 and higher, .NET Core, and the Windows Runtime.</span></span> <span data-ttu-id="e0c2b-106">コンパイラがこれまで開発者が行っていた難しい作業を実行し、アプリケーションは同期コードに類似した論理構造を保持します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-106">The compiler does the difficult work that the developer used to do, and your application retains a logical structure that resembles synchronous code.</span></span> <span data-ttu-id="e0c2b-107">その結果、わずかな作業量で非同期プログラミングのすべての利点を得られます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-107">As a result, you get all the advantages of asynchronous programming with a fraction of the effort.</span></span>  
  
<span data-ttu-id="e0c2b-108">このトピックでは、非同期プログラミングをいつ、どのように使用するかの概要を紹介します。詳細と例を含むをサポート トピックへのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-108">This topic provides an overview of when and how to use async programming and includes links to support topics that contain details and examples.</span></span>  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a><span data-ttu-id="e0c2b-109">非同期による応答性の改善</span><span class="sxs-lookup"><span data-stu-id="e0c2b-109">Async improves responsiveness</span></span>  
 <span data-ttu-id="e0c2b-110">Web アクセスなど、ブロックされる可能性がある操作には、非同期が必要となります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-110">Asynchrony is essential for activities that are potentially blocking, such as web access.</span></span> <span data-ttu-id="e0c2b-111">Web リソースへのアクセスには、遅延が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-111">Access to a web resource sometimes is slow or delayed.</span></span> <span data-ttu-id="e0c2b-112">このような操作が同期処理内でブロックされた場合、アプリケーション全体が待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-112">If such an activity is blocked in a synchronous process, the entire application must wait.</span></span> <span data-ttu-id="e0c2b-113">非同期処理では、ブロックする可能性のあるタスク終了するまで、アプリケーションは Web リソースに依存しない他の操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-113">In an asynchronous process, the application can continue with other work that doesn't depend on the web resource until the potentially blocking task finishes.</span></span>  
  
 <span data-ttu-id="e0c2b-114">非同期プログラミングによって応答性を向上する一般的な領域を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-114">The following table shows typical areas where asynchronous programming improves responsiveness.</span></span> <span data-ttu-id="e0c2b-115">.NET および Windows ランタイムの API の一覧には、非同期のプログラミングをサポートするメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-115">The listed APIs from .NET and the Windows Runtime contain methods that support async programming.</span></span>  
  
| <span data-ttu-id="e0c2b-116">アプリケーション領域</span><span class="sxs-lookup"><span data-stu-id="e0c2b-116">Application area</span></span>    | <span data-ttu-id="e0c2b-117">非同期メソッドがある .NET 型</span><span class="sxs-lookup"><span data-stu-id="e0c2b-117">.NET types with async methods</span></span>     | <span data-ttu-id="e0c2b-118">非同期メソッドがある Windows ランタイム型</span><span class="sxs-lookup"><span data-stu-id="e0c2b-118">Windows Runtime types with async methods</span></span>  |
|---------------------|-----------------------------------|-------------------------------------------|
|<span data-ttu-id="e0c2b-119">Web アクセス</span><span class="sxs-lookup"><span data-stu-id="e0c2b-119">Web access</span></span>|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|<span data-ttu-id="e0c2b-120">ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="e0c2b-120">Working with files</span></span>|<span data-ttu-id="e0c2b-121"><xref:System.IO.StreamWriter>、<xref:System.IO.StreamReader>、<xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="e0c2b-121"><xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader></span></span>|<xref:Windows.Storage.StorageFile>|  
|<span data-ttu-id="e0c2b-122">イメージの処理</span><span class="sxs-lookup"><span data-stu-id="e0c2b-122">Working with images</span></span>||<span data-ttu-id="e0c2b-123"><xref:Windows.Media.Capture.MediaCapture>、<xref:Windows.Graphics.Imaging.BitmapEncoder>、<xref:Windows.Graphics.Imaging.BitmapDecoder></span><span class="sxs-lookup"><span data-stu-id="e0c2b-123"><xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder></span></span>|  
|<span data-ttu-id="e0c2b-124">WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="e0c2b-124">WCF programming</span></span>|[<span data-ttu-id="e0c2b-125">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="e0c2b-125">Synchronous and Asynchronous Operations</span></span>](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
<span data-ttu-id="e0c2b-126">非同期性は、UI スレッドにアクセスするアプリケーションに対して特に有効です。これは、すべての UI 関連のアクティビティが一般的に 1 つのスレッドを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-126">Asynchrony proves especially valuable for applications that access the UI thread because all UI-related activity usually shares one thread.</span></span> <span data-ttu-id="e0c2b-127">同期アプリケーションでは、1 つのプロセスがブロックされるとすべてがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-127">If any process is blocked in a synchronous application, all are blocked.</span></span> <span data-ttu-id="e0c2b-128">アプリケーションが応答を停止するため、待機状態であるとは考えずに失敗したと結論付けることもあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-128">Your application stops responding, and you might conclude that it has failed when instead it's just waiting.</span></span>  
  
 <span data-ttu-id="e0c2b-129">非同期メソッドを使用すると、アプリケーションは UI に応答し続けます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-129">When you use asynchronous methods, the application continues to respond to the UI.</span></span> <span data-ttu-id="e0c2b-130">たとえば、ウィンドウのサイズ変更や最小化を実行したり、アプリケーション処理の完了待たずに、アプリケーションを閉じたりできます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-130">You can resize or minimize a window, for example, or you can close the application if you don't want to wait for it to finish.</span></span>  
  
 <span data-ttu-id="e0c2b-131">非同期ベースの方法は、非同期操作を設計する場合に選択できるオプションの一覧に、自動送信に相当するものを追加します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-131">The async-based approach adds the equivalent of an automatic transmission to the list of options that you can choose from when designing asynchronous operations.</span></span> <span data-ttu-id="e0c2b-132">つまり、開発者の少しの作業量で、従来の非同期プログラミングのすべての利点を取得できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-132">That is, you get all the benefits of traditional asynchronous programming but with much less effort from the developer.</span></span>  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a><span data-ttu-id="e0c2b-133">非同期メソッドの作成の簡素化</span><span class="sxs-lookup"><span data-stu-id="e0c2b-133">Async methods are easier to write</span></span>  
 <span data-ttu-id="e0c2b-134">C# の [async](../../../../csharp/language-reference/keywords/async.md) キーワードと [await](../../../../csharp/language-reference/keywords/await.md) キーワードは、非同期プログラミングの中核です。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-134">The [async](../../../../csharp/language-reference/keywords/async.md) and [await](../../../../csharp/language-reference/keywords/await.md) keywords in C# are the heart of async programming.</span></span> <span data-ttu-id="e0c2b-135">これら 2 つのキーワードを使用すると、同期メソッドの作成とほぼ同様の容易さで、.NET Framework、.NET Core または Windows ランタイムのリソースを使用して非同期メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-135">By using those two keywords, you can use resources in the .NET Framework, .NET Core, or the Windows Runtime to create an asynchronous method almost as easily as you create a synchronous method.</span></span> <span data-ttu-id="e0c2b-136">`async` キーワードを使用して定義する非同期メソッドは、"*async メソッド*" として参照されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-136">Asynchronous methods that you define by using the `async` keyword are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="e0c2b-137">async メソッドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-137">The following example shows an async method.</span></span> <span data-ttu-id="e0c2b-138">コードのほとんどは、見たことのあるものと思います。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-138">Almost everything in the code should look completely familiar to you.</span></span> <span data-ttu-id="e0c2b-139">コメントは、非同期性を作成するために追加した機能を明示しています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-139">The comments call out the features that you add to create the asynchrony.</span></span>  
  
 <span data-ttu-id="e0c2b-140">このトピックの最後に完全な Windows Presentation Foundation (WPF) サンプル ファイルがあります。また、「[Async Sample: Example from "Asynchronous Programming with Async and Await" (非同期のサンプル: 「Async および Await を使用した非同期プログラミング」の例)](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c)」からサンプルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-140">You can find a complete Windows Presentation Foundation (WPF) example file at the end of this topic, and you can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).</span></span>  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
    // You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork();  
  
    // The await operator suspends AccessTheWebAsync.  
    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    //  - Control resumes here when getStringTask is complete.   
    //  - The await operator then retrieves the string result from getStringTask.  
    string urlContents = await getStringTask;  
  
    // The return statement specifies an integer result.  
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="e0c2b-141">`AccessTheWebAsync` に `GetStringAsync` を呼び出してその完了を待機する間で実行できる作業がない場合、次の 1 つのステートメントで呼び出しと待機をするようにコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-141">If `AccessTheWebAsync` doesn't have any work that it can do between calling `GetStringAsync` and awaiting its completion, you can simplify your code by calling and awaiting in the following single statement.</span></span>  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
<span data-ttu-id="e0c2b-142">次の特徴は、前の例を非同期のメソッドにするための概略です。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-142">The following characteristics summarize what makes the previous example an async method.</span></span>  
  
-   <span data-ttu-id="e0c2b-143">メソッド シグネチャは `async` 修飾子を含みます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-143">The method signature includes an `async` modifier.</span></span>  
  
-   <span data-ttu-id="e0c2b-144">非同期メソッドの名前は、慣例により「Async」というサフィックスで終わります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-144">The name of an async method, by convention, ends with an "Async" suffix.</span></span>  
  
-   <span data-ttu-id="e0c2b-145">戻り値の型は次のいずれかになります:</span><span class="sxs-lookup"><span data-stu-id="e0c2b-145">The return type is one of the following types:</span></span>  
  
    -   <span data-ttu-id="e0c2b-146">メソッドが、オペランドに `TResult` 型を持つステートメントを戻す場合、<xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-146"><xref:System.Threading.Tasks.Task%601> if your method has a return statement in which the operand has type `TResult`.</span></span>  
  
    -   <span data-ttu-id="e0c2b-147">メソッドがステートメントを戻さない、またはオペランドを持たないステートメントを戻す場合、<xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-147"><xref:System.Threading.Tasks.Task> if your method has no return statement or has a return statement with no operand.</span></span>  
  
    -   <span data-ttu-id="e0c2b-148">非同期のイベント ハンドラーを作成する場合、`void`。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-148">`void` if you're writing an async event handler.</span></span>  

    -   <span data-ttu-id="e0c2b-149">`GetAwaiter` メソッドがあるその他の任意の型 (C# 7.0 以降)。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-149">Any other type that has a `GetAwaiter` method (starting with C# 7.0).</span></span>
  
     <span data-ttu-id="e0c2b-150">詳細については、「[戻り値の型およびパラメーター](#BKMK_ReturnTypesandParameters)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-150">For more information, see the [Return Types and Parameters](#BKMK_ReturnTypesandParameters) section.</span></span>  
  
-   <span data-ttu-id="e0c2b-151">メソッドには、通常は 1 つ以上の await 式があり、待機中の非同期操作が完了するまでメソッドを続行できないポイントをマークします。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-151">The method usually includes at least one await expression, which marks a point where the method can't continue until the awaited asynchronous operation is complete.</span></span> <span data-ttu-id="e0c2b-152">この間メソッドは中断し、メソッドの呼び出し元にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-152">In the meantime, the method is suspended, and control returns to the method's caller.</span></span> <span data-ttu-id="e0c2b-153">このトピックの次のセクションでは、中断ポイントで何が発生するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-153">The next section of this topic illustrates what happens at the suspension point.</span></span>  
  
 <span data-ttu-id="e0c2b-154">非同期のメソッドでは、指定のキーワードと型を使用して何を実行するかを示すと、コンパイラがその作業を引き継ぎます。作業には、中断されたメソッドの待機ポイントにコントロールが戻された場合に実行される作業を、継続的に追跡することも含まれます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-154">In async methods, you use the provided keywords and types to indicate what you want to do, and the compiler does the rest, including keeping track of what must happen when control returns to an await point in a suspended method.</span></span> <span data-ttu-id="e0c2b-155">ループおよび例外処理など一部のルーチンのプロセスは、従来の非同期コードによる操作が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-155">Some routine processes, such as loops and exception handling, can be difficult to handle in traditional asynchronous code.</span></span> <span data-ttu-id="e0c2b-156">非同期のメソッドでは、同期ソリューションの場合と同様にこれらの要素を記述すると、問題が解決します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-156">In an async method, you write these elements much as you would in a synchronous solution, and the problem is solved.</span></span>  
  
 <span data-ttu-id="e0c2b-157">.NET Framework の以前のバージョンでの非同期性の詳細については、「[TPL と従来の .NET Framework 非同期プログラミング](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-157">For more information about asynchrony in previous versions of the .NET Framework, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).</span></span>  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a><span data-ttu-id="e0c2b-158">非同期メソッドでの動作</span><span class="sxs-lookup"><span data-stu-id="e0c2b-158">What happens in an async method</span></span>  
 <span data-ttu-id="e0c2b-159">非同期プログラミングでは理解が必要な最も重要なことは、コントロール フローがどのようにメソッドからのメソッドに移動するかということです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-159">The most important thing to understand in asynchronous programming is how the control flow moves from method to method.</span></span> <span data-ttu-id="e0c2b-160">次の図は、このプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-160">The following diagram leads you through the process.</span></span>  
  
 <span data-ttu-id="e0c2b-161">![非同期プログラムのトレース](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span><span class="sxs-lookup"><span data-stu-id="e0c2b-161">![Trace an async program](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span></span>  
  
 <span data-ttu-id="e0c2b-162">図内の数字は、次の手順の番号に対応しています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-162">The numbers in the diagram correspond to the following steps.</span></span>  
  
1.  <span data-ttu-id="e0c2b-163">イベント ハンドラーは `AccessTheWebAsync` 非同期のメソッドを呼び出して待機します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-163">An event handler calls and awaits the  `AccessTheWebAsync` async method.</span></span>  
  
2.  <span data-ttu-id="e0c2b-164">`AccessTheWebAsync` は <xref:System.Net.Http.HttpClient> インスタンスを作成し、文字列として Web サイトのコンテンツをダウンロードする <xref:System.Net.Http.HttpClient.GetStringAsync%2A> 非同期メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-164">`AccessTheWebAsync` creates an <xref:System.Net.Http.HttpClient> instance and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronous method to download the contents of a website as a string.</span></span>  
  
3.  <span data-ttu-id="e0c2b-165">`GetStringAsync` に何かが発生するとプロセスが中断します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-165">Something happens in `GetStringAsync` that suspends its progress.</span></span> <span data-ttu-id="e0c2b-166">Web サイトからのダウンロード処理、または他のブロックしているアクティビティを待機する必要が考えられます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-166">Perhaps it must wait for a website to download or some other blocking activity.</span></span> <span data-ttu-id="e0c2b-167">リソースのブロックを回避するために、`GetStringAsync` は呼び出し元の `AccessTheWebAsync` にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-167">To avoid blocking resources, `GetStringAsync` yields control to its caller, `AccessTheWebAsync`.</span></span>  
  
     <span data-ttu-id="e0c2b-168">`GetStringAsync` は `TResult` が文字列である <xref:System.Threading.Tasks.Task%601> を返し、`AccessTheWebAsync` は `getStringTask` 変数にタスクを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-168">`GetStringAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is a string, and `AccessTheWebAsync` assigns the task to the `getStringTask` variable.</span></span> <span data-ttu-id="e0c2b-169">タスクには `GetStringAsync` への呼び出しの進行中のプロセスを表し、作業が完了すると実際の文字列値を生成するコミットメントがあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-169">The task represents the ongoing process for the call to `GetStringAsync`, with a commitment to produce an actual string value when the work is complete.</span></span>  
  
4.  <span data-ttu-id="e0c2b-170">`getStringTask` が待機しないため、`AccessTheWebAsync` は `GetStringAsync` からの最終結果に依存しない他の作業を続行できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-170">Because `getStringTask` hasn't been awaited yet, `AccessTheWebAsync` can continue with other work that doesn't depend on the final result from `GetStringAsync`.</span></span> <span data-ttu-id="e0c2b-171">この作業は同期メソッド `DoIndependentWork` への呼び出しによって表されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-171">That work is represented by a call to the synchronous method `DoIndependentWork`.</span></span>  
  
5.  <span data-ttu-id="e0c2b-172">`DoIndependentWork` は、作業を実行し、呼び出し元に戻る同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-172">`DoIndependentWork` is a synchronous method that does its work and returns to its caller.</span></span>  
  
6.  <span data-ttu-id="e0c2b-173">`AccessTheWebAsync` は `getStringTask` からの結果なしで実行できる作業を使い果たしました。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-173">`AccessTheWebAsync` has run out of work that it can do without a result from `getStringTask`.</span></span> <span data-ttu-id="e0c2b-174">`AccessTheWebAsync` は次に、ダウンロードする文字列の長さを計算しますが、メソッドに文字列が戻されるまで、メソッドはその値を計算できません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-174">`AccessTheWebAsync` next wants to calculate and return the length of the downloaded string, but the method can't calculate that value until the method has the string.</span></span>  
  
     <span data-ttu-id="e0c2b-175">そのため、`AccessTheWebAsync` は await 演算子を使用してその進行を中断し、`AccessTheWebAsync` を呼び出したメソッドにコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-175">Therefore, `AccessTheWebAsync` uses an await operator to suspend its progress and to yield control to the method that called `AccessTheWebAsync`.</span></span> <span data-ttu-id="e0c2b-176">`AccessTheWebAsync` は呼び出し元に `Task<int>` を返します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-176">`AccessTheWebAsync` returns a `Task<int>` to the caller.</span></span> <span data-ttu-id="e0c2b-177">タスクは、ダウンロードされた文字列の長さの整数値を生成することの保証を表します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-177">The task represents a promise to produce an integer result that's the length of the downloaded string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0c2b-178">`GetStringAsync` (および、結果として `getStringTask`) が `AccessTheWebAsync` が待機する前に完了した場合、コントロールは `AccessTheWebAsync` に残ります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-178">If `GetStringAsync` (and therefore `getStringTask`) is complete before `AccessTheWebAsync` awaits it, control remains in `AccessTheWebAsync`.</span></span> <span data-ttu-id="e0c2b-179">`AccessTheWebAsync` を中断して後から戻ることは、呼び出された非同期プロセス (`getStringTask`) が既に完了していて、`AccessTheWebSync` が最終結果を待つ必要がない場合に、無駄になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-179">The expense of suspending and then returning to `AccessTheWebAsync` would be wasted if the called asynchronous process (`getStringTask`) has already completed and `AccessTheWebSync` doesn't have to wait for the final result.</span></span>  
  
     <span data-ttu-id="e0c2b-180">呼び出し元 (この例ではイベント ハンドラー) の内部で、処理パターンが続行されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-180">Inside the caller (the event handler in this example), the processing pattern continues.</span></span> <span data-ttu-id="e0c2b-181">呼び出し元は `AccessTheWebAsync` からの結果に依存しない他の作業をすることもあり、または直ちに待機状態になることもあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-181">The caller might do other work that doesn't depend on the result from `AccessTheWebAsync` before awaiting that result, or the caller might await immediately.</span></span>   <span data-ttu-id="e0c2b-182">イベント ハンドラーは `AccessTheWebAsync` を待機し、`AccessTheWebAsync` は、`GetStringAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-182">The event handler is waiting for `AccessTheWebAsync`, and `AccessTheWebAsync` is waiting for `GetStringAsync`.</span></span>  
  
7.  <span data-ttu-id="e0c2b-183">`GetStringAsync` が完了し、文字列の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-183">`GetStringAsync` completes and produces a string result.</span></span> <span data-ttu-id="e0c2b-184">文字列の結果は、`GetStringAsync` への呼び出しによって、意図した形式では戻されません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-184">The string result isn't returned by the call to `GetStringAsync` in the way that you might expect.</span></span> <span data-ttu-id="e0c2b-185">(メソッドは既に手順 3 のタスクで戻されていることに注意してください)。代わりに、文字列の結果は、`getStringTask` メソッドの完了を表すタスク内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-185">(Remember that the method already returned a task in step 3.) Instead, the string result is stored in the task that represents the completion of the method, `getStringTask`.</span></span> <span data-ttu-id="e0c2b-186">await 演算子は、`getStringTask` から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-186">The await operator retrieves the result from `getStringTask`.</span></span> <span data-ttu-id="e0c2b-187">代入ステートメントは `urlContents` に取得された結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-187">The assignment statement assigns the retrieved result to `urlContents`.</span></span>  
  
8.  <span data-ttu-id="e0c2b-188">`AccessTheWebAsync` に文字列の結果がある場合、メソッドは文字列の長さを計算できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-188">When `AccessTheWebAsync` has the string result, the method can calculate the length of the string.</span></span> <span data-ttu-id="e0c2b-189">次に `AccessTheWebAsync` の作業も完了し、待機しているイベント ハンドラーが再開できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-189">Then the work of `AccessTheWebAsync` is also complete, and the waiting event handler can resume.</span></span> <span data-ttu-id="e0c2b-190">トピックの最後にある完全なサンプルでは、イベント ハンドラーが長さの結果の値を取得して印刷することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-190">In the full example at the end of the topic, you can confirm that the event handler retrieves and prints the value of the length result.</span></span>    
<span data-ttu-id="e0c2b-191">非同期プログラミングの経験がない場合、同期および非同期の動作の違いを、少し時間を割いて考慮してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-191">If you are new to asynchronous programming, take a minute to consider the difference between synchronous and asynchronous behavior.</span></span> <span data-ttu-id="e0c2b-192">同期メソッドは作業が完了すると戻されます (手順 5.) が、非同期のメソッドは、作業が中断されるとタスクの値を戻します。(手順 3. および 6.)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-192">A synchronous method returns when its work is complete (step 5), but an async method returns a task value when its work is suspended (steps 3 and 6).</span></span> <span data-ttu-id="e0c2b-193">非同期のメソッドが最終的に作業を完了すると、タスクは完了とマークされ、結果が存在する場合はタスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-193">When the async method eventually completes its work, the task is marked as completed and the result, if any, is stored in the task.</span></span>  
  
<span data-ttu-id="e0c2b-194">制御フローの詳細については、「[非同期プログラムにおける制御フロー (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-194">For more information about control flow, see [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
##  <a name="BKMK_APIAsyncMethods"></a> <span data-ttu-id="e0c2b-195">API の非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="e0c2b-195">API async methods</span></span>  
 <span data-ttu-id="e0c2b-196">非同期のプログラミングをサポートする `GetStringAsync` などのメソッドがどこにあるのかということです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-196">You might be wondering where to find methods such as `GetStringAsync` that support async programming.</span></span> <span data-ttu-id="e0c2b-197">.NET Framework 4.5 以降および .NET Core には、`async` および `await` で使用する多くのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-197">The  .NET Framework 4.5 or higher and .NET Core contain many members that work with `async` and `await`.</span></span> <span data-ttu-id="e0c2b-198">メンバー名に付記されている "Async" というサフィックスと、その戻り値の型である <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> から識別できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-198">You can recognize them by the "Async" suffix that’s appended to the member name, and by their return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e0c2b-199">たとえば、`System.IO.Stream` のクラスには、同期メソッドの <xref:System.IO.Stream.CopyTo%2A>、<xref:System.IO.Stream.Read%2A>、および <xref:System.IO.Stream.Write%2A> と共に、<xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> および <xref:System.IO.Stream.WriteAsync%2A> という同期メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-199">For example, the `System.IO.Stream` class contains methods such as <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> alongside the synchronous methods <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, and <xref:System.IO.Stream.Write%2A>.</span></span>  
  
 <span data-ttu-id="e0c2b-200">Windows ランタイムにも、Windows アプリの `async` と `await` で使用できる多くのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-200">The Windows Runtime also contains many methods that you can use with `async` and `await` in Windows apps.</span></span> <span data-ttu-id="e0c2b-201">UWP 開発の詳細については、「[スレッド化と非同期プログラミング](/windows/uwp/threading-async/)」を参照してください。旧バージョンの Windows ランタイムを使用する場合は、「[Asynchronous programming (Windows Store apps)](/previous-versions/windows/apps/hh464924(v=win.10))」 (非同期プログラミング (Windows ストア アプリ)) および「[Quickstart: Calling asynchronous APIs in C# or Visual Basic](/previous-versions/windows/apps/hh452713(v=win.10))」(クイック スタート: C# または Visual Basic での非同期 API の呼び出し) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-201">For more information, see [Threading and async programming](/windows/uwp/threading-async/) for UWP development, and [Asynchronous programming (Windows Store apps)](/previous-versions/windows/apps/hh464924(v=win.10)) and [Quickstart: Calling asynchronous APIs in C# or Visual Basic](/previous-versions/windows/apps/hh452713(v=win.10)) if you use earlier versions of the Windows Runtime.</span></span>  
  
##  <a name="BKMK_Threads"></a><span data-ttu-id="e0c2b-202">スレッド</span><span class="sxs-lookup"><span data-stu-id="e0c2b-202">Threads</span></span>  
<span data-ttu-id="e0c2b-203">非同期のメソッドは非ブロッキング操作を意図しています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-203">Async methods are intended to be non-blocking operations.</span></span> <span data-ttu-id="e0c2b-204">非同期のメソッドの `await` 式は、待機中のタスクの実行中に現在のスレッドをブロックしません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-204">An `await` expression in an async method doesn’t block the current thread while the awaited task is running.</span></span> <span data-ttu-id="e0c2b-205">代わりに、式はメソッドの残りの部分の継続を登録し、非同期のメソッドの呼び出し元にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-205">Instead, the expression signs up the rest of the method as a continuation and returns control to the caller of the async method.</span></span>  
  
<span data-ttu-id="e0c2b-206">`async` および `await` キーワードは、追加のスレッドを作成する要因にはなりません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-206">The `async` and `await` keywords don't cause additional threads to be created.</span></span> <span data-ttu-id="e0c2b-207">非同期のメソッドは自分自身のスレッドで実行しないため、マルチスレッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-207">Async methods don't require multithreading because an async method doesn't run on its own thread.</span></span> <span data-ttu-id="e0c2b-208">メソッドは、現在の同期コンテキストで実行し、メソッドがアクティブな場合に限りスレッドの時間を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-208">The method runs on the current synchronization context and uses time on the thread only when the method is active.</span></span> <span data-ttu-id="e0c2b-209"><xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> を使用して、CPU バインディングの作業をバックグラウンド スレッドに移動できますが、バックグラウンド スレッドは、結果を待つだけのプロセスを援助しません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-209">You can use <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> to move CPU-bound work to a background thread, but a background thread doesn't help with a process that's just waiting for results to become available.</span></span>  
  
<span data-ttu-id="e0c2b-210">非同期プログラミングへの非同期ベースのアプローチは、ほぼすべてのケースの既存のアプローチに推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-210">The async-based approach to asynchronous programming is preferable to existing approaches in almost every case.</span></span> <span data-ttu-id="e0c2b-211">特に、このアプローチはコードがシンプルで競合状態からの保護の必要がないため、I/O バウンドの操作では、<xref:System.ComponentModel.BackgroundWorker> クラスよりも優れています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-211">In particular, this approach is better than the <xref:System.ComponentModel.BackgroundWorker> class for I/O-bound operations because the code is simpler and you don't have to guard against race conditions.</span></span> <span data-ttu-id="e0c2b-212"><xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> メソッドと組み合わせると、非同期のプログラミングは CPU バインディングの操作に関して <xref:System.ComponentModel.BackgroundWorker> よりも優れています。非同期のプログラミングは、`Task.Run` がスレッド プールから移動する作業から、実行するコードの調整の詳細を分離するためです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-212">In combination with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method, async programming is better than <xref:System.ComponentModel.BackgroundWorker> for CPU-bound operations because async programming separates the coordination details of running your code from the work that `Task.Run` transfers to the threadpool.</span></span>  
  
##  <a name="BKMK_AsyncandAwait"></a><span data-ttu-id="e0c2b-213">async と await</span><span class="sxs-lookup"><span data-stu-id="e0c2b-213">async and await</span></span>  
 <span data-ttu-id="e0c2b-214">[async](../../../../csharp/language-reference/keywords/async.md) 修飾子を使用して、メソッドが非同期メソッドであることを指定すると、次の 2 つの機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-214">If you specify that a method is an async method by using the [async](../../../../csharp/language-reference/keywords/async.md) modifier, you enable the following two capabilities.</span></span>  
  
-   <span data-ttu-id="e0c2b-215">マークされた非同期のメソッドは中断ポイントを示すために [await](../../../../csharp/language-reference/keywords/await.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-215">The marked async method can use [await](../../../../csharp/language-reference/keywords/await.md) to designate suspension points.</span></span> <span data-ttu-id="e0c2b-216">`await` 演算子は、非同期のメソッドが、待機中の非同期のプロセスが完了するまでこのポイント以降を続行できないことを、コンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-216">The `await` operator tells the compiler that the async method can't continue past that point until the awaited asynchronous process is complete.</span></span> <span data-ttu-id="e0c2b-217">その間、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-217">In the meantime, control returns to the caller of the async method.</span></span>  
  
     <span data-ttu-id="e0c2b-218">非同期のメソッドの `await` 式での中断は、メソッドからの終了を意図するものではなく、`finally` ブロックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-218">The suspension of an async method at an `await` expression doesn't constitute an exit from the method, and `finally` blocks don’t run.</span></span>  
  
-   <span data-ttu-id="e0c2b-219">マークされた非同期のメソッド自体は、呼び出し元のメソッドによって待機できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-219">The marked async method can itself be awaited by methods that call it.</span></span>  
  
<span data-ttu-id="e0c2b-220">非同期のメソッドには、通常の `await` 演算子が 1 つ以上ありますが、`await` 式がない場合もコンパイラ エラーの原因にはなりません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-220">An async method typically contains one or more occurrences of an `await` operator, but the absence of `await` expressions doesn’t cause a compiler error.</span></span> <span data-ttu-id="e0c2b-221">中断ポイントをマークするために非同期のメソッドが `await` 演算子を使用しない場合、`async` 修飾子が存在しても、メソッドは同期メソッドと同様に実行されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-221">If an async method doesn’t use an `await` operator to mark a suspension point, the method executes as a synchronous method does, despite the `async` modifier.</span></span> <span data-ttu-id="e0c2b-222">このようなメソッドには、コンパイラが警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-222">The compiler issues a warning for such methods.</span></span>  
  
 <span data-ttu-id="e0c2b-223">`async` と `await` は、コンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-223">`async` and `await` are contextual keywords.</span></span> <span data-ttu-id="e0c2b-224">詳細およびサンプルについては、次のトピックを参照してください:</span><span class="sxs-lookup"><span data-stu-id="e0c2b-224">For more information and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e0c2b-225">async</span><span class="sxs-lookup"><span data-stu-id="e0c2b-225">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
  
-   [<span data-ttu-id="e0c2b-226">await</span><span class="sxs-lookup"><span data-stu-id="e0c2b-226">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a><span data-ttu-id="e0c2b-227">戻り値の型およびパラメーター</span><span class="sxs-lookup"><span data-stu-id="e0c2b-227">Return types and parameters</span></span>  
<span data-ttu-id="e0c2b-228">非同期メソッドは、通常 <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-228">An async method typically returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="e0c2b-229">非同期のメソッド内で、`await` 演算子は、他の非同期のメソッドへの呼び出しから戻されたタスクに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-229">Inside an async method, an `await` operator is applied to a task that's returned from a call to another async method.</span></span>  
  
<span data-ttu-id="e0c2b-230">メソッドが、`TResult` 型のオペランドを指定する [Return](../../../../csharp/language-reference/keywords/return.md) ステートメントを含む場合、<xref:System.Threading.Tasks.Task%601> を戻り値の型として指定します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-230">You specify <xref:System.Threading.Tasks.Task%601> as the return type if the method contains a [return](../../../../csharp/language-reference/keywords/return.md) statement that specifies an operand of type `TResult`.</span></span> 
  
<span data-ttu-id="e0c2b-231">メソッドに Return ステートメントがない場合、または Return ステートメントがオペランドを戻さない場合、<xref:System.Threading.Tasks.Task> を戻り値の型として使用します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-231">You use <xref:System.Threading.Tasks.Task>  as the return type if the method has no return statement or has a return statement that doesn't return an operand.</span></span>  

<span data-ttu-id="e0c2b-232">C# 7.0 以降では、その型に `GetAwaiter` メソッドがある場合に限り、別の戻り値の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-232">Starting with C# 7.0, you can also specify any other return type, provided that that type includes a `GetAwaiter` method.</span></span> <span data-ttu-id="e0c2b-233">このような型の例として、<xref:System.Threading.Tasks.ValueTask%601> が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-233"><xref:System.Threading.Tasks.ValueTask%601> is an example of such a type.</span></span> <span data-ttu-id="e0c2b-234">これは、[System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet パッケージにあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-234">It is available in the [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet package.</span></span>
  
 <span data-ttu-id="e0c2b-235">次のサンプルは、<xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task> を戻すメソッドを宣言し、呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-235">The following example shows how you declare and call a method that returns a <xref:System.Threading.Tasks.Task%601> or a <xref:System.Threading.Tasks.Task>.</span></span>  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
```  
  
<span data-ttu-id="e0c2b-236">それぞれ、進行中の作業を示すタスクを戻します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-236">Each returned task represents ongoing work.</span></span> <span data-ttu-id="e0c2b-237">タスクに非同期処理の状態に関する情報、および最終的にはプロセスからの最終結果、またはプロセスが成功しなかった場合に発生する例外をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-237">A task encapsulates information about the state of the asynchronous process and, eventually, either the final result from the process or the exception that the process raises if it doesn't succeed.</span></span>  
  
<span data-ttu-id="e0c2b-238">非同期のメソッドの戻り値の型としては、`void` を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-238">An async method can also have a `void` return type.</span></span> <span data-ttu-id="e0c2b-239">この戻り値の型は主として、`void` の戻り値の型が必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-239">This return type is used primarily to define event handlers, where a `void` return type is required.</span></span> <span data-ttu-id="e0c2b-240">非同期のイベント ハンドラーは通常、非同期のプログラムの開始点として機能します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-240">Async event handlers often serve as the starting point for async programs.</span></span>  
  
<span data-ttu-id="e0c2b-241">`void` の戻り値の型を持つ非同期のメソッドは、待機できません。void を戻すメソッドの呼び出し元は、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-241">An async method that has a `void` return type can’t be awaited, and the caller of a void-returning method can't catch any exceptions that the method throws.</span></span>  
  
<span data-ttu-id="e0c2b-242">非同期のメソッドで [in](../../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../../csharp/language-reference/keywords/ref.md)、または [out](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターを宣言することはできませんが、これらのパラメーターを持つメソッドを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-242">An async method can't declare [in](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) or [out](../../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, but the method can call methods that have such parameters.</span></span> <span data-ttu-id="e0c2b-243">同様に、非同期メソッドは ref 戻り値を使用してメソッドを呼び出すことはできますが、参照を使用して値を返すことはできません。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-243">Similarly, an async method can't return a value by reference, although it can call methods with ref return values.</span></span> 
  
<span data-ttu-id="e0c2b-244">使用例を含む詳細については、「[非同期の戻り値の型 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-244">For more information and examples, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span> <span data-ttu-id="e0c2b-245">非同期のメソッドで例外をキャッチする方法の詳細については、「[try-catch](../../../../csharp/language-reference/keywords/try-catch.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-245">For more information about how to catch exceptions in async methods, see [try-catch](../../../../csharp/language-reference/keywords/try-catch.md).</span></span> 
  
<span data-ttu-id="e0c2b-246">Windows ランタイム プログラミングの非同期 API には、タスクに類似した次のような戻り値の型の 1 つがあります。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-246">Asynchronous APIs in Windows Runtime programming have one of the following return types, which are similar to tasks:</span></span>  
  
-   <span data-ttu-id="e0c2b-247"><xref:Windows.Foundation.IAsyncOperation%601> は <xref:System.Threading.Tasks.Task%601> に対応します</span><span class="sxs-lookup"><span data-stu-id="e0c2b-247"><xref:Windows.Foundation.IAsyncOperation%601>, which corresponds to <xref:System.Threading.Tasks.Task%601></span></span>  
  
-   <span data-ttu-id="e0c2b-248"><xref:Windows.Foundation.IAsyncAction> は <xref:System.Threading.Tasks.Task> に対応します</span><span class="sxs-lookup"><span data-stu-id="e0c2b-248"><xref:Windows.Foundation.IAsyncAction>, which corresponds to <xref:System.Threading.Tasks.Task></span></span>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a><span data-ttu-id="e0c2b-249">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="e0c2b-249">Naming convention</span></span>  
 <span data-ttu-id="e0c2b-250">慣例により、`async` 修飾子を持つメソッドの名前には、"Async" を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-250">By convention, you append "Async" to the names of methods that have an `async` modifier.</span></span>  
  
 <span data-ttu-id="e0c2b-251">イベント、基底クラス、またはインターフェイスのコントラクトが別の名前を表示している場合は、この慣例を無視できます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-251">You can ignore the convention where an event, base class, or interface contract suggests a different name.</span></span> <span data-ttu-id="e0c2b-252">たとえば、`Button1_Click` などの共通のイベント ハンドラーの名前は、変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-252">For example, you shouldn’t rename common event handlers, such as `Button1_Click`.</span></span>  
  
##  <a name="BKMK_RelatedTopics"></a><span data-ttu-id="e0c2b-253">関連トピックとサンプル (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-253">Related topics and samples (Visual Studio)</span></span>  
  
|<span data-ttu-id="e0c2b-254">Title</span><span class="sxs-lookup"><span data-stu-id="e0c2b-254">Title</span></span>|<span data-ttu-id="e0c2b-255">説明</span><span class="sxs-lookup"><span data-stu-id="e0c2b-255">Description</span></span>|<span data-ttu-id="e0c2b-256">サンプル</span><span class="sxs-lookup"><span data-stu-id="e0c2b-256">Sample</span></span>|  
|-----------|-----------------|------------|  
|[<span data-ttu-id="e0c2b-257">チュートリアル: async と await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-257">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|<span data-ttu-id="e0c2b-258">同期 WPF のソリューションを非同期 WPF のソリューションに変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-258">Shows how to convert a synchronous WPF solution to an asynchronous WPF solution.</span></span> <span data-ttu-id="e0c2b-259">アプリケーションは、一連の Web サイトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-259">The application downloads a series of websites.</span></span>|[<span data-ttu-id="e0c2b-260">Async Sample: Accessing the Web Walkthrough (非同期のサンプル: Web サイトへのアクセスのチュートリアル)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-260">Async Sample: Accessing the Web Walkthrough</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[<span data-ttu-id="e0c2b-261">方法: Task.WhenAll を使用して AsyncWalkthrough を拡張する (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-261">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|<span data-ttu-id="e0c2b-262">前のチュートリアルに <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> を追加します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-262">Adds <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> to the previous walkthrough.</span></span> <span data-ttu-id="e0c2b-263">`WhenAll` を使用すると、すべてのダウンロードが同時に開始します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-263">The use of `WhenAll` starts all the downloads at the same time.</span></span>||  
|[<span data-ttu-id="e0c2b-264">方法: async と await を使用して複数の Web 要求を並列実行する</span><span class="sxs-lookup"><span data-stu-id="e0c2b-264">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|<span data-ttu-id="e0c2b-265">複数のタスクを同時に開始する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-265">Demonstrates how to start several tasks at the same time.</span></span>|[<span data-ttu-id="e0c2b-266">Async Sample: Make Multiple Web Requests in Parallel (非同期のサンプル: 複数の並行 Web 要求の作成)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-266">Async Sample: Make Multiple Web Requests in Parallel</span></span>](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[<span data-ttu-id="e0c2b-267">非同期の戻り値の型 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-267">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|<span data-ttu-id="e0c2b-268">非同期のメソッドが戻す型、および各型の適切な使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-268">Illustrates the types that async methods can return and explains when each type is appropriate.</span></span>||  
|[<span data-ttu-id="e0c2b-269">非同期プログラムにおける制御フロー (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-269">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|<span data-ttu-id="e0c2b-270">非同期プログラムでの await 式を継続して、コントロールのフローの詳細をトレースします。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-270">Traces in detail the flow of control through a succession of await expressions in an asynchronous program.</span></span>|[<span data-ttu-id="e0c2b-271">Async Sample: Control Flow in Async Programs (非同期のサンプル: 非同期プログラムにおける制御フロー)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-271">Async Sample: Control Flow in Async Programs</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[<span data-ttu-id="e0c2b-272">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-272">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|<span data-ttu-id="e0c2b-273">非同期のソリューションに次の機能を追加する方法を示します:</span><span class="sxs-lookup"><span data-stu-id="e0c2b-273">Shows how to add the following functionality to your async solution:</span></span><br /><br /> <span data-ttu-id="e0c2b-274">-   [非同期タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-274">-   [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span></span><br /><span data-ttu-id="e0c2b-275">-   [指定した時間の経過後の非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-275">-   [Cancel Async Tasks after a Period of Time (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span></span><br /><span data-ttu-id="e0c2b-276">-   [完了後の残りの非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-276">-   [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span></span><br /><span data-ttu-id="e0c2b-277">-   [完了時での複数の非同期タスクとプロセスの実行 (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-277">-   [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span></span>|[<span data-ttu-id="e0c2b-278">Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-278">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[<span data-ttu-id="e0c2b-279">非同期アプリにおける再入の処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-279">Handling Reentrancy in Async Apps (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|<span data-ttu-id="e0c2b-280">実行中にアクティブな非同期操作を再起動するケースの処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-280">Shows how to handle cases in which an active asynchronous operation is restarted while it’s running.</span></span>||  
|<span data-ttu-id="e0c2b-281">[WhenAny: .NET Framework と Windows ランタイム間のブリッジ](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-281">[WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span></span>|<span data-ttu-id="e0c2b-282">[!INCLUDE[wrt](~/includes/wrt-md.md)] のメソッドの <xref:System.Threading.Tasks.Task.WhenAny%2A> を使用可能にするために、[!INCLUDE[wrt](~/includes/wrt-md.md)] で、.NET Framework および IAsyncOperations のタスクの種類間をブリッジする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-282">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.Tasks.Task.WhenAny%2A> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="e0c2b-283">Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny) (非同期のサンプル: .NET と Windows ランタイム間のブリッジ (AsTask と WhenAny))</span><span class="sxs-lookup"><span data-stu-id="e0c2b-283">Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|<span data-ttu-id="e0c2b-284">非同期のキャンセル: .NET Framework と Windows ランタイム間のブリッジ</span><span class="sxs-lookup"><span data-stu-id="e0c2b-284">Async Cancellation: Bridging between the .NET Framework and the Windows Runtime</span></span>|<span data-ttu-id="e0c2b-285">[!INCLUDE[wrt](~/includes/wrt-md.md)] のメソッドの <xref:System.Threading.CancellationTokenSource> を使用可能にするために、[!INCLUDE[wrt](~/includes/wrt-md.md)] で、.NET Framework および IAsyncOperations のタスクの種類間をブリッジする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-285">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.CancellationTokenSource> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="e0c2b-286">Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation) (非同期のサンプル: .NET と Windows ランタイム間のブリッジ (AsTask と Cancellation))</span><span class="sxs-lookup"><span data-stu-id="e0c2b-286">Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[<span data-ttu-id="e0c2b-287">ファイル アクセスにおける非同期の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-287">Using Async for File Access (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|<span data-ttu-id="e0c2b-288">async および await を使用してファイルにアクセスすることの利点の一覧と紹介です。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-288">Lists and demonstrates the benefits of using async and await to access files.</span></span>||  
|[<span data-ttu-id="e0c2b-289">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="e0c2b-289">Task-based Asynchronous Pattern (TAP)</span></span>](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|<span data-ttu-id="e0c2b-290">.NET Framework での非同期性の新しいパターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-290">Describes a new pattern for asynchrony in the .NET Framework.</span></span> <span data-ttu-id="e0c2b-291">パターンは <xref:System.Threading.Tasks.Task> および <xref:System.Threading.Tasks.Task%601> の型に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-291">The pattern is based on the <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> types.</span></span>||  
|[<span data-ttu-id="e0c2b-292">Channel 9 の非同期に関するビデオ</span><span class="sxs-lookup"><span data-stu-id="e0c2b-292">Async Videos on Channel 9</span></span>](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|<span data-ttu-id="e0c2b-293">非同期のプログラミングに関するさまざまなビデオへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-293">Provides links to a variety of videos about async programming.</span></span>||  
  
##  <a name="BKMK_CompleteExample"></a> <span data-ttu-id="e0c2b-294">コード例全体</span><span class="sxs-lookup"><span data-stu-id="e0c2b-294">Complete example</span></span>  
 <span data-ttu-id="e0c2b-295">次のコードは、このトピックで説明する Windows Presentation Foundation (WPF) アプリケーションの MainWindow.xaml.cs ファイルです。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-295">The following code is the MainWindow.xaml.cs file from the Windows Presentation Foundation (WPF) application that this topic discusses.</span></span> <span data-ttu-id="e0c2b-296">サンプルは、「[Async Sample: Example from "Asynchronous Programming with Async and Await" (非同期のサンプル: 「Async および Await を使用した非同期プログラミング」の例)](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e0c2b-296">You can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
            // You can do work here that doesn't rely on the string from GetStringAsync.  
            DoIndependentWork();  
  
            // The await operator suspends AccessTheWebAsync.  
            //  - AccessTheWebAsync can't continue until getStringTask is complete.  
            //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
            //  - Control resumes here when getStringTask is complete.   
            //  - The await operator then retrieves the string result from getStringTask.  
            string urlContents = await getStringTask;  
  
            // The return statement specifies an integer result.  
            // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
            return urlContents.Length;  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0c2b-297">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0c2b-297">See also</span></span>  
 [<span data-ttu-id="e0c2b-298">async</span><span class="sxs-lookup"><span data-stu-id="e0c2b-298">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="e0c2b-299">await</span><span class="sxs-lookup"><span data-stu-id="e0c2b-299">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="e0c2b-300">非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="e0c2b-300">Asynchronous programming</span></span>](../../../../csharp/async.md)  
 [<span data-ttu-id="e0c2b-301">非同期の概要</span><span class="sxs-lookup"><span data-stu-id="e0c2b-301">Async overview</span></span>](../../../../standard/async.md)  
