---
title: "非同期アプリケーションの微調整 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7afcdb28fbe10d5aa33dd2704d264ffd716af5d6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="41e69-102">非同期アプリケーションの微調整 (C#)</span><span class="sxs-lookup"><span data-stu-id="41e69-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="41e69-103"><xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使用して、非同期アプリケーションに精度と柔軟性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="41e69-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="41e69-104">このセクションのトピックでは <xref:System.Threading.CancellationToken> および `Task` などのような、重要な <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> メソッドおよび <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="41e69-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="41e69-105">`WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。</span><span class="sxs-lookup"><span data-stu-id="41e69-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="41e69-106">`WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="41e69-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="41e69-107">`WhenAny` を使う例については、「[完了後の残りの非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)」および「[完了時での複数の同期タスクとプロセスの実行 (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41e69-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="41e69-108">`WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="41e69-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="41e69-109">`WhenAll` の使用に関する詳細と例については、「[方法: Task.WhenAll を使用して async Walkthrough を拡張する (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="41e69-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="41e69-110">ここでは、次の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="41e69-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="41e69-111">[非同期タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="41e69-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="41e69-112">指定した時間の経過後の非同期タスクのキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="41e69-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="41e69-113">完了後の残りの非同期タスクのキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="41e69-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="41e69-114">完了時での複数の同期タスクとプロセスの実行 (C#)</span><span class="sxs-lookup"><span data-stu-id="41e69-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="41e69-115">この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41e69-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="41e69-116">次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。</span><span class="sxs-lookup"><span data-stu-id="41e69-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="41e69-117">ボタンの名前は `startButton` と `cancelButton` です。</span><span class="sxs-lookup"><span data-stu-id="41e69-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="41e69-118">![[キャンセル] ボタンが表示された WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")</span><span class="sxs-lookup"><span data-stu-id="41e69-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="41e69-119">完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="41e69-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e69-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="41e69-120">See Also</span></span>  
 [<span data-ttu-id="41e69-121">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="41e69-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)

