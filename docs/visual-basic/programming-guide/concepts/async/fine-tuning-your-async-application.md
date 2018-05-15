---
title: 非同期アプリケーション (Visual Basic) の微調整
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 34aa79da671f11dc53ac2b0306730d510fb09515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="d8fc0-102">非同期アプリケーション (Visual Basic) の微調整</span><span class="sxs-lookup"><span data-stu-id="d8fc0-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="d8fc0-103"><xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使用して、非同期アプリケーションに精度と柔軟性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="d8fc0-104">このセクションのトピックでは <xref:System.Threading.CancellationToken> および `Task` などのような、重要な <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> メソッドおよび <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d8fc0-105">`WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="d8fc0-106">`WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="d8fc0-107">使用する例について`WhenAny`を参照してください[1 つは、完了 (Visual Basic) の後に残りの非同期タスクのキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)と[複数の非同期タスクの開始、プロセスとして、完全な (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="d8fc0-108">`WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="d8fc0-109">詳細については、使用する例を`WhenAll`を参照してください[する方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="d8fc0-110">ここでは、次の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="d8fc0-111">[非同期タスクまたはタスク (Visual Basic) の一覧のキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="d8fc0-112">非同期タスクのキャンセル後一定の時間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fc0-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="d8fc0-113">完了 (Visual Basic の場合) は、1 つ後の残りの非同期タスクのキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="d8fc0-114">複数の非同期タスクし、プロセスの完了 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fc0-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="d8fc0-115">この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="d8fc0-116">次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="d8fc0-117">ボタンの名前は `startButton` と `cancelButton` です。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="d8fc0-118">![[キャンセル] ボタンが表示された WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")</span><span class="sxs-lookup"><span data-stu-id="d8fc0-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="d8fc0-119">完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="d8fc0-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8fc0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8fc0-120">See Also</span></span>  
 [<span data-ttu-id="d8fc0-121">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8fc0-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
