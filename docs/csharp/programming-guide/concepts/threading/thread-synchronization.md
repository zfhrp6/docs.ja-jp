---
title: "スレッドの同期 (C#)"
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
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
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
ms.openlocfilehash: df4093d4bf777f904aa8ce376cd164ed822350a0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="thread-synchronization-c"></a>スレッドの同期 (C#)
次のセクションでは、マルチスレッド アプリケーションでリソースへのアクセスを同期するために使用できる機能とクラスについて説明します。  
  
 アプリケーションで複数のスレッドを使用する利点の 1 つは、各スレッドを非同期的に実行できる点にあります。 Windows アプリケーションでは、これによって、アプリケーションのウィンドウやコントロールを応答可能な状態に維持しつつ、時間のかかるタスクをバックグラウンドで実行することができます。 サーバー アプリケーションでは、マルチスレッドを使用することで、受け取った各要求を別個のスレッドで処理できるようになります。 マルチスレッドを使用しない場合、前の要求が完全に満たされるまで、新しい要求はサービスを受けることができません。  
  
 ただし、スレッドでの処理が非同期であるために、ファイル ハンドル、ネットワーク接続、およびメモリなどのリソースへのアクセスを調整する必要が生じます。 調整が行われないと、互いに別のスレッドの動作が認識できず、複数のスレッドが同時に同じリソースにアクセスしてしまうことになります。 その結果、予測できないデータ破損が発生します。  
  
 整数の数値データ型に対する単純な演算の場合は、<xref:System.Threading.Interlocked> クラスのメンバーを使用することにより、スレッドの同期を実現できます。 その他のすべてのデータ型やスレッド セーフではないリソースについては、このトピックで説明する構成要素を使用しない限り、マルチスレッド処理を安全に実行することはできません。  
  
 マルチスレッド プログラミングの背景情報については、以下を参照してください。  
  
-   [マネージ スレッド処理の基本](../../../../standard/threading/managed-threading-basics.md)  
  
-   [スレッドの使用とスレッド処理](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [マネージ スレッド処理の実施](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>lock キーワード  
 C# `lock` ステートメントを使用すると、他のスレッドからの割り込みを受けることなくコード ブロックを確実に最後まで実行できます。 これは、コード ブロックの実行中に、特定のオブジェクトに対して同時に使用できないロックを取得することで実現されます。  
  
 `lock` ステートメントには引数としてオブジェクトが渡され、その後に、一度に 1 つのスレッドだけが実行するコード ブロックが続きます。 例:  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 `lock` キーワードに渡される引数は、参照型に基づくオブジェクトである必要があり、ロックのスコープを定義するために使用されます。 前の例では、関数の外部にオブジェクト `lockThis` への参照が存在しないため、ロックのスコープはこの関数に限定されます。 この参照が存在していたら、ロックのスコープはそのオブジェクトまで拡張されていました。 厳密には、渡されるオブジェクトは、複数のスレッドで共有されるリソースを一意に識別するためだけに使用されるので、任意のクラスのインスタンスを使用できます。 ただし、実際には、このオブジェクトは、スレッドの同期が必要なリソースを表すのが普通です。 たとえば、複数のスレッドがコンテナー オブジェクトを使用する場合、そのコンテナーを lock に渡すと、lock に続く、同期されたコード ブロックがそのコンテナーにアクセスできるようになります。 他のスレッドが同じコンテナーにアクセスする前にコンテナーをロックすると、このオブジェクトへのアクセスを安全に同期できます。  
  
 一般に、`public` 型や、アプリケーションの制御が及ばないオブジェクト インスタンスはロックしないことをお勧めします。 たとえば、インスタンスにパブリックにアクセスできる場合、`lock(this)` は問題となることがあります。ユーザーの制御が及ばないコードによってもこのオブジェクトがロックされる可能性があるからです。 この場合、複数のスレッドが同じオブジェクトの解放を待機しているような場合にはデッドロック状態が発生することがあります。 オブジェクトではなく、パブリックなデータ型をロックした場合も同じ理由から問題が生じることがあります。 リテラル文字列は共通言語ランタイム (CLR) の*インターン プールに存在*しているため、リテラル文字列をロックすることは特に危険です。 つまり、プログラム全体では任意のリテラル文字列のインスタンスは 1 つしか存在しませんが、まったく同じオブジェクトが、実行中のすべてのアプリケーション ドメインのすべてのスレッド上のリテラルを表すためです。 この結果、アプリケーション プロセスの任意の場所で同じ内容を持つ文字列をロックした場合、アプリケーション内のその文字列のすべてのインスタンスがロックされてしまいます。 したがって、インターン プールに存在しないプライベート メンバーまたはプロテクト メンバーをロックすることをお勧めします。 クラスによっては、ロック専用のメンバーを提供するものもあります。 たとえば、<xref:System.Array> 型では <xref:System.Array.SyncRoot%2A> が提供されます。 多くのコレクション型でも、`SyncRoot` メンバーが提供されます。  
  
 `lock` ステートメントの詳細については、次のトピックを参照してください。  
  
-   [lock ステートメント](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   @System.Threading.Monitor  
  
## <a name="monitors"></a>モニター  
 `lock` キーワードと同様、モニターも複数のスレッドによるコード ブロックの同時実行を防ぎます。 <xref:System.Threading.Monitor.Enter%2A> メソッドは 1 つのスレッドにのみ後続のステートメントに進むことを許可します。他のすべてのスレッドは、実行中のスレッドが <xref:System.Threading.Monitor.Exit%2A> を呼び出すまでブロックされます。 これは `lock` キーワードを使用した場合とまったく同じ結果になります。 例:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 このようにすると、次の記述と同じ結果が得られます。  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 通常は、<xref:System.Threading.Monitor> クラスを直接使用するよりも `lock` キーワードを使用することをお勧めします。`lock` の方が簡潔であり、また、`lock` を使用すると、保護されたコードが例外をスローした場合でも基になるモニターが確実に解放されるためです。 モニターを確実に解放するには、`finally` キーワードを使用します。このキーワードを使用することにより、例外がスローされたかどうかに関係なく、関連付けられているコード ブロックが実行されます。  
  
## <a name="synchronization-events-and-wait-handles"></a>同期イベントと待機ハンドル  
 スレッド依存のコード ブロックが同時に実行されないようにするためにロックやモニターを使用することは有効ですが、このような構成要素だけでは、スレッド間でイベントをやりとりすることはできません。 そこで、*同期イベント*が必要になります。これは、シグナル状態と非シグナル状態という 2 つの状態を持つオブジェクトで、これを使用することにより、スレッドをアクティブにしたり中断したりできます。 非シグナル状態の同期イベントを待機させることによってスレッドを中断できます。また、イベントの状態をシグナル状態に変更することにより、スレッドをアクティブにできます。 既にシグナル状態にあるイベントをスレッドが待機している場合、スレッドは遅延なしに実行され続けます。  
  
 同期イベントには、<xref:System.Threading.AutoResetEvent> と <xref:System.Threading.ManualResetEvent> の 2 種類があります。 この 2 つで唯一違うのは、<xref:System.Threading.AutoResetEvent> の場合、1 つのスレッドをアクティブにするたびに自動的にシグナル状態から非シグナル状態に変わるという点です。 逆に <xref:System.Threading.ManualResetEvent> では、そのシグナル状態で任意の数のスレッドをアクティブにでき、<xref:System.Threading.EventWaitHandle.Reset%2A> メソッドが呼び出された場合にのみ、非シグナル状態に戻ります。  
  
 <xref:System.Threading.WaitHandle.WaitOne%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A>、<xref:System.Threading.WaitHandle.WaitAll%2A> などの待機メソッドのいずれかを呼び出すことによって、スレッドにイベントを待機させることができます。 <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> は、単一のイベントがシグナル状態になるまでスレッドを待機させます。<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> は、指定した 1 つ以上のイベントがシグナル状態になるまでスレッドをブロックします。<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> は、指定したすべてのイベントがシグナル状態になるまでスレッドをブロックします。 イベントは、その <xref:System.Threading.EventWaitHandle.Set%2A> メソッドが呼び出されると、シグナル状態になります。  
  
 次の例では、`Main` 関数によってスレッドが作成され開始されます。 新しいスレッドは <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを使用してイベントを待機します。 このスレッドは、`Main` 関数を実行しているプライマリ スレッドによってイベントがシグナル状態になるまで中断されます。 イベントがシグナル状態になると、この補助スレッドに制御が戻ります。 この場合は 1 つのスレッドだけをアクティブにするためにイベントを使用しているので、<xref:System.Threading.AutoResetEvent> クラスまたは <xref:System.Threading.ManualResetEvent> クラスのいずれも使用できます。  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>ミューテックス オブジェクト  
 *ミューテックス*は、複数のスレッドによってコード ブロックが同時に実行されるのを防ぐという点でモニターに似ています。 実際、"mutex (ミューテックス)" という名前は、"mutually exclusive (相互に排他的)" という用語の短縮形です。 ただし、モニターとは違って、ミューテックスを使用するとプロセス間でスレッドを同期できます。 ミューテックスは、<xref:System.Threading.Mutex> クラスで表されます。  
  
 プロセス間の同期に使用されるミューテックスは、*名前付きミューテックス*と呼ばれます。このようなミューテックスは別のアプリケーションで使用される可能性があるため、グローバル変数や静的変数を使用して共有できないからです。 したがって、両方のアプリケーションから同じミューテックス オブジェクトにアクセスできるように、名前を付ける必要があります。  
  
 ミューテックスを使用するとプロセス間でスレッドを同期できますが、通常は <xref:System.Threading.Monitor> の使用をお勧めします。その理由は、モニターが .NET Framework 専用にデザインされているため、より適切にリソースを利用できる点にあります。 一方、<xref:System.Threading.Mutex> クラスは Win32 の構成要素のラッパーです。 ミューテックスはモニターよりも強力ですが、<xref:System.Threading.Monitor> クラスよりも相互運用機能の遷移に必要な計算上の負荷が大きくなってしまいます。 ミューテックスの使用例については、「[ミューテックス](../../../../standard/threading/mutexes.md)」を参照してください。  
  
## <a name="interlocked-class"></a>Interlocked クラス  
 <xref:System.Threading.Interlocked> クラスのメソッドを使用すると、複数のスレッドが同じ値を同時に更新または比較しようとしたときに発生する可能性のある問題を回避できます。 このクラスのメソッドによって、どのスレッドの値も安全にインクリメント、デクリメント、交換、比較することができます。  
  
## <a name="readerwriter-locks"></a>ReaderWriter ロック  
 場合によっては、データを書き込むときだけリソースをロックし、データが更新されないときには複数のクライアントにデータの同時読み取りを許可することがあります。 <xref:System.Threading.ReaderWriterLock> クラスを使用すると、スレッドがリソースを変更する間はリソースに排他アクセスを適用し、リソースを読み取るときには排他的でないアクセスを許可できます。 ReaderWriter ロックは、データの更新が必要ないときでも、他のスレッドを待機させる方法として、排他ロックに代わる有効な手段です。  
  
## <a name="deadlocks"></a>デッドロック  
 スレッドの同期は、マルチスレッド アプリケーションにとって非常に大切ですが、`deadlock` を生じさせてしまう危険性が常にあります。つまり、複数のスレッドが互いに待機しあって、アプリケーションが中断してしまう状態になります。 デッドロックは、たとえるなら四方向が一時停止の交差点で停止した車どうしが、相手の車を先に行かせるよう互いに譲り合い、誰もが動けなくなっている状態に似ています。 デッドロックを防ぐことは重要です。その鍵となるのは、綿密なプランです。 コーディングを始める前にマルチスレッド アプリケーションを図式化すると、デッドロック状態を予想できることがよくあります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.WaitHandle.WaitOne%2A>   
 <xref:System.Threading.WaitHandle.WaitAny%2A>   
 <xref:System.Threading.WaitHandle.WaitAll%2A>   
 <xref:System.Threading.Thread.Join%2A>   
 <xref:System.Threading.Thread.Start%2A>   
 <xref:System.Threading.Thread.Sleep%2A>   
 <xref:System.Threading.Monitor>   
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Interlocked>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading>   
 <xref:System.Threading.EventWaitHandle.Set%2A>   
 [マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [lock ステートメント](../../../../csharp/language-reference/keywords/lock-statement.md)   
 [ミューテックス](../../../../standard/threading/mutexes.md)   
 @System.Threading.Monitor   
 [インタロックされた操作](../../../../standard/threading/interlocked-operations.md)   
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)   
 [マルチスレッド処理のためのデータの同期](../../../../standard/threading/synchronizing-data-for-multithreading.md)

