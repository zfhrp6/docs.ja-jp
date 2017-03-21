---
title: "スレッド プール (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6037d7ea17e260d44bae571aa25d413996f5a123
ms.lasthandoff: 03/13/2017

---
# <a name="thread-pooling-visual-basic"></a>スレッド プール (Visual Basic)
A*スレッド プール*をバック グラウンドでいくつかのタスクを実行するために使用できるスレッドのコレクションです。 (を参照してください[スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)背景情報です)。これにより、プライマリ スレッドを自由に他のタスクを非同期的に実行します。  
  
 スレッド プールは、サーバー アプリケーションで多く採用されています。 受信された各要求は、プライマリ スレッドを停止したり、後続の要求の処理を遅らせることがなく、要求が、非同期的に処理できるように、スレッド プールからスレッドに割り当てられます。  
  
 プール内のスレッドには、そのタスクが完了すると、待機中のスレッドのキューに返される、使用できます。 この再利用により、タスクごとに新しいスレッドを作成するコストを回避できます。  
  
 スレッド プールには、通常、スレッドの最大数があります。 すべてのスレッドがビジーである場合、その他のタスクは、スレッドが公開されたらすぐに処理できるようになるまでキューに置かれます。  
  
 独自のスレッド プールを実装することができますが、<xref:System.Threading.ThreadPool>クラス</xref:System.Threading.ThreadPool>を .NET Framework で提供されるスレッド プールを使用する方が簡単  
  
 呼び出すスレッドがプールを使用した、 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>、実行する手順については、デリゲートを使用してメソッド、および Visual Basic、スレッドを作成して、プロシージャを実行します</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=fullName>。  
  
## <a name="thread-pooling-example"></a>スレッド プールの例  
 次の例では、いくつかのタスクを開始するプールのスレッドを使用する方法を示します。  
  
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
  
 スレッド プールの利点の&1; つは、引数、タスクの手順に状態のオブジェクトに渡すことができます。 呼び出しているプロシージャは、1 つ以上の引数を必要とする場合は、構造体またはにクラスのインスタンスをキャストすることができます、`Object`データ型。  
  
## <a name="thread-pool-parameters-and-return-values"></a>スレッド プールのパラメーターと戻り値  
 スレッド プールのスレッドからの戻り値は、簡単ではありません。 関数呼び出しからの戻り値の標準的な方法は許可されません`Sub`プロシージャは、スレッド プールにキューに配置するプロシージャの唯一の種類。 一方向のパラメーターを指定し、切断したパラメーター、戻り値をラップすることによって値があり、メソッドのラッパー内クラス」の説明に従って[パラメーターとマルチ スレッド プロシージャ (Visual Basic) の値を返す](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)します。  
  
 容易パラメーターを指定して、戻り値は省略可能なを使用して`ByVal`の状態のオブジェクト変数、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>メソッド</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>。 クラスのインスタンスへの参照を渡すためにこの変数を使用する場合は、インスタンスのメンバーをスレッド プールのスレッドによって変更され、戻り値として使用します。  
  
 最初に、わかりにくいかもしれません値によって渡される変数が参照するオブジェクトを変更することができます。 オブジェクトの参照だけが値によって渡されるために、これを行うことができます。 オブジェクト参照によって参照されるオブジェクトのメンバーに変更を加えると、変更は、実際のクラスのインスタンスに適用されます。  
  
 構造体は、状態オブジェクトの中の値を返すには使用できません。 構造体は値型であるために、非同期プロセスによって加えられる変更は元の構造体のメンバーも変わりません。 構造体を使用すると、戻り値が不要なときに、パラメーターを提供します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.ThreadPool></xref:System.Threading.ThreadPool>   
 [方法: スレッド プール (Visual Basic) を使用します。](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)   
 [スレッド処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md)   
 [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [スレッドの同期 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
