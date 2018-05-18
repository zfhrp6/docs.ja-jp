---
title: スレッド プール (C#)
ms.date: 07/20/2015
ms.assetid: 98ae68c1-ace8-44b9-9317-8920ac9ef2b6
ms.openlocfilehash: 42e1dcedc1897dc82bbd13f12882cbef6a5da4c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pooling-c"></a>スレッド プール (C#)
"*スレッド プール*" とは、複数のタスクをバックグラウンドで実行するときに使用できるスレッドのコレクションです  (詳細については、「[スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)」を参照してください)。これにより、プライマリ スレッドは他のタスクを非同期的に実行できます。  
  
 スレッド プールは、サーバー アプリケーションでよく使用されます。 受信した要求がそれぞれスレッド プールのスレッドに割り当てられるため、プライマリ スレッドを占有したり、後続の要求の処理を遅延させたりすることなく、非同期的に処理できます。  
  
 タスクを完了したプール内のスレッドは待機スレッドのキューに戻り、再利用できるようになります。 これにより、タスクごとに新しいスレッドを作成するという負荷がアプリケーションにかからなくなります。  
  
 スレッド プールには、通常、最大数のスレッドが含まれています。 すべてのスレッドがビジーの場合、追加のタスクは、スレッドが使用可能になってタスクを処理できるようになるまでキューに置かれます。  
  
 独自のスレッド プールを実装することもできますが、.NET Framework が <xref:System.Threading.ThreadPool> クラスを通じて提供するスレッド プールを使用する方が簡単です。  
  
 スレッド プールを使用する場合、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> メソッドを呼び出すときに実行対象のプロシージャのデリゲートを指定すると、C# によってスレッドが作成され、プロシージャが実行されます。  
  
## <a name="thread-pooling-example"></a>スレッド プールの例  
 次の例は、スレッド プールを使用して、タスクをいくつか開始する方法を示しています。  
  
```csharp  
public void DoWork()  
{  
    // Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(SomeLongTask));  
    // Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        new System.Threading.WaitCallback(AnotherLongTask));  
}  
  
private void SomeLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
  
private void AnotherLongTask(Object state)  
{  
    // Insert code to perform a long task.  
}  
```  
  
 スレッド プールのメリットの 1 つとして、引数を状態オブジェクトでタスク プロシージャに渡すことができます。 呼び出し先のプロシージャが複数の引数を必要とする場合は、構造体またはクラスのインスタンスを `Object` データ型にキャストできます。  
  
## <a name="thread-pool-parameters-and-return-values"></a>スレッド プールのパラメーターと戻り値  
 スレッド プールのスレッドから値が返る際は、直接返されるわけではありません。 スレッド プールのキューに追加できるプロシージャは `Sub` プロシージャだけのため、関数呼び出しから値を返すという標準的な方法が使用できません。 パラメーターと戻り値を提供する方法の 1 つとして、パラメーター、戻り値、メソッドをラッパー クラスにラップする方法があります。これについては、「[マルチスレッド プロシージャのパラメーターと戻り値 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)」を参照してください。  
  
 より簡単にパラメーターと戻り値を提供する方法として、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用できます。 この変数を使用して、クラスのインスタンスへの参照を渡すと、スレッド プールのスレッドでインスタンスのメンバーを変更し、これを戻り値として使用できます。  
  
 値によって渡される変数の参照先オブジェクトを変更できるということがわかりにくいかもしれません。 これが可能なのは、値によって渡されるのがオブジェクト参照のみであるためです。 オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、その変更が実際のクラス インスタンスに適用されます。  
  
 構造体を使用して、状態オブジェクト内の値を返すことはできません。 構造体は値型であるため、非同期プロセスで行われた変更によって元の構造体のメンバーが変更されることはありません。 構造体は、戻り値を必要としないときにパラメーターを提供するために使用します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [方法: スレッド プールを使用する (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)
