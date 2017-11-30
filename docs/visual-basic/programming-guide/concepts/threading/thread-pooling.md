---
title: "スレッド プール (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a>スレッド プール (Visual Basic)
"*スレッド プール*" とは、複数のタスクをバックグラウンドで実行するときに使用できるスレッドのコレクションです  (を参照してください[スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景情報についてはします)。これにより、プライマリ スレッドは他のタスクを非同期的に実行できます。  
  
 スレッド プールは、サーバー アプリケーションでよく使用されます。 受信した要求がそれぞれスレッド プールのスレッドに割り当てられるため、プライマリ スレッドを占有したり、後続の要求の処理を遅延させたりすることなく、非同期的に処理できます。  
  
 タスクを完了したプール内のスレッドは待機スレッドのキューに戻り、再利用できるようになります。 これにより、タスクごとに新しいスレッドを作成するという負荷がアプリケーションにかからなくなります。  
  
 スレッド プールには、通常、最大数のスレッドが含まれています。 すべてのスレッドがビジーの場合、追加のタスクは、スレッドが使用可能になってタスクを処理できるようになるまでキューに置かれます。  
  
 独自のスレッド プールを実装することもできますが、.NET Framework が <xref:System.Threading.ThreadPool> クラスを通じて提供するスレッド プールを使用する方が簡単です。  
  
 スレッド プールでを呼び出す、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>を実行する手順については、デリゲートにメソッドおよび Visual Basic、スレッドを作成して、プロシージャを実行します。  
  
## <a name="thread-pooling-example"></a>スレッド プールの例  
 次の例は、スレッド プールを使用して、タスクをいくつか開始する方法を示しています。  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 スレッド プールのメリットの 1 つとして、引数を状態オブジェクトでタスク プロシージャに渡すことができます。 呼び出し先のプロシージャが複数の引数を必要とする場合は、構造体またはクラスのインスタンスを `Object` データ型にキャストできます。  
  
## <a name="thread-pool-parameters-and-return-values"></a>スレッド プールのパラメーターと戻り値  
 スレッド プールのスレッドから値が返る際は、直接返されるわけではありません。 スレッド プールのキューに追加できるプロシージャは `Sub` プロシージャだけのため、関数呼び出しから値を返すという標準的な方法が使用できません。 一方向のパラメーターを指定してパラメーター、戻り値の値をラップすることによって値があり、メソッドのラッパー内で説明されているクラスを返す[パラメーターとマルチ スレッド プロシージャ (Visual Basic) の値を返す](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)です。  
  
 より簡単にパラメーターと戻り値を提供する方法として、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用できます。 この変数を使用して、クラスのインスタンスへの参照を渡すと、スレッド プールのスレッドでインスタンスのメンバーを変更し、これを戻り値として使用できます。  
  
 値によって渡される変数の参照先オブジェクトを変更できるということがわかりにくいかもしれません。 これが可能なのは、値によって渡されるのがオブジェクト参照のみであるためです。 オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、その変更が実際のクラス インスタンスに適用されます。  
  
 構造体を使用して、状態オブジェクト内の値を返すことはできません。 構造体は値型であるため、非同期プロセスで行われた変更によって元の構造体のメンバーが変更されることはありません。 構造体は、戻り値を必要としないときにパラメーターを提供するために使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [方法: スレッド プールを使用する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [マルチスレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
