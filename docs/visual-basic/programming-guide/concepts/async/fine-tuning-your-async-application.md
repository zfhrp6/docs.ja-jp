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
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7d0cac2fe7305031b93a375a08e785285a291320
ms.lasthandoff: 03/13/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a>非同期アプリケーション (Visual Basic) の微調整
できる精度と柔軟性、非同期アプリケーションに使用して追加するメソッドとプロパティを<xref:System.Threading.Tasks.Task>型が使用できるようにします</xref:System.Threading.Tasks.Task>。 このセクションのトピックを使用する例を示して<xref:System.Threading.CancellationToken>重要な`Task`<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>および<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>などの方法</xref:System.Threading.CancellationToken>  
  
 `WhenAny` と `WhenAll` を使用すると、複数のタスクをより簡単に開始し、単一のタスクを監視して、その完了を待機できます。  
  
-   `WhenAny` は、コレクションのいずれかのタスクが完了すると完了するタスクを返します。  
  
     使用する例について`WhenAny`を参照してください[1 つの完了 (Visual Basic) の後に残りの非同期タスクのキャンセル](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)と[複数の同期タスクの開始、プロセスとして、完全な (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)します。  
  
-   `WhenAll` は、コレクションのすべてのタスクが完了すると完了するタスクを返します。  
  
     詳細については、使用する例を`WhenAll`を参照してください[する方法: Task.WhenAll を使用する」(Visual Basic の場合) して Asyncwalkthrough を拡張](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)します。  
  
 ここでは、次の例について説明します。  
  
-   [非同期タスクまたはタスク (Visual Basic) の一覧を取り消す](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)します。  
  
-   [経過時間 (Visual Basic) の非同期タスクをキャンセルします。](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [1 つは、(Visual Basic) の完了後の残りの非同期タスクのキャンセルします。](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [複数の同期タスクし、プロセスの完了 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 が必要または以降のコンピューターにインストールします。  
  
 次の図が示すように、プロジェクトは、プロセスを開始するボタンとそれを取り消すボタンを含む UI を作成します。 ボタンの名前は `startButton` と `cancelButton` です。  
  
 ![[キャンセル] ボタンを WPF ウィンドウ](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "キャンセル")  
  
 完全な Windows Presentation Foundation (WPF) プロジェクトをダウンロードする[Async サンプル: 細かいアプリケーションの調整](http://go.microsoft.com/fwlink/?LinkId=255046)します。  
  
## <a name="see-also"></a>関連項目  
 [非同期プログラミングを Async と Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
