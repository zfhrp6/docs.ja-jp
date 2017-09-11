---
title: "非同期アプリケーション (Visual Basic) の微調整 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e031c2e23430a62629424ee57a140a7d8da41777
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="f5a07-102">非同期アプリケーション (Visual Basic) の微調整</span><span class="sxs-lookup"><span data-stu-id="f5a07-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="f5a07-103">できる精度と柔軟性、非同期アプリケーションに使用して追加するメソッドとプロパティを<xref:System.Threading.Tasks.Task>型が使用できるようにします</xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="f5a07-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="f5a07-104">このセクションのトピックを使用する例を示して<xref:System.Threading.CancellationToken>重要な`Task`<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>および<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>などの方法</xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="f5a07-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="f5a07-105">`WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。</span><span class="sxs-lookup"><span data-stu-id="f5a07-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="f5a07-106">`WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="f5a07-107">使用する例について`WhenAny`を参照してください[1 つの完了 (Visual Basic) の後に残りの非同期タスクのキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)と[複数の同期タスクの開始、プロセスとして、完全な (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="f5a07-108">`WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="f5a07-109">詳細については、使用する例を`WhenAll`を参照してください[する方法: Task.WhenAll を使用する」(Visual Basic の場合) して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="f5a07-110">ここでは、次の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="f5a07-111">[非同期タスクまたはタスク (Visual Basic) の一覧を取り消す](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="f5a07-112">経過時間 (Visual Basic) の非同期タスクをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="f5a07-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="f5a07-113">1 つは、(Visual Basic) の完了後の残りの非同期タスクのキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="f5a07-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="f5a07-114">複数の同期タスクし、プロセスの完了 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5a07-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="f5a07-115">例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="f5a07-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="f5a07-116">次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="f5a07-117">ボタンの名前は `startButton` と `cancelButton` です。</span><span class="sxs-lookup"><span data-stu-id="f5a07-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="f5a07-118">![[キャンセル] ボタンを WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")</span><span class="sxs-lookup"><span data-stu-id="f5a07-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="f5a07-119">完全な Windows Presentation Foundation (WPF) プロジェクトをダウンロードする[Async サンプル: 細かいアプリケーションの調整](http://go.microsoft.com/fwlink/?LinkId=255046)します。</span><span class="sxs-lookup"><span data-stu-id="f5a07-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a07-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5a07-120">See Also</span></span>  
 [<span data-ttu-id="f5a07-121">非同期プログラミングを Async と Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5a07-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
