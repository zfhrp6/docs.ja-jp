---
title: "非同期アプリケーションの微調整 (C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 74cab732debe2381cbd3b9106b2431e2490ef57e
ms.lasthandoff: 03/13/2017

---
# <a name="fine-tuning-your-async-application-c"></a>非同期アプリケーションの微調整 (C#)
<xref:System.Threading.Tasks.Task> 型を使用できるメソッドとプロパティを使って、非同期アプリケーションに精度と柔軟性を追加できます。 このセクションのトピックでは、<xref:System.Threading.CancellationToken> と、<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> や <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> などの重要な `Task` メソッドを使う例を示します。  
  
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
  
 完全な Windows Presentation Foundation (WPF) プロジェクトは、「[Async Sample: Fine Tuning Your Application (非同期のサンプル: アプリケーションの微調整)](http://go.microsoft.com/fwlink/?LinkId=255046)」からダウンロードできます。  
  
## <a name="see-also"></a>関連項目  
 [Async および Await を使用した非同期プログラミング (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
