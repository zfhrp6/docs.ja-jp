---
title: 非同期アプリケーション (Visual Basic) の微調整
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6e919d3998719186d0355b9bd187782fcb0e5332
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696677"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a>非同期アプリケーション (Visual Basic) の微調整
<xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使用して、非同期アプリケーションに精度と柔軟性を追加できます。 このセクションのトピックでは <xref:System.Threading.CancellationToken> および `Task` などのような、重要な <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> メソッドおよび <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> の使用例を示します。  
  
 `WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。  
  
-   `WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。  
  
     使用する例について`WhenAny`を参照してください[1 つは、完了 (Visual Basic) の後に残りの非同期タスクのキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)と[複数の非同期タスクの開始、プロセスとして、完全な (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)です。  
  
-   `WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。  
  
     詳細については、使用する例を`WhenAll`を参照してください[する方法: Task.WhenAll (Visual Basic) を使用して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)です。  
  
 ここでは、次の例について説明します。  
  
-   [非同期タスクまたはタスク (Visual Basic) の一覧のキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)です。  
  
-   [非同期タスクのキャンセル後一定の時間 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [完了 (Visual Basic の場合) は、1 つ後の残りの非同期タスクのキャンセルします。](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [複数の非同期タスクし、プロセスの完了 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  この例を実行するには、コンピューターに Visual Studio 2012 以降および .NET Framework 4.5 以降がインストールされている必要があります。  
  
 次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。 ボタンの名前は `startButton` と `cancelButton` です。  
  
 ![[キャンセル] ボタンが表示された WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")  
  
 完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)」からダウンロードできます。  
  
## <a name="see-also"></a>関連項目  
 [Async および Await を使用した非同期プログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
