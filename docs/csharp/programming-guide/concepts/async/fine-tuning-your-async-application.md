---
title: 非同期アプリケーションの微調整 (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cf4e0082fbaa2a5189646014e53f0320e16f40de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322758"
---
# <a name="fine-tuning-your-async-application-c"></a>非同期アプリケーションの微調整 (C#)
<xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使用して、非同期アプリケーションに精度と柔軟性を追加できます。 このセクションのトピックでは <xref:System.Threading.CancellationToken> および `Task` などのような、重要な <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> メソッドおよび <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> の使用例を示します。  
  
 `WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。  
  
-   `WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。  
  
     `WhenAny` を使う例については、「[完了後の残りの非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)」および「[完了時での複数の同期タスクとプロセスの実行 (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)」をご覧ください。  
  
-   `WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。  
  
     `WhenAll` の使用に関する詳細と例については、「[方法: Task.WhenAll を使用して async Walkthrough を拡張する (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」をご覧ください。  
  
 ここでは、次の例について説明します。  
  
-   [非同期タスクまたはタスクの一覧のキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
  
-   [指定した時間の経過後の非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [完了後の残りの非同期タスクのキャンセル (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [完了時での複数の同期タスクとプロセスの実行 (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  この例を実行するには、Visual Studio 2012 以降および .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。  
  
 次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。 ボタンの名前は `startButton` と `cancelButton` です。  
  
 ![[キャンセル] ボタンが表示された WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")  
  
 完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。  
  
## <a name="see-also"></a>参照  
 [Async および Await を使用した非同期プログラミング (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
