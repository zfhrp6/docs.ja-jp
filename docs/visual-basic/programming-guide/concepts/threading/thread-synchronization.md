---
title: "スレッドの同期 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ec8fa89c8921eadee428a90971d9ae4ce305a109
ms.lasthandoff: 03/13/2017

---
# <a name="thread-synchronization-visual-basic"></a>スレッドの同期 (Visual Basic)
次のセクションでは、機能とマルチ スレッド アプリケーションのリソースへのアクセスを同期するために使用されるクラスについて説明します。  
  
 アプリケーションで複数のスレッドを使用する利点の&1; つは、各スレッドが非同期的に実行することです。 Windows アプリケーションは、これにより、アプリケーション ウィンドウの中にバック グラウンドで実行する時間のかかるタスクし、コントロールの応答性を維持します。 サーバーには、アプリケーション、マルチ スレッドは、別のスレッドで受信された各要求を処理する機能を提供します。 それ以外の場合、完全には満足できましたが、前回の要求まで新しい要求が処理されないとを取得します。  
  
 ただし、非同期の特質がファイル ハンドル、ネットワーク接続、およびメモリなどのリソースにアクセスするスレッドの場合は、調整する必要があります。 それ以外の場合、2 つまたは複数のスレッドは、同じリソースに同時に、それぞれの動作を認識しないアクセスでした。 予期しないデータの破損になります。  
  
 整数の数値データ型に対する単純な操作は、スレッドの同期で実現できる<xref:System.Threading.Interlocked>クラス</xref:System.Threading.Interlocked>のメンバー その他のすべてのデータ型および非スレッド セーフであるリソース、マルチ スレッドのみ安全に実行できますこのトピックの構成要素を使用します。  
  
 マルチ スレッド プログラミングの基礎知識についてを参照してください。  
  
-   [マネージ スレッド処理の基礎](http://msdn.microsoft.com/library/b2944911-0e8f-427d-a8bb-077550618935)  
  
-   [スレッドを使用して、スレッド処理](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)  
  
-   [マネージ スレッド処理のベスト プラクティス](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557)  
  
## <a name="the-lock-and-synclock-keywords"></a>ロックおよび SyncLock キーワード  
 Visual Basic`SyncLock`他のスレッドによって中断されることがなく完了するまでのコード ブロックが実行できるようにするステートメントを使用できます。 これは、コード ブロックの中から特定のオブジェクト相互排他ロックを取得することによって行います。  
  
 A`SyncLock`ステートメントが、引数としてオブジェクトが指定され、一度に&1; つのスレッドによって実行されるコード ブロックが続きます。 例:  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 渡される引数、`SyncLock`キーワードが参照型に基づくオブジェクトである必要があり、ロックのスコープを定義するために使用します。 上記の例で、ロックのスコープはこの関数に限定されているため、オブジェクトへの参照`lockThis`関数の外部に存在します。 このような参照が存在すると場合、そのオブジェクトにロックのスコープを拡張します。 厳密に言えば、指定されたオブジェクトは任意のクラス インスタンスにするために複数のスレッド間で共有されるリソースを一意に識別するためだけに使用します。 実際にこのオブジェクト通常は、スレッドの同期が必要なリソースです。 たとえば、コンテナー オブジェクトを複数のスレッドで使用する場合は、し、ロックするには、コンテナーを渡すことができ、ロックの後、同期されたコード ブロックは、コンテナーへのアクセスします。 上の他のスレッドをロックしている限り、アクセスする前に含む同じし、オブジェクトへのアクセスを安全に同期します。  
  
 一般をロックしないことをお勧め、`public`の種類や、アプリケーション処理の対象外のオブジェクト インスタンス。 たとえば、`lockThis`は問題となるインスタンスがパブリックにアクセスできる場合もオブジェクトにユーザーが制御できないコードがロックされることがあるためです。 これにより、デッドロックが&2; つまたは複数のスレッドが同じオブジェクトの解放を待機が作成する可能性があります。 オブジェクトではなく、パブリックなデータ型をロックすると、同じ理由で問題が発生することができます。 リテラル文字列はリテラル文字列のロックは特に危険*インターン*共通言語ランタイム (CLR) によってです。 つまり、すべての文字列の&1; つのインスタンスがあるプログラム全体のリテラル、まったく同じオブジェクトがすべてのリテラルを表すすべてのスレッドでアプリケーション ドメインを実行します。 その結果をロックと同じ内容の文字列に任意の場所アプリケーション プロセスのロックのアプリケーションでは、その文字列のすべてのインスタンス。 その結果、隔離されていないプライベートまたはプロテクト メンバーをロックすることをお勧めします。 一部のクラスは、ロック専用のメンバーを提供します。 <xref:System.Array>型、たとえばに<xref:System.Array.SyncRoot%2A>。</xref:System.Array.SyncRoot%2A>が用意されています</xref:System.Array> 多くのコレクション型には、`SyncRoot`メンバーもします。  
  
 詳細については、`SyncLock`ステートメントでは、次のトピックを参照してください。  
  
-   [SyncLock ステートメント](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a>モニター  
 ように、`SyncLock`キーワード、モニターは、複数のスレッドが同時に実行からのコード ブロックを防ぐためです。 <xref:System.Threading.Monitor.Enter%2A>メソッドを使用して、次のステートメントに続行する、1 つのスレッドは実行中のスレッドが<xref:System.Threading.Monitor.Exit%2A>。</xref:System.Threading.Monitor.Exit%2A>を呼び出すまで、他のすべてのスレッドがブロックされます。</xref:System.Threading.Monitor.Enter%2A> これを使用するよう、`SyncLock`キーワードです。 例:  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 これと同じです。  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 使用して、`SyncLock`を使用するキーワードは、通常の優先、<xref:System.Threading.Monitor>クラスを直接両方ため`SyncLock`はより簡潔なので、`SyncLock`基になっているモニターが離されたことを保証する場合でも、保護されているコードが例外をスローします</xref:System.Threading.Monitor>。 これを行うと、`Finally`キーワードで、例外をスローするかどうかに関係なく、関連するコード ブロックを実行します。  
  
## <a name="synchronization-events-and-wait-handles"></a>同期イベントと待機ハンドル  
 ロックまたはモニターの使用は、コードのスレッドに依存したブロックを同時に実行を防止するために役立ちますが、これらの構成要素には、1 つのスレッドにイベントを別の通信にはできません。 これが必要です*同期イベント*、これは、2 つの状態の&1; つを持つオブジェクトをアクティブ化し、スレッドを中断に使用するシグナルと非シグナル状態であります。 スレッドは、シグナル、同期イベントを待機させることによって中断されることができますあり、イベントの状態をシグナル状態に変更することによってアクティブ化されることができます。 スレッドは、イベントがシグナルを待機しようとする場合は、遅延なしに実行、スレッドが続行します。  
  
 同期イベントの&2; つの種類があります: <xref:System.Threading.AutoResetEvent>、 <xref:System.Threading.ManualResetEvent>.</xref:System.Threading.ManualResetEvent> </xref:System.Threading.AutoResetEvent> のみが異なりますを<xref:System.Threading.AutoResetEvent>から変更シグナル状態にシグナルを自動的に時間がいずれかのスレッドがアクティブになります</xref:System.Threading.AutoResetEvent>。 逆に、<xref:System.Threading.ManualResetEvent>のシグナルの状態によってアクティブ化するスレッドの任意の数を使用し、シグナルに戻りますのみ状態のときにその<xref:System.Threading.EventWaitHandle.Reset%2A>メソッドが呼び出されます</xref:System.Threading.EventWaitHandle.Reset%2A></xref:System.Threading.ManualResetEvent>。  
  
 待機メソッドの&1; つを呼び出してなどのイベントを待機するスレッドができる<xref:System.Threading.WaitHandle.WaitOne%2A>、 <xref:System.Threading.WaitHandle.WaitAny%2A>、または<xref:System.Threading.WaitHandle.WaitAll%2A>.</xref:System.Threading.WaitHandle.WaitAll%2A> </xref:System.Threading.WaitHandle.WaitAny%2A> </xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>1 つのイベントがシグナル状態になるまで待機するスレッド<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>1 つ以上の指定されたイベントがシグナル状態になるまで、スレッドをブロックし、<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>すべて指定されたイベントのシグナル状態になるまで、スレッドをブロックします</xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName></xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>。</xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> イベントがシグナル状態とその<xref:System.Threading.EventWaitHandle.Set%2A>メソッドが呼び出されます</xref:System.Threading.EventWaitHandle.Set%2A>。  
  
 スレッドの作成および開始で次の例では、`Main`関数です。 イベントを使用して、新しいスレッドが待機する、<xref:System.Threading.WaitHandle.WaitOne%2A>メソッド</xref:System.Threading.WaitHandle.WaitOne%2A>。 実行しているプライマリ スレッドによってイベントがシグナル状態になるまでスレッドが中断、`Main`関数です。 補助的なスレッドが戻るイベントがシグナル状態になります。 この場合、イベントがのみ使用されるための&1; つのスレッドのアクティブ化するか、<xref:System.Threading.AutoResetEvent>または<xref:System.Threading.ManualResetEvent>クラスを使用できます</xref:System.Threading.ManualResetEvent></xref:System.Threading.AutoResetEvent>。  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
```  
  
## <a name="mutex-object"></a>ミュー テックス オブジェクト  
 A*ミュー テックス*モニターのようなことにより、コードのブロックを同時に実行スレッドは&1; つ以上の一度にします。 実際には、「相互に排他的です」という用語の短縮形は、名前「ミュー テックス」 モニターとは異なり、ミュー テックスできますプロセス間でスレッドを同期します。 ミュー テックスが<xref:System.Threading.Mutex>クラス</xref:System.Threading.Mutex>によって表される  
  
 ミュー テックスと呼ばれるプロセス間の同期に使用する場合、*名前付きミュー テックス*別のアプリケーションで使用するのには、グローバルまたは静的変数を使用ため共有することはできません。 これは、必要があります名前を指定する両方のアプリケーションが同じミュー テックス オブジェクトにアクセスできるようにします。  
  
 使用して、ミュー テックスを使用して、プロセス間のスレッドの同期化できますが、<xref:System.Threading.Monitor>が一般に推奨されるモニターが向けに .NET Framework とはそのためのリソースを活用して行っています</xref:System.Threading.Monitor>。 これに対し、<xref:System.Threading.Mutex>クラスは、Win32 コンストラクトにラッパー</xref:System.Threading.Mutex> 。 ミュー テックスがより負荷の大きい<xref:System.Threading.Monitor>クラス</xref:System.Threading.Monitor>で必要なものである相互運用機能の遷移を必要とモニターよりも強力ですが、 ミュー テックスを使用しての例は、次を参照してください。[ミュー テックス](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)します。  
  
## <a name="interlocked-class"></a>Interlocked クラス  
 メソッドを使用する、<xref:System.Threading.Interlocked>複数のスレッドが同時に更新または同じ値と比較を試みるときに発生する問題を防止するクラス</xref:System.Threading.Interlocked>。 このクラスのメソッドを使用する安全なインクリメント、デクリメント、交換、および任意のスレッドからの値を比較します。  
  
## <a name="readerwriter-locks"></a>ReaderWriter ロック  
 場合によっては、データが書き込まれている場合にのみ、リソースをロックし、複数のクライアントにデータが更新されていないときにデータの同時読み取りを許可するのにすることがあります。 <xref:System.Threading.ReaderWriterLock>クラスは、スレッドが、リソースを変更するは、リソースの読み取り時に非排他的なアクセスが許可されているときに、リソースへの排他アクセスを強制します</xref:System.Threading.ReaderWriterLock>。 ReaderWriter ロックは、待機もとそれらのスレッドする必要はありませんデータを更新するには、他のスレッド排他ロックの代わりにします。  
  
## <a name="deadlocks"></a>デッドロック  
 スレッドの同期はマルチ スレッド アプリケーションで役に立つが、常に作成する危険性がある、 `deadlock`」複数のスレッドが互いを待機しているし、アプリケーションが停止するものです。 デッドロックは、車が&4; 方向の位置で停止されたして移動するその他の各ユーザーが待機しているのと似ています。 デッドロックを避けることが重要です。綿密な計画が重要です。 多くの場合、コーディングを開始する前に、マルチ スレッド アプリケーションを図式化でデッドロックが発生を予測できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread></xref:System.Threading.Thread>   
 <xref:System.Threading.WaitHandle.WaitOne%2A></xref:System.Threading.WaitHandle.WaitOne%2A>   
 <xref:System.Threading.WaitHandle.WaitAny%2A></xref:System.Threading.WaitHandle.WaitAny%2A>   
 <xref:System.Threading.WaitHandle.WaitAll%2A></xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.Thread.Join%2A></xref:System.Threading.Thread.Join%2A>   
 <xref:System.Threading.Thread.Start%2A></xref:System.Threading.Thread.Start%2A>   
 <xref:System.Threading.Thread.Sleep%2A></xref:System.Threading.Thread.Sleep%2A>   
 <xref:System.Threading.Monitor></xref:System.Threading.Monitor>   
 <xref:System.Threading.Mutex></xref:System.Threading.Mutex>   
 <xref:System.Threading.AutoResetEvent></xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent></xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Interlocked></xref:System.Threading.Interlocked>   
 <xref:System.Threading.WaitHandle></xref:System.Threading.WaitHandle>   
 <xref:System.Threading.EventWaitHandle></xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading></xref:System.Threading>   
 <xref:System.Threading.EventWaitHandle.Set%2A></xref:System.Threading.EventWaitHandle.Set%2A>   
 [マルチ スレッド アプリケーション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [SyncLock ステートメント](../../../../visual-basic/language-reference/statements/synclock-statement.md)   
 [ミュー テックス](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)   
 @System.Threading.Monitor   
 [インタロックされた操作](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [データを同期するマルチ スレッド](http://msdn.microsoft.com/library/b980eb4c-71d5-4860-864a-6dfe3692430a)
