---
title: Async および Await を使用した非同期プログラミング (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd7e462b-583b-4395-9c36-45aa9e61072c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 18e3abb8d010d3766aa1b1239b3d22cc3cb9b47e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-programming-with-async-and-await-visual-basic"></a><span data-ttu-id="1e504-102">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-102">Asynchronous Programming with Async and Await (Visual Basic)</span></span>
<span data-ttu-id="1e504-103">パフォーマンスのボトルネックを回避しアプリケーション全体の応答性を向上させるために、非同期プログラミングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-103">You can avoid performance bottlenecks and enhance the overall responsiveness of your application by using asynchronous programming.</span></span> <span data-ttu-id="1e504-104">ただ、非同期アプリケーションを作成する従来の方法は複雑で、プログラムの作成、デバッグ、保守が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e504-104">However, traditional techniques for writing asynchronous applications can be complicated, making them difficult to write, debug, and maintain.</span></span>  
  
 <span data-ttu-id="1e504-105">Visual Studio 2012 では、.NET Framework 4.5 以降と Windows ランタイムの非同期サポートを利用した "非同期プログラミング" と呼ばれる簡単な方法が導入されました。</span><span class="sxs-lookup"><span data-stu-id="1e504-105">Visual Studio 2012 introduced a simplified approach, async programming, that leverages asynchronous support in the .NET Framework 4.5 and higher as well as  in the Windows Runtime.</span></span> <span data-ttu-id="1e504-106">コンパイラがこれまで開発者が行っていた難しい作業を実行し、アプリケーションは同期コードに類似した論理構造を保持します。</span><span class="sxs-lookup"><span data-stu-id="1e504-106">The compiler does the difficult work that the developer used to do, and your application retains a logical structure that resembles synchronous code.</span></span> <span data-ttu-id="1e504-107">その結果、わずかな作業量で非同期プログラミングのすべての利点を得られます。</span><span class="sxs-lookup"><span data-stu-id="1e504-107">As a result, you get all the advantages of asynchronous programming with a fraction of the effort.</span></span>  
  
 <span data-ttu-id="1e504-108">このトピックでは、非同期プログラミングをいつ、どのように使用するかの概要を紹介します。詳細と例を含むをサポート トピックへのリンクもあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-108">This topic provides an overview of when and how to use async programming and includes links to support topics that contain details and examples.</span></span>  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a><span data-ttu-id="1e504-109">非同期による応答性の改善</span><span class="sxs-lookup"><span data-stu-id="1e504-109">Async Improves Responsiveness</span></span>  
 <span data-ttu-id="1e504-110">アプリケーションが Web サイトにアクセスする場合など、ブロックする可能性がある操作には、非同期が必要となります。</span><span class="sxs-lookup"><span data-stu-id="1e504-110">Asynchrony is essential for activities that are potentially blocking, such as when your application accesses the web.</span></span> <span data-ttu-id="1e504-111">Web リソースへのアクセスには、遅延が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-111">Access to a web resource sometimes is slow or delayed.</span></span> <span data-ttu-id="1e504-112">このような操作が同期処理内でブロックされた場合、アプリケーション全体が待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e504-112">If such an activity is blocked within a synchronous process, the entire application must wait.</span></span> <span data-ttu-id="1e504-113">非同期処理では、ブロックする可能性のあるタスク終了するまで、アプリケーションは Web リソースに依存しない他の操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-113">In an asynchronous process, the application can continue with other work that doesn't depend on the web resource until the potentially blocking task finishes.</span></span>  
  
 <span data-ttu-id="1e504-114">非同期プログラミングによって応答性を向上する一般的な領域を、次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-114">The following table shows typical areas where asynchronous programming improves responsiveness.</span></span> <span data-ttu-id="1e504-115">.NET Framework 4.5 および Windows ランタイムの API の一覧には、非同期のプログラミングをサポートするメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e504-115">The listed APIs from the  .NET Framework 4.5 and the Windows Runtime contain methods that support async programming.</span></span>  
  
|<span data-ttu-id="1e504-116">アプリケーション領域</span><span class="sxs-lookup"><span data-stu-id="1e504-116">Application area</span></span>|<span data-ttu-id="1e504-117">サポートされている、非同期のメソッドを含む API</span><span class="sxs-lookup"><span data-stu-id="1e504-117">Supporting APIs that contain async methods</span></span>|  
|----------------------|------------------------------------------------|  
|<span data-ttu-id="1e504-118">Web アクセス</span><span class="sxs-lookup"><span data-stu-id="1e504-118">Web access</span></span>|<span data-ttu-id="1e504-119"><xref:System.Net.Http.HttpClient>, [SyndicationClient](http://go.microsoft.com/fwlink/p/?LinkId=259441)</span><span class="sxs-lookup"><span data-stu-id="1e504-119"><xref:System.Net.Http.HttpClient>, [SyndicationClient](http://go.microsoft.com/fwlink/p/?LinkId=259441)</span></span>|  
|<span data-ttu-id="1e504-120">ファイルの処理</span><span class="sxs-lookup"><span data-stu-id="1e504-120">Working with files</span></span>|<span data-ttu-id="1e504-121">[StorageFile](http://go.microsoft.com/fwlink/p/?LinkId=248220), <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="1e504-121">[StorageFile](http://go.microsoft.com/fwlink/p/?LinkId=248220), <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader></span></span>|  
|<span data-ttu-id="1e504-122">イメージの処理</span><span class="sxs-lookup"><span data-stu-id="1e504-122">Working with images</span></span>|<span data-ttu-id="1e504-123">[MediaCapture](http://go.microsoft.com/fwlink/p/?LinkId=261839)、[BitmapEncoder](http://go.microsoft.com/fwlink/p/?LinkId=261840)、[BitmapDecoder](http://go.microsoft.com/fwlink/p/?LinkId=261841)</span><span class="sxs-lookup"><span data-stu-id="1e504-123">[MediaCapture](http://go.microsoft.com/fwlink/p/?LinkId=261839), [BitmapEncoder](http://go.microsoft.com/fwlink/p/?LinkId=261840), [BitmapDecoder](http://go.microsoft.com/fwlink/p/?LinkId=261841)</span></span>|  
|<span data-ttu-id="1e504-124">WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="1e504-124">WCF programming</span></span>|[<span data-ttu-id="1e504-125">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="1e504-125">Synchronous and Asynchronous Operations</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=192382)|  
|||  
  
 <span data-ttu-id="1e504-126">非同期性は、UI スレッドにアクセスするアプリケーションに対して特に有効です。これは、すべての UI 関連のアクティビティが一般的に 1 つのスレッドを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="1e504-126">Asynchrony proves especially valuable for applications that access the UI thread because all UI-related activity usually shares one thread.</span></span> <span data-ttu-id="1e504-127">同期アプリケーションでは、1 つのプロセスがブロックされるとすべてがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="1e504-127">If any process is blocked in a synchronous application, all are blocked.</span></span> <span data-ttu-id="1e504-128">アプリケーションが応答を停止するため、待機状態であるとは考えずに失敗したと結論付けることもあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-128">Your application stops responding, and you might conclude that it has failed when instead it's just waiting.</span></span>  
  
 <span data-ttu-id="1e504-129">非同期メソッドを使用すると、アプリケーションは UI に応答し続けます。</span><span class="sxs-lookup"><span data-stu-id="1e504-129">When you use asynchronous methods, the application continues to respond to the UI.</span></span> <span data-ttu-id="1e504-130">たとえば、ウィンドウのサイズ変更や最小化を実行したり、アプリケーション処理の完了待たずに、アプリケーションを閉じたりできます。</span><span class="sxs-lookup"><span data-stu-id="1e504-130">You can resize or minimize a window, for example, or you can close the application if you don't want to wait for it to finish.</span></span>  
  
 <span data-ttu-id="1e504-131">非同期ベースの方法は、非同期操作を設計する場合に選択できるオプションの一覧に、自動送信に相当するものを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e504-131">The async-based approach adds the equivalent of an automatic transmission to the list of options that you can choose from when designing asynchronous operations.</span></span> <span data-ttu-id="1e504-132">つまり、開発者の少しの作業量で、従来の非同期プログラミングのすべての利点を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-132">That is, you get all the benefits of traditional asynchronous programming but with much less effort from the developer.</span></span>  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a><span data-ttu-id="1e504-133">非同期メソッドの作成の簡素化</span><span class="sxs-lookup"><span data-stu-id="1e504-133">Async Methods Are Easier to Write</span></span>  
 <span data-ttu-id="1e504-134">Visual Basic の [Async](../../../../visual-basic/language-reference/modifiers/async.md) キーワードと [Await](../../../../visual-basic/language-reference/modifiers/async.md) キーワードは、非同期プログラミングの中核です。</span><span class="sxs-lookup"><span data-stu-id="1e504-134">The [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await](../../../../visual-basic/language-reference/modifiers/async.md) keywords in Visual Basic are the heart of async programming.</span></span> <span data-ttu-id="1e504-135">これら 2 つのキーワードを使用すると、同期メソッドの作成とほぼ同様の容易さで、.NET Framework または Windows ランタイムのリソースを使用して非同期メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-135">By using those two keywords, you can use resources in the .NET Framework or the Windows Runtime to create an asynchronous method almost as easily as you create a synchronous method.</span></span> <span data-ttu-id="1e504-136">`Async` および `Await` を使用して定義する非同期メソッドは、async メソッドとして参照されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-136">Asynchronous methods that you define by using `Async` and `Await` are referred to as async methods.</span></span>  
  
 <span data-ttu-id="1e504-137">async メソッドの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-137">The following example shows an async method.</span></span> <span data-ttu-id="1e504-138">コードのほとんどは、見たことのあるものと思います。</span><span class="sxs-lookup"><span data-stu-id="1e504-138">Almost everything in the code should look completely familiar to you.</span></span> <span data-ttu-id="1e504-139">コメントは、非同期性を作成するために追加した機能を明示しています。</span><span class="sxs-lookup"><span data-stu-id="1e504-139">The comments call out the features that you add to create the asynchrony.</span></span>  
  
 <span data-ttu-id="1e504-140">このトピックの最後に完全な Windows Presentation Foundation (WPF) サンプル ファイルがあります。また、「[Async Sample: Example from "Asynchronous Programming with Async and Await" (非同期のサンプル: 「Async および Await を使用した非同期プログラミング」の例)](http://go.microsoft.com/fwlink/?LinkID=261549)」からサンプルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1e504-140">You can find a complete Windows Presentation Foundation (WPF) example file at the end of this topic, and you can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](http://go.microsoft.com/fwlink/?LinkID=261549).</span></span>  
  
```vb  
' Three things to note in the signature:  
'  - The method has an Async modifier.   
'  - The return type is Task or Task(Of T). (See "Return Types" section.)  
'    Here, it is Task(Of Integer) because the return statement returns an integer.  
'  - The method name ends in "Async."  
Async Function AccessTheWebAsync() As Task(Of Integer)  
  
    ' You need to add a reference to System.Net.Http to declare client.  
    Dim client As HttpClient = New HttpClient()  
  
    ' GetStringAsync returns a Task(Of String). That means that when you await the  
    ' task you'll get a string (urlContents).  
    Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
    ' You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork()  
  
    ' The Await operator suspends AccessTheWebAsync.  
    '  - AccessTheWebAsync can't continue until getStringTask is complete.  
    '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    '  - Control resumes here when getStringTask is complete.   
    '  - The Await operator then retrieves the string result from getStringTask.  
    Dim urlContents As String = Await getStringTask  
  
    ' The return statement specifies an integer result.  
    ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    Return urlContents.Length  
End Function  
```  
  
 <span data-ttu-id="1e504-141">`AccessTheWebAsync` に `GetStringAsync` を呼び出してその完了を待機する間で実行できる作業がない場合、次の 1 つのステートメントで呼び出しと待機をするようにコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-141">If `AccessTheWebAsync` doesn't have any work that it can do between calling `GetStringAsync` and awaiting its completion, you can simplify your code by calling and awaiting in the following single statement.</span></span>  
  
```vb  
Dim urlContents As String = Await client.GetStringAsync()  
```  
  
 <span data-ttu-id="1e504-142">次の特徴は、前の例を非同期のメソッドにするための概略です。</span><span class="sxs-lookup"><span data-stu-id="1e504-142">The following characteristics summarize what makes the previous example an async method.</span></span>  
  
-   <span data-ttu-id="1e504-143">メソッド シグネチャは `Async` 修飾子を含みます。</span><span class="sxs-lookup"><span data-stu-id="1e504-143">The method signature includes an `Async` modifier.</span></span>  
  
-   <span data-ttu-id="1e504-144">非同期メソッドの名前は、慣例により「Async」というサフィックスで終わります。</span><span class="sxs-lookup"><span data-stu-id="1e504-144">The name of an async method, by convention, ends with an "Async" suffix.</span></span>  
  
-   <span data-ttu-id="1e504-145">戻り値の型は次のいずれかになります:</span><span class="sxs-lookup"><span data-stu-id="1e504-145">The return type is one of the following types:</span></span>  
  
    -   <span data-ttu-id="1e504-146">メソッドが、オペランドに TResult 型を持つステートメントを戻す場合、<xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="1e504-146"><xref:System.Threading.Tasks.Task%601> if your method has a return statement in which the operand has type TResult.</span></span>  
  
    -   <span data-ttu-id="1e504-147">メソッドがステートメントを戻さない、またはオペランドを持たないステートメントを戻す場合、<xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="1e504-147"><xref:System.Threading.Tasks.Task> if your method has no return statement or has a return statement with no operand.</span></span>  
  
    -   <span data-ttu-id="1e504-148">非同期のイベント ハンドラーを作成する場合、[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="1e504-148">[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) if you're writing an async event handler.</span></span>  
  
     <span data-ttu-id="1e504-149">詳細については、このトピックで後述する「戻り値の型およびパラメーター」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-149">For more information, see "Return Types and Parameters" later in this topic.</span></span>  
  
-   <span data-ttu-id="1e504-150">メソッドには、通常は 1 つ以上の await 式があり、待機中の非同期操作が完了するまでメソッドを続行できないポイントをマークします。</span><span class="sxs-lookup"><span data-stu-id="1e504-150">The method usually includes at least one await expression, which marks a point where the method can't continue until the awaited asynchronous operation is complete.</span></span> <span data-ttu-id="1e504-151">この間メソッドは中断し、メソッドの呼び出し元にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-151">In the meantime, the method is suspended, and control returns to the method's caller.</span></span> <span data-ttu-id="1e504-152">このトピックの次のセクションでは、中断ポイントで何が発生するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="1e504-152">The next section of this topic illustrates what happens at the suspension point.</span></span>  
  
 <span data-ttu-id="1e504-153">非同期のメソッドでは、指定のキーワードと型を使用して何を実行するかを示すと、コンパイラがその作業を引き継ぎます。作業には、中断されたメソッドの待機ポイントにコントロールが戻された場合に実行される作業を、継続的に追跡することも含まれます。</span><span class="sxs-lookup"><span data-stu-id="1e504-153">In async methods, you use the provided keywords and types to indicate what you want to do, and the compiler does the rest, including keeping track of what must happen when control returns to an await point in a suspended method.</span></span> <span data-ttu-id="1e504-154">ループおよび例外処理など一部のルーチンのプロセスは、従来の非同期コードによる操作が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e504-154">Some routine processes, such as loops and exception handling, can be difficult to handle in traditional asynchronous code.</span></span> <span data-ttu-id="1e504-155">非同期のメソッドでは、同期ソリューションの場合と同様にこれらの要素を記述すると、問題が解決します。</span><span class="sxs-lookup"><span data-stu-id="1e504-155">In an async method, you write these elements much as you would in a synchronous solution, and the problem is solved.</span></span>  
  
 <span data-ttu-id="1e504-156">.NET Framework の以前のバージョンでの非同期性の詳細については、「[TPL と従来の .NET Framework 非同期プログラミング](http://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-156">For more information about asynchrony in previous versions of the .NET Framework, see [TPL and Traditional .NET Framework Asynchronous Programming](http://msdn.microsoft.com/library/e7b31170-a156-433f-9f26-b1fc7cd1776f).</span></span>  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a><span data-ttu-id="1e504-157">非同期メソッドでの動作</span><span class="sxs-lookup"><span data-stu-id="1e504-157">What Happens in an Async Method</span></span>  
 <span data-ttu-id="1e504-158">非同期プログラミングでは理解が必要な最も重要なことは、コントロール フローがどのようにメソッドからのメソッドに移動するかということです。</span><span class="sxs-lookup"><span data-stu-id="1e504-158">The most important thing to understand in asynchronous programming is how the control flow moves from method to method.</span></span> <span data-ttu-id="1e504-159">次の図は、このプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1e504-159">The following diagram leads you through the process.</span></span>  
  
 <span data-ttu-id="1e504-160">![非同期プログラムのトレース](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span><span class="sxs-lookup"><span data-stu-id="1e504-160">![Trace an async program](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span></span>  
  
 <span data-ttu-id="1e504-161">図内の数字は、次の手順の番号に対応しています。</span><span class="sxs-lookup"><span data-stu-id="1e504-161">The numbers in the diagram correspond to the following steps.</span></span>  
  
1.  <span data-ttu-id="1e504-162">イベント ハンドラーは `AccessTheWebAsync` 非同期のメソッドを呼び出して待機します。</span><span class="sxs-lookup"><span data-stu-id="1e504-162">An event handler calls and awaits  the  `AccessTheWebAsync` async method.</span></span>  
  
2.  <span data-ttu-id="1e504-163">`AccessTheWebAsync` は <xref:System.Net.Http.HttpClient> インスタンスを作成し、文字列として Web サイトのコンテンツをダウンロードする <xref:System.Net.Http.HttpClient.GetStringAsync%2A> 非同期メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1e504-163">`AccessTheWebAsync` creates an <xref:System.Net.Http.HttpClient> instance and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronous method to download the contents of a website as a string.</span></span>  
  
3.  <span data-ttu-id="1e504-164">`GetStringAsync` に何かが発生するとプロセスが中断します。</span><span class="sxs-lookup"><span data-stu-id="1e504-164">Something happens in `GetStringAsync` that suspends its progress.</span></span> <span data-ttu-id="1e504-165">Web サイトからのダウンロード処理、または他のブロックしているアクティビティを待機する必要が考えられます。</span><span class="sxs-lookup"><span data-stu-id="1e504-165">Perhaps it must wait for a website to download or some other blocking activity.</span></span> <span data-ttu-id="1e504-166">リソースのブロックを回避するために、`GetStringAsync` は呼び出し元の `AccessTheWebAsync` にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-166">To avoid blocking resources, `GetStringAsync` yields control to its caller, `AccessTheWebAsync`.</span></span>  
  
     <span data-ttu-id="1e504-167">`GetStringAsync` は TResult が文字列である <xref:System.Threading.Tasks.Task%601> を返し、`AccessTheWebAsync` は `getStringTask` 変数にタスクを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1e504-167">`GetStringAsync` returns a <xref:System.Threading.Tasks.Task%601> where TResult is a string, and `AccessTheWebAsync` assigns the task to the `getStringTask` variable.</span></span> <span data-ttu-id="1e504-168">タスクには `GetStringAsync` への呼び出しの進行中のプロセスを表し、作業が完了すると実際の文字列値を生成するコミットメントがあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-168">The task represents the ongoing process for the call to `GetStringAsync`, with a commitment to produce an actual string value when the work is complete.</span></span>  
  
4.  <span data-ttu-id="1e504-169">`getStringTask` が待機しないため、`AccessTheWebAsync` は `GetStringAsync` からの最終結果に依存しない他の作業を続行できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-169">Because `getStringTask` hasn't been awaited yet, `AccessTheWebAsync` can continue with other work that doesn't depend on the final result from `GetStringAsync`.</span></span> <span data-ttu-id="1e504-170">この作業は同期メソッド `DoIndependentWork` への呼び出しによって表されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-170">That work is represented by a call to the synchronous method `DoIndependentWork`.</span></span>  
  
5.  <span data-ttu-id="1e504-171">`DoIndependentWork` は、作業を実行し、呼び出し元に戻る同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1e504-171">`DoIndependentWork` is a synchronous method that does its work and returns to its caller.</span></span>  
  
6.  <span data-ttu-id="1e504-172">`AccessTheWebAsync` は `getStringTask` からの結果なしで実行できる作業を使い果たしました。</span><span class="sxs-lookup"><span data-stu-id="1e504-172">`AccessTheWebAsync` has run out of work that it can do without a result from `getStringTask`.</span></span> <span data-ttu-id="1e504-173">`AccessTheWebAsync` は次に、ダウンロードする文字列の長さを計算しますが、メソッドに文字列が戻されるまで、メソッドはその値を計算できません。</span><span class="sxs-lookup"><span data-stu-id="1e504-173">`AccessTheWebAsync` next wants to calculate and return the length of the downloaded string, but the method can't calculate that value until the method has the string.</span></span>  
  
     <span data-ttu-id="1e504-174">そのため、`AccessTheWebAsync` は await 演算子を使用してその進行を中断し、`AccessTheWebAsync` を呼び出したメソッドにコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-174">Therefore, `AccessTheWebAsync` uses an await operator to suspend its progress and to yield control to the method that called `AccessTheWebAsync`.</span></span> <span data-ttu-id="1e504-175">`AccessTheWebAsync` は呼び出し元に `Task<int>` (Visual Basic では `Task(Of Integer)`) を返します。</span><span class="sxs-lookup"><span data-stu-id="1e504-175">`AccessTheWebAsync` returns a `Task<int>` (`Task(Of Integer)` in Visual Basic) to the caller.</span></span> <span data-ttu-id="1e504-176">タスクは、ダウンロードされた文字列の長さの整数値を生成することの保証を表します。</span><span class="sxs-lookup"><span data-stu-id="1e504-176">The task represents a promise to produce an integer result that's the length of the downloaded string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e504-177">`GetStringAsync` (および、結果として `getStringTask`) が `AccessTheWebAsync` が待機する前に完了した場合、コントロールは `AccessTheWebAsync` に残ります。</span><span class="sxs-lookup"><span data-stu-id="1e504-177">If `GetStringAsync` (and therefore `getStringTask`) is complete before `AccessTheWebAsync` awaits it, control remains in `AccessTheWebAsync`.</span></span> <span data-ttu-id="1e504-178">`AccessTheWebAsync` を中断して後から戻ることは、呼び出された非同期プロセス (`getStringTask`) が既に完了していて、AccessTheWebSync が最終結果を待つ必要がない場合に、無駄になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-178">The expense of suspending and then returning to `AccessTheWebAsync` would be wasted if the called asynchronous process (`getStringTask`) has already completed and AccessTheWebSync doesn't have to wait for the final result.</span></span>  
  
     <span data-ttu-id="1e504-179">呼び出し元 (この例ではイベント ハンドラー) の内部で、処理パターンが続行されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-179">Inside the caller (the event handler in this example), the processing pattern continues.</span></span> <span data-ttu-id="1e504-180">呼び出し元は `AccessTheWebAsync` からの結果に依存しない他の作業をすることもあり、または直ちに待機状態になることもあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-180">The caller might do other work that doesn't depend on the result from `AccessTheWebAsync` before awaiting that result, or the caller might await immediately.</span></span>   <span data-ttu-id="1e504-181">イベント ハンドラーは `AccessTheWebAsync` を待機し、`AccessTheWebAsync` は、`GetStringAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="1e504-181">The event handler is waiting for `AccessTheWebAsync`, and `AccessTheWebAsync` is waiting for `GetStringAsync`.</span></span>  
  
7.  <span data-ttu-id="1e504-182">`GetStringAsync` が完了し、文字列の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="1e504-182">`GetStringAsync` completes and produces a string result.</span></span> <span data-ttu-id="1e504-183">文字列の結果は、`GetStringAsync` への呼び出しによって、意図した形式では戻されません。</span><span class="sxs-lookup"><span data-stu-id="1e504-183">The string result isn't returned by the call to `GetStringAsync` in the way that you might expect.</span></span> <span data-ttu-id="1e504-184">(メソッドは既に手順 3 のタスクで戻されていることに注意してください)。代わりに、文字列の結果は、`getStringTask` メソッドの完了を表すタスク内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-184">(Remember that the method already returned a task in step 3.) Instead, the string result is stored in the task that represents the completion of the method, `getStringTask`.</span></span> <span data-ttu-id="1e504-185">await 演算子は、`getStringTask` から結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e504-185">The await operator retrieves the result from `getStringTask`.</span></span> <span data-ttu-id="1e504-186">代入ステートメントは `urlContents` に取得された結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1e504-186">The assignment statement assigns the retrieved result to `urlContents`.</span></span>  
  
8.  <span data-ttu-id="1e504-187">`AccessTheWebAsync` に文字列の結果がある場合、メソッドは文字列の長さを計算できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-187">When `AccessTheWebAsync` has the string result, the method can calculate the length of the string.</span></span> <span data-ttu-id="1e504-188">次に `AccessTheWebAsync` の作業も完了し、待機しているイベント ハンドラーが再開できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-188">Then the work of `AccessTheWebAsync` is also complete, and the waiting event handler can resume.</span></span> <span data-ttu-id="1e504-189">トピックの最後にある完全なサンプルでは、イベント ハンドラーが長さの結果の値を取得して印刷することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-189">In the full example at the end of the topic, you can confirm that the event handler retrieves and prints the value of the length result.</span></span>  
  
 <span data-ttu-id="1e504-190">非同期プログラミングの経験がない場合、同期および非同期の動作の違いを、少し時間を割いて考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-190">If you are new to asynchronous programming, take a minute to consider the difference between synchronous and asynchronous behavior.</span></span> <span data-ttu-id="1e504-191">同期メソッドは作業が完了すると戻されます (手順 5.) が、非同期のメソッドは、作業が中断されるとタスクの値を戻します。(手順 3. および 6.)</span><span class="sxs-lookup"><span data-stu-id="1e504-191">A synchronous method returns when its work is complete (step 5), but an async method returns a task value when its work is suspended (steps 3 and 6).</span></span> <span data-ttu-id="1e504-192">非同期のメソッドが最終的に作業を完了すると、タスクは完了とマークされ、結果が存在する場合はタスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-192">When the async method eventually completes its work, the task is marked as completed and the result, if any, is stored in the task.</span></span>  
  
 <span data-ttu-id="1e504-193">制御フローの詳細については、「[非同期プログラムにおける制御フロー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-193">For more information about control flow, see [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
##  <a name="BKMK_APIAsyncMethods"></a><span data-ttu-id="1e504-194">API の非同期メソッド</span><span class="sxs-lookup"><span data-stu-id="1e504-194">API Async Methods</span></span>  
 <span data-ttu-id="1e504-195">非同期のプログラミングをサポートする `GetStringAsync` などのメソッドがどこにあるのかということです。</span><span class="sxs-lookup"><span data-stu-id="1e504-195">You might be wondering where to find methods such as `GetStringAsync` that support async programming.</span></span> <span data-ttu-id="1e504-196">.NET Framework 4.5 以降には、`Async` および `Await` で使用する多くのメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e504-196">The  .NET Framework 4.5 or higher contains many members that work with `Async` and `Await`.</span></span> <span data-ttu-id="1e504-197">メンバー名と <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> の戻り値の型に付けられている「Async」というサフィックスでこれらのメンバーを識別できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-197">You can recognize these members by the "Async" suffix that’s attached to the member name and a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1e504-198">たとえば、`System.IO.Stream` のクラスには、同期メソッドの <xref:System.IO.Stream.CopyTo%2A>、<xref:System.IO.Stream.Read%2A>、および <xref:System.IO.Stream.Write%2A> と共に、<xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> および <xref:System.IO.Stream.WriteAsync%2A> という同期メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e504-198">For example, the `System.IO.Stream` class contains methods such as <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> alongside the synchronous methods <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, and <xref:System.IO.Stream.Write%2A>.</span></span>  
  
 <span data-ttu-id="1e504-199">Windows ランタイムにも、Windows アプリの `Async` と `Await` で使用できる多くのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e504-199">The Windows Runtime also contains many methods that you can use with `Async` and `Await` in Windows apps.</span></span> <span data-ttu-id="1e504-200">詳細およびサンプル メソッドについては、「[クイック スタート: await 演算子を使用した非同期プログラミング](http://go.microsoft.com/fwlink/?LinkId=248545)」、「[非同期プログラミング (Windows ストア アプリ)](http://go.microsoft.com/fwlink/?LinkId=259592)」、および「[WhenAny: .NET Framework と Windows ランタイム間のブリッジ](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-200">For more information and example methods, see [Quickstart: using the await operator for asynchronous programming](http://go.microsoft.com/fwlink/?LinkId=248545), [Asynchronous programming (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=259592), and [WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx).</span></span>  
  
##  <a name="BKMK_Threads"></a><span data-ttu-id="1e504-201">スレッド</span><span class="sxs-lookup"><span data-stu-id="1e504-201">Threads</span></span>  
 <span data-ttu-id="1e504-202">非同期のメソッドは非ブロッキング操作を意図しています。</span><span class="sxs-lookup"><span data-stu-id="1e504-202">Async methods are intended to be non-blocking operations.</span></span> <span data-ttu-id="1e504-203">非同期のメソッドの `Await` 式は、待機中のタスクの実行中に現在のスレッドをブロックしません。</span><span class="sxs-lookup"><span data-stu-id="1e504-203">An `Await` expression in an async method doesn’t block the current thread while the awaited task is running.</span></span> <span data-ttu-id="1e504-204">代わりに、式はメソッドの残りの部分の継続を登録し、非同期のメソッドの呼び出し元にコントロールを戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-204">Instead, the expression signs up the rest of the method as a continuation and returns control to the caller of the async method.</span></span>  
  
 <span data-ttu-id="1e504-205">`Async` および `Await` キーワードは、追加のスレッドを作成する要因にはなりません。</span><span class="sxs-lookup"><span data-stu-id="1e504-205">The `Async` and `Await` keywords don't cause additional threads to be created.</span></span> <span data-ttu-id="1e504-206">非同期のメソッドは自分自身のスレッドで実行しないため、マルチスレッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1e504-206">Async methods don't require multithreading because an async method doesn't run on its own thread.</span></span> <span data-ttu-id="1e504-207">メソッドは、現在の同期コンテキストで実行し、メソッドがアクティブな場合に限りスレッドの時間を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e504-207">The method runs on the current synchronization context and uses time on the thread only when the method is active.</span></span> <span data-ttu-id="1e504-208"><xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> を使用して、CPU バインディングの作業をバックグラウンド スレッドに移動できますが、バックグラウンド スレッドは、結果を待つだけのプロセスを援助しません。</span><span class="sxs-lookup"><span data-stu-id="1e504-208">You can use <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> to move CPU-bound work to a background thread, but a background thread doesn't help with a process that's just waiting for results to become available.</span></span>  
  
 <span data-ttu-id="1e504-209">非同期プログラミングへの非同期ベースのアプローチは、ほぼすべてのケースの既存のアプローチに推奨されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-209">The async-based approach to asynchronous programming is preferable to existing approaches in almost every case.</span></span> <span data-ttu-id="1e504-210">特に、このアプローチはコードがシンプルで競合状態からの保護の必要がないため、I/O バインディングの操作では、<xref:System.ComponentModel.BackgroundWorker> よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="1e504-210">In particular, this approach is better than <xref:System.ComponentModel.BackgroundWorker> for IO-bound operations because the code is simpler and you don't have to guard against race conditions.</span></span> <span data-ttu-id="1e504-211"><xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> と組み合わせると、非同期のプログラミングは CPU バインディングの操作に関して <xref:System.ComponentModel.BackgroundWorker> よりも優れています。非同期のプログラミングは、`Task.Run` がスレッド プールから移動する作業から、実行するコードの調整の詳細を分離するためです。</span><span class="sxs-lookup"><span data-stu-id="1e504-211">In combination with <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, async programming is better than <xref:System.ComponentModel.BackgroundWorker> for CPU-bound operations because async programming separates the coordination details of running your code from the work that `Task.Run` transfers to the threadpool.</span></span>  
  
##  <a name="BKMK_AsyncandAwait"></a><span data-ttu-id="1e504-212">Async と Await</span><span class="sxs-lookup"><span data-stu-id="1e504-212">Async and Await</span></span>  
 <span data-ttu-id="1e504-213">[Async](../../../../visual-basic/language-reference/modifiers/async.md) 修飾子を使用して、メソッドが非同期メソッドであることを指定すると、次の 2 つの機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="1e504-213">If you specify that a method is an async method by using an [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier, you enable the following two capabilities.</span></span>  
  
-   <span data-ttu-id="1e504-214">マークされた非同期のメソッドは中断ポイントを示すために [Await](../../../../visual-basic/language-reference/operators/await-operator.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-214">The marked async method can use [Await](../../../../visual-basic/language-reference/operators/await-operator.md) to designate suspension points.</span></span> <span data-ttu-id="1e504-215">await 演算子は、非同期のメソッドが、待機中の非同期のプロセスが完了するまでこのポイント以降を続行できないことを、コンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-215">The await operator tells the compiler that the async method can't continue past that point until the awaited asynchronous process is complete.</span></span> <span data-ttu-id="1e504-216">その間、コントロールは非同期のメソッドの呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-216">In the meantime, control returns to the caller of the async method.</span></span>  
  
     <span data-ttu-id="1e504-217">非同期のメソッドの `Await` 式での中断は、メソッドからの終了を意図するものではなく、`Finally` ブロックは実行されません。</span><span class="sxs-lookup"><span data-stu-id="1e504-217">The suspension of an async method at an `Await` expression doesn't constitute an exit from the method, and `Finally` blocks don’t run.</span></span>  
  
-   <span data-ttu-id="1e504-218">マークされた非同期のメソッド自体は、呼び出し元のメソッドによって待機できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-218">The marked async method can itself be awaited by methods that call it.</span></span>  
  
 <span data-ttu-id="1e504-219">非同期のメソッドには、通常の `Await` 演算子が 1 つ以上ありますが、`Await` 式がない場合もコンパイラ エラーの原因にはなりません。</span><span class="sxs-lookup"><span data-stu-id="1e504-219">An async method typically contains one or more occurrences of an `Await` operator, but the absence of `Await` expressions doesn’t cause a compiler error.</span></span> <span data-ttu-id="1e504-220">中断ポイントをマークするために非同期のメソッドが `Await` 演算子を使用しない場合、`Async` 修飾子が存在しても、メソッドは同期メソッドと同様に実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-220">If an async method doesn’t use an `Await` operator to mark a suspension point, the method executes as a synchronous method does, despite the `Async` modifier.</span></span> <span data-ttu-id="1e504-221">このようなメソッドには、コンパイラが警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="1e504-221">The compiler issues a warning for such methods.</span></span>  
  
 <span data-ttu-id="1e504-222">`Async` と `Await` は、コンテキスト キーワードです。</span><span class="sxs-lookup"><span data-stu-id="1e504-222">`Async` and `Await` are contextual keywords.</span></span> <span data-ttu-id="1e504-223">詳細およびサンプルについては、次のトピックを参照してください:</span><span class="sxs-lookup"><span data-stu-id="1e504-223">For more information and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="1e504-224">Async</span><span class="sxs-lookup"><span data-stu-id="1e504-224">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [<span data-ttu-id="1e504-225">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="1e504-225">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a><span data-ttu-id="1e504-226">戻り値の型およびパラメーター</span><span class="sxs-lookup"><span data-stu-id="1e504-226">Return Types and Parameters</span></span>  
 <span data-ttu-id="1e504-227">.NET Framework プログラミングでは、非同期のメソッドは、一般的に <xref:System.Threading.Tasks.Task>、または <xref:System.Threading.Tasks.Task%601> を戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-227">In .NET Framework programming, an async method typically returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1e504-228">非同期のメソッド内で、`Await` 演算子は、他の非同期のメソッドへの呼び出しから戻されたタスクに適用されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-228">Inside an async method, an `Await` operator is applied to a task that's returned from a call to another async method.</span></span>  
  
 <span data-ttu-id="1e504-229">メソッドが、`TResult` 型のオペランドを指定する [Return](../../../../visual-basic/language-reference/statements/return-statement.md) ステートメントを含む場合、<xref:System.Threading.Tasks.Task%601> を戻り値の型として指定します。</span><span class="sxs-lookup"><span data-stu-id="1e504-229">You specify <xref:System.Threading.Tasks.Task%601> as the return type if the method contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that specifies an operand of type `TResult`.</span></span>  
  
 <span data-ttu-id="1e504-230">メソッドに Return ステートメントがない場合、または Return ステートメントがオペランドを戻さない場合、`Task` を戻り値の型として使用します。</span><span class="sxs-lookup"><span data-stu-id="1e504-230">You use `Task` as the return type if the method has no return statement or has a return statement that doesn't return an operand.</span></span>  
  
 <span data-ttu-id="1e504-231">次のサンプルは、<xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task> を戻すメソッドを宣言し、呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-231">The following example shows how you declare and call a method that returns a <xref:System.Threading.Tasks.Task%601> or a <xref:System.Threading.Tasks.Task>.</span></span>  
  
```vb  
' Signature specifies Task(Of Integer)  
Async Function TaskOfTResult_MethodAsync() As Task(Of Integer)  
  
    Dim hours As Integer  
    ' . . .  
    ' Return statement specifies an integer result.  
    Return hours  
End Function  
  
' Calls to TaskOfTResult_MethodAsync  
Dim returnedTaskTResult As Task(Of Integer) = TaskOfTResult_MethodAsync()  
Dim intResult As Integer = Await returnedTaskTResult  
' or, in a single statement  
Dim intResult As Integer = Await TaskOfTResult_MethodAsync()  
  
' Signature specifies Task  
Async Function Task_MethodAsync() As Task  
  
    ' . . .  
    ' The method has no return statement.  
End Function  
  
' Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync()  
Await returnedTask  
' or, in a single statement  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="1e504-232">それぞれ、進行中の作業を示すタスクを戻します。</span><span class="sxs-lookup"><span data-stu-id="1e504-232">Each returned task represents ongoing work.</span></span> <span data-ttu-id="1e504-233">タスクに非同期処理の状態に関する情報、および最終的にはプロセスからの最終結果、またはプロセスが成功しなかった場合に発生する例外をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="1e504-233">A task encapsulates information about the state of the asynchronous process and, eventually, either the final result from the process or the exception that the process raises if it doesn't succeed.</span></span>  
  
 <span data-ttu-id="1e504-234">非同期のメソッドは、`Sub` メソッドにもなります。</span><span class="sxs-lookup"><span data-stu-id="1e504-234">An async method can also be a `Sub` method.</span></span> <span data-ttu-id="1e504-235">この戻り値の型は主として、戻り値の型が必要なイベント ハンドラーの定義に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e504-235">This return type is used primarily to define event handlers, where a return type is required.</span></span> <span data-ttu-id="1e504-236">非同期のイベント ハンドラーは通常、非同期のプログラムの開始点として機能します。</span><span class="sxs-lookup"><span data-stu-id="1e504-236">Async event handlers often serve as the starting point for async programs.</span></span>  
  
 <span data-ttu-id="1e504-237">`Sub` プロシージャである非同期のメソッドは、待機できません。呼び出し元は、このメソッドがスローする例外をキャッチできません。</span><span class="sxs-lookup"><span data-stu-id="1e504-237">An async method that’s a `Sub` procedure can’t be awaited, and the caller can't catch any exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="1e504-238">非同期のメソッドで [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) パラメーターを宣言することはできませんが、これらのパラメーターを持つメソッドを呼び出すことはできます。</span><span class="sxs-lookup"><span data-stu-id="1e504-238">An async method can't declare [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parameters, but the method can call methods that have such parameters.</span></span>  
  
 <span data-ttu-id="1e504-239">使用例を含む詳細については、「[非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-239">For more information and examples, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span> <span data-ttu-id="1e504-240">非同期のメソッドで例外をキャッチする方法の詳細については、「[Try...Catch...Finally Statement (Try...Catch...Finally ステートメント)](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-240">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="1e504-241">Windows ランタイム プログラミングの非同期 API には、タスクに類似した次のような戻り値の型の 1 つがあります。</span><span class="sxs-lookup"><span data-stu-id="1e504-241">Asynchronous APIs in Windows Runtime  programming have one of the following return types, which are similar to tasks:</span></span>  
  
-   <span data-ttu-id="1e504-242">[IAsyncOperation](http://go.microsoft.com/fwlink/p/?LinkId=261896) (<xref:System.Threading.Tasks.Task%601> に対応)</span><span class="sxs-lookup"><span data-stu-id="1e504-242">[IAsyncOperation](http://go.microsoft.com/fwlink/p/?LinkId=261896), which corresponds to <xref:System.Threading.Tasks.Task%601></span></span>  
  
-   <span data-ttu-id="1e504-243">[IAsyncAction](http://go.microsoft.com/fwlink/p/?LinkId=261897) (<xref:System.Threading.Tasks.Task> に対応)</span><span class="sxs-lookup"><span data-stu-id="1e504-243">[IAsyncAction](http://go.microsoft.com/fwlink/p/?LinkId=261897), which corresponds to <xref:System.Threading.Tasks.Task></span></span>  
  
-   [<span data-ttu-id="1e504-244">IAsyncActionWithProgress</span><span class="sxs-lookup"><span data-stu-id="1e504-244">IAsyncActionWithProgress</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=261898)  
  
-   [<span data-ttu-id="1e504-245">IAsyncOperationWithProgress</span><span class="sxs-lookup"><span data-stu-id="1e504-245">IAsyncOperationWithProgress</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=259454)  
  
 <span data-ttu-id="1e504-246">詳細およびサンプルついては、「[クイック スタート: 非同期プログラミングに await 演算子を使用する](http://go.microsoft.com/fwlink/p/?LinkId=248545)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e504-246">For more information and an example, see [Quickstart: using the await operator for asynchronous programming](http://go.microsoft.com/fwlink/p/?LinkId=248545).</span></span>  
  
##  <a name="BKMK_NamingConvention"></a><span data-ttu-id="1e504-247">名前付け規約</span><span class="sxs-lookup"><span data-stu-id="1e504-247">Naming Convention</span></span>  
 <span data-ttu-id="1e504-248">慣例により、`Async` 修飾子を持つメソッドの名前には、"Async" を追加します。</span><span class="sxs-lookup"><span data-stu-id="1e504-248">By convention, you append "Async" to the names of methods that have an `Async` modifier.</span></span>  
  
 <span data-ttu-id="1e504-249">イベント、基底クラス、またはインターフェイスのコントラクトが別の名前を表示している場合は、この慣例を無視できます。</span><span class="sxs-lookup"><span data-stu-id="1e504-249">You can ignore the convention where an event, base class, or interface contract suggests a different name.</span></span> <span data-ttu-id="1e504-250">たとえば、`Button1_Click` などの共通のイベント ハンドラーの名前は、変更しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1e504-250">For example, you shouldn’t rename common event handlers, such as `Button1_Click`.</span></span>  
  
##  <a name="BKMK_RelatedTopics"></a><span data-ttu-id="1e504-251">関連トピックとサンプル (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1e504-251">Related Topics and Samples (Visual Studio)</span></span>  
  
|<span data-ttu-id="1e504-252">タイトル</span><span class="sxs-lookup"><span data-stu-id="1e504-252">Title</span></span>|<span data-ttu-id="1e504-253">説明</span><span class="sxs-lookup"><span data-stu-id="1e504-253">Description</span></span>|<span data-ttu-id="1e504-254">サンプル</span><span class="sxs-lookup"><span data-stu-id="1e504-254">Sample</span></span>|  
|-----------|-----------------|------------|  
|[<span data-ttu-id="1e504-255">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-255">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|<span data-ttu-id="1e504-256">同期 WPF のソリューションを非同期 WPF のソリューションに変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-256">Shows how to convert a synchronous WPF solution to an asynchronous WPF solution.</span></span> <span data-ttu-id="1e504-257">アプリケーションは、一連の Web サイトをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1e504-257">The application downloads a series of websites.</span></span>|[<span data-ttu-id="1e504-258">Async Sample: Accessing the Web Walkthrough (非同期のサンプル: Web サイトへのアクセスのチュートリアル)</span><span class="sxs-lookup"><span data-stu-id="1e504-258">Async Sample: Accessing the Web Walkthrough</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=255191&clcid=0x409)|  
|[<span data-ttu-id="1e504-259">方法: Task.WhenAll を使用して AsyncWalkthrough を拡張する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-259">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|<span data-ttu-id="1e504-260">前のチュートリアルに <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> を追加します。</span><span class="sxs-lookup"><span data-stu-id="1e504-260">Adds <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> to the previous walkthrough.</span></span> <span data-ttu-id="1e504-261">`WhenAll` を使用すると、すべてのダウンロードが同時に開始します。</span><span class="sxs-lookup"><span data-stu-id="1e504-261">The use of `WhenAll` starts all the downloads at the same time.</span></span>||  
|[<span data-ttu-id="1e504-262">方法: Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-262">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|<span data-ttu-id="1e504-263">複数のタスクを同時に開始する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-263">Demonstrates how to start several tasks at the same time.</span></span>|[<span data-ttu-id="1e504-264">Async Sample: Make Multiple Web Requests in Parallel (非同期のサンプル: 複数の並行 Web 要求の作成)</span><span class="sxs-lookup"><span data-stu-id="1e504-264">Async Sample: Make Multiple Web Requests in Parallel</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=254906&clcid=0x409)|  
|[<span data-ttu-id="1e504-265">非同期の戻り値の型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-265">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)|<span data-ttu-id="1e504-266">非同期のメソッドが戻す型、および各型の適切な使用方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1e504-266">Illustrates the types that async methods can return and explains when each type is appropriate.</span></span>||  
|[<span data-ttu-id="1e504-267">非同期プログラムにおける制御フロー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-267">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|<span data-ttu-id="1e504-268">非同期プログラムでの await 式を継続して、コントロールのフローの詳細をトレースします。</span><span class="sxs-lookup"><span data-stu-id="1e504-268">Traces in detail the flow of control through a succession of await expressions in an asynchronous program.</span></span>|[<span data-ttu-id="1e504-269">Async Sample: Control Flow in Async Programs (非同期のサンプル: 非同期プログラムにおける制御フロー)</span><span class="sxs-lookup"><span data-stu-id="1e504-269">Async Sample: Control Flow in Async Programs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=255285&clcid=0x409)|  
|[<span data-ttu-id="1e504-270">非同期アプリケーションの微調整 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-270">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)|<span data-ttu-id="1e504-271">非同期のソリューションに次の機能を追加する方法を示します:</span><span class="sxs-lookup"><span data-stu-id="1e504-271">Shows how to add the following functionality to your async solution:</span></span><br /><br /> <span data-ttu-id="1e504-272">-   [非同期タスクまたはタスクの一覧のキャンセル (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="1e504-272">-   [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span></span><br /><span data-ttu-id="1e504-273">-   [指定した時間の経過後の非同期タスクのキャンセル (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span><span class="sxs-lookup"><span data-stu-id="1e504-273">-   [Cancel Async Tasks after a Period of Time (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span></span><br /><span data-ttu-id="1e504-274">-   [完了後の残りの非同期タスクのキャンセル (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span><span class="sxs-lookup"><span data-stu-id="1e504-274">-   [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span></span><br /><span data-ttu-id="1e504-275">-   [完了時での複数の同期タスクとプロセスの実行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span><span class="sxs-lookup"><span data-stu-id="1e504-275">-   [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span></span>|[<span data-ttu-id="1e504-276">Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)</span><span class="sxs-lookup"><span data-stu-id="1e504-276">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=255046&clcid=0x409)|  
|[<span data-ttu-id="1e504-277">非同期アプリにおける再入の処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-277">Handling Reentrancy in Async Apps (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|<span data-ttu-id="1e504-278">実行中にアクティブな非同期操作を再起動するケースの処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-278">Shows how to handle cases in which an active asynchronous operation is restarted while it’s running.</span></span>||  
|<span data-ttu-id="1e504-279">[WhenAny: .NET Framework と Windows ランタイム間のブリッジ](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="1e504-279">[WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span></span>|<span data-ttu-id="1e504-280">[!INCLUDE[wrt](~/includes/wrt-md.md)] のメソッドの <xref:System.Threading.Tasks.Task.WhenAny%2A> を使用可能にするために、[!INCLUDE[wrt](~/includes/wrt-md.md)] で、.NET Framework および IAsyncOperations のタスクの種類間をブリッジする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-280">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.Tasks.Task.WhenAny%2A> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="1e504-281">Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny) (非同期のサンプル: .NET と Windows ランタイム間のブリッジ (AsTask と WhenAny))</span><span class="sxs-lookup"><span data-stu-id="1e504-281">Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny)</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=260638)|  
|<span data-ttu-id="1e504-282">非同期のキャンセル: .NET Framework と Windows ランタイム間のブリッジ</span><span class="sxs-lookup"><span data-stu-id="1e504-282">Async Cancellation: Bridging between the .NET Framework and the Windows Runtime</span></span>|<span data-ttu-id="1e504-283">[!INCLUDE[wrt](~/includes/wrt-md.md)] のメソッドの <xref:System.Threading.CancellationTokenSource> を使用可能にするために、[!INCLUDE[wrt](~/includes/wrt-md.md)] で、.NET Framework および IAsyncOperations のタスクの種類間をブリッジする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-283">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.CancellationTokenSource> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="1e504-284">Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation) (非同期のサンプル: .NET と Windows ランタイム間のブリッジ (AsTask と Cancellation))</span><span class="sxs-lookup"><span data-stu-id="1e504-284">Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation)</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=263004)|  
|[<span data-ttu-id="1e504-285">ファイル アクセスにおける非同期の使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e504-285">Using Async for File Access (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/using-async-for-file-access.md)|<span data-ttu-id="1e504-286">async および await を使用してファイルにアクセスすることの利点の一覧と紹介です。</span><span class="sxs-lookup"><span data-stu-id="1e504-286">Lists and demonstrates the benefits of using async and await to access files.</span></span>||  
|[<span data-ttu-id="1e504-287">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="1e504-287">Task-based Asynchronous Pattern (TAP)</span></span>](http://msdn.microsoft.com/library/8cef1fcf-6f9f-417c-b21f-3fd8bac75007)|<span data-ttu-id="1e504-288">.NET Framework での非同期性の新しいパターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1e504-288">Describes a new pattern for asynchrony in the .NET Framework.</span></span> <span data-ttu-id="1e504-289">パターンは <xref:System.Threading.Tasks.Task> および <xref:System.Threading.Tasks.Task%601> の型に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1e504-289">The pattern is based on the <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> types.</span></span>||  
|[<span data-ttu-id="1e504-290">Channel 9 の非同期に関するビデオ</span><span class="sxs-lookup"><span data-stu-id="1e504-290">Async Videos on Channel 9</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=267466)|<span data-ttu-id="1e504-291">非同期のプログラミングに関するさまざまなビデオへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="1e504-291">Provides links to a variety of videos about async programming.</span></span>||  
  
##  <a name="BKMK_CompleteExample"></a><span data-ttu-id="1e504-292">コード例全体</span><span class="sxs-lookup"><span data-stu-id="1e504-292">Complete Example</span></span>  
 <span data-ttu-id="1e504-293">次のコードは、このトピックで説明する Windows Presentation Foundation (WPF) アプリケーションの MainWindow.xaml.vb ファイルです。</span><span class="sxs-lookup"><span data-stu-id="1e504-293">The following code is the MainWindow.xaml.vb file from the Windows Presentation Foundation (WPF) application that this topic discusses.</span></span> <span data-ttu-id="1e504-294">サンプルは、「[Async Sample: Example from "Asynchronous Programming with Async and Await" (非同期のサンプル: 「Async および Await を使用した非同期プログラミング」の例)](http://go.microsoft.com/fwlink/p/?LinkID=261549)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="1e504-294">You can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](http://go.microsoft.com/fwlink/p/?LinkID=261549).</span></span>  
  
```vb  
' Add an Imports statement and a reference for System.Net.Http  
Imports System.Net.Http  
  
Class MainWindow  
  
    ' Mark the event handler with async so you can use Await in it.  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Call and await separately.  
        'Task<int> getLengthTask = AccessTheWebAsync();  
        '' You can do independent work here.  
        'int contentLength = await getLengthTask;  
  
        Dim contentLength As Integer = Await AccessTheWebAsync()  
  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
    End Sub  
  
    ' Three things to note in the signature:  
    '  - The method has an Async modifier.   
    '  - The return type is Task or Task(Of T). (See "Return Types" section.)  
    '    Here, it is Task(Of Integer) because the return statement returns an integer.  
    '  - The method name ends in "Async."  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' You need to add a reference to System.Net.Http to declare client.  
        Dim client As HttpClient = New HttpClient()  
  
        ' GetStringAsync returns a Task(Of String). That means that when you await the  
        ' task you'll get a string (urlContents).  
        Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork()  
  
        ' The Await operator suspends AccessTheWebAsync.  
        '  - AccessTheWebAsync can't continue until getStringTask is complete.  
        '  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        '  - Control resumes here when getStringTask is complete.   
        '  - The Await operator then retrieves the string result from getStringTask.  
        Dim urlContents As String = Await getStringTask  
  
        ' The return statement specifies an integer result.  
        ' Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        Return urlContents.Length  
    End Function  
  
    Sub DoIndependentWork()  
        ResultsTextBox.Text &= "Working . . . . . . ." & vbCrLf  
    End Sub  
End Class  
  
' Sample Output:  
  
' Working . . . . . . .  
  
' Length of the downloaded string: 41763.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e504-295">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e504-295">See Also</span></span>  
 [<span data-ttu-id="1e504-296">Await 演算子</span><span class="sxs-lookup"><span data-stu-id="1e504-296">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="1e504-297">Async</span><span class="sxs-lookup"><span data-stu-id="1e504-297">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
