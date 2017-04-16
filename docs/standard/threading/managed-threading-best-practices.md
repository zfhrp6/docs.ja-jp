---
title: "Managed Threading Best Practices | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], design guidelines"
  - "threading [.NET Framework], best practices"
  - "managed threading"
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading Best Practices
マルチスレッドには慎重なプログラミングが必要です。  ほとんどのタスクでは、スレッド プールのスレッドを使って実行の要求をキューに置くことによって、処理の複雑さを軽減できます。  このトピックでは、マルチ スレッド動作の調整や、ブロックするスレッドの処理など、より難しい状況について説明します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、マルチスレッド プログラミングの複雑さとリスクを軽減する API が Task Parallel Library および PLINQ に用意されています。  詳細については、「[Parallel Programming](../../../docs/standard/parallel-programming/index.md)」を参照してください。  
  
## デッドロックと競合状態  
 マルチスレッドはスループットと応答速度の問題を解決しますが、その一方で、デッドロックと競合状態という新たな問題を発生させます。  
  
### デッドロック  
 デッドロックは、2 つのスレッドのうちの一方が、もう一方によって既にロックされているリソースをロックしようとすると発生します。  こうなると、どちらのスレッドも続行できなくなります。  
  
 マネージ スレッド処理クラスの多くのメソッドには、ロックアウトを検出するためのタイムアウト機能が用意されています。  たとえば、現在のインスタンスへのロックの取得を試みるコードを次に示します。  ロックが 300 ミリ秒の間に得られない場合は、<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=fullName> は **false** を返します。  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(Me)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(this);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### 競合状態  
 競合状態は、2 つ以上のスレッドのうちのどれが特定のコード ブロックに最初に到達するかによって、プログラムの結果が変わってしまうバグのことです。  プログラムを何回か実行すると、異なる結果が得られ、実行の結果は予測できません。  
  
 競合状態の簡単な例として、フィールドのインクリメントがあります。  クラスにプライベートの **static** フィールド \(Visual Basic では **Shared**\) があり、このフィールドは、`objCt++;` \(C\# の場合\) または `objCt += 1` \(Visual Basic の場合\) のようなコードを使用して、クラスのインスタンスが生成されるたびにインクリメントされるものとします。  この演算によって、`objCt` からレジスタへの値の読み込み、値のインクリメント、および `objCt` への値の格納が行われます。  
  
 マルチスレッドされたアプリケーションでは、値の読み込みとインクリメントを行ったスレッドが、この 3 つの処理を実行する別のスレッドに先を越される可能性があります。最初のスレッドは、実行を再開して値を格納するとき、待機中に値が変更されたかどうかを考慮せずに、`objCt` の値を上書きしてしまいます。  
  
 このような特定の競合状態は、<xref:System.Threading.Interlocked.Increment%2A?displayProperty=fullName> など、<xref:System.Threading.Interlocked> クラスのメソッドを使用することによって容易に回避できます。  複数のスレッド間でデータを同期する他の手法については、「[マルチスレッド処理のためのデータの同期](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)」を参照してください。  
  
 競合状態は、複数のスレッドの動作を同期するときにも発生します。  コードを記述するときには、そのコードの行 \(または行を構成する各マシン命令\) を実行するスレッドが別のスレッドに追い越された場合に何が起きるのかを考慮しておく必要があります。  
  
## プロセッサの数  
 ほとんどのコンピューターは、タブレットや携帯電話のような小型のデバイスでさえも、複数のプロセッサ \(コアともいいます\) を持ちます。  シングル プロセッサ コンピューターでも動作するソフトウェアを開発する場合は、マルチスレッドによってシングル プロセッサ コンピューターとマルチプロセッサ コンピューターとで異なる問題が解決される点に注意してください。  
  
### マルチプロセッサ コンピューター  
 マルチスレッドによって、スループットが大幅に向上します。  10 個のプロセッサは 1 個のプロセッサの 10 倍の仕事をします。ただし、これは仕事が分割され、10 個のプロセッサが同時に働いた場合です。スレッドを使用すると、簡単な方法で仕事を分割し、プロセッサの能力を活用できます。  マルチプロセッサ コンピューターでマルチスレッドを使用する場合は、次の点に注意が必要です。  
  
-   同時に実行できるスレッドの数は、プロセッサの数によって制限されます。  
  
-   実行されているフォアグラウンド スレッドの数がプロセッサの数よりも少ないときだけ、バックグラウンド スレッドが実行されます。  
  
-   スレッドで <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> メソッドを呼び出しても、プロセッサの数と待機中のスレッドの数によっては、スレッドがすぐに開始されない場合があります。  
  
-   競合状態は、別のスレッドによる予期していなかった割り込みがあった場合に発生するだけでなく、別々のプロセッサで実行されている 2 つのスレッドが特定のコード ブロックに到達するタイミングによって発生する場合もあります。  
  
### シングル プロセッサ コンピューター  
 マルチスレッドによって、ユーザーへの応答速度が向上し、アイドル時間はバックグランド タスクに使用されます。  シングル プロセッサ コンピューターでマルチスレッドを使用するときは、次の点に注意が必要です。  
  
-   各瞬間には、1 つのスレッドだけが実行されています。  
  
-   バックグラウンド スレッドは、メイン ユーザー スレッドがアイドル状態のときだけ実行されます。  フォアグラウンド スレッドが連続して実行されると、バックグラウンド スレッドのプロセッサ時間が少なくなります。  
  
-   スレッドで <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> メソッドを呼び出しても、現在実行中のスレッドがプロセッサを解放するか、オペレーティング システムによって割り込まれるまでは、スレッドの実行が開始されません。  
  
-   スレッドが別のスレッドに割り込まれてしまい、特定のコード ブロックに先に到達されてしまう可能性をプログラマが予測できていない場合に、競合状態が発生しやすくなります。  
  
## 静的メンバーと静的コンストラクター  
 クラスは、そのクラス コンストラクター \(C\# では `static` コンストラクター、Visual Basic では `Shared Sub New`\) の実行が完了するまで初期化されません。  初期化されていない型のコードの実行を防止するため、共通言語ランタイムは、クラス コンストラクターの実行が完了するまで、他のスレッドからのそのクラスの `static` メンバー \(Visual Basic では `Shared` メンバー\) 呼び出しをすべてブロックします。  
  
 たとえば、クラス コンストラクターが新しいスレッドを起動し、そのスレッドのプロシージャがクラスの `static` メンバーを呼び出した場合、その新しいスレッドは、クラス コンストラクターが完了するまでブロックされます。  
  
 このことは、`static` コンストラクターを持つことができるすべての型に当てはまります。  
  
## 一般的な推奨事項  
 マルチスレッドを使用するときは、以下のガイドラインを考慮してください。  
  
-   他のスレッドを終了させるために <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> を使用することは避けてください。  他のスレッドの **Abort** を呼び出すことは、そのスレッドの処理がどこまで到達しているかを把握せずに例外をスローするのと同じことになります。  
  
-   <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Resume%2A?displayProperty=fullName> を使用して複数のスレッドの動作を同期することは避けてください。  <xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent>、および <xref:System.Threading.Monitor> を使用してください。  
  
-   メイン プログラムから、イベントなどを使用して、ワーカー スレッドの実行を制御しないでください。  ワーカー スレッドの側で、作業ができるようになるまでの待機、作業の実行、および実行終了後のプログラムへの通知を行うように、プログラムをデザインします。  ワーカー スレッドによるブロックを行わない場合は、スレッド プールのスレッドを使用することを考慮します。  ワーカー スレッドがブロックを行う場合は、<xref:System.Threading.Monitor.PulseAll%2A?displayProperty=fullName> が役立ちます。  
  
-   ロック オブジェクトとして型を使用しないでください。  つまり、C\# の `lock(typeof(X))`、Visual Basic の `SyncLock(GetType(X))` などのコードを使用すること、または <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> を <xref:System.Type> オブジェクトと組み合わせて使用することを避けます。  <xref:System.Type?displayProperty=fullName> のインスタンスは、1 つの型につきアプリケーション ドメインごとに 1 つのみです。  ロックする型がパブリックの場合、自分以外のコードでもその型をロックできるため、デッドロックになる可能性があります。  詳細については、「[信頼性に関するベスト プラクティス](../../../docs/framework/performance/reliability-best-practices.md)」を参照してください。  
  
-   インスタンスをロックする場合 \(たとえば、C\# の `lock(this)`、Visual Basic の `SyncLock(Me)`\) には注意してください。  アプリケーション内の、その型以外の他のコードがオブジェクトをロックすると、デッドロックが発生する場合があります。  
  
-   モニター状態に入った \(ロックを取得した\) スレッドは、モニター状態である間に例外が発生した場合でも、必ずモニター状態から出すようにします。  C\# の [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) ステートメントと Visual Basic の [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) ステートメントは、**finally** ブロックを使用して <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> が呼び出されるようにすることで、この動作を自動的に提供します。  **Exit** を確実に呼び出すことができない場合は、**Mutex** を使用するようにデザインを変更することを考慮します。  ミューテックスは、現在それを保持しているスレッドが終了すると、自動的に解放されます。  
  
-   マルチ スレッドは異なるリソースを必要とするタスクに使用し、1 つのリソースに複数のスレッドを割り当てることがないように注意します。  たとえば、I\/O を含む作業であれば、その作業専用のスレッドを用意すると有益です。I\/O 操作の間、このスレッドはブロックを行いますが、他のスレッドは実行できるからです。  ユーザー入力も、専用のスレッドが役に立つリソースの 1 つです。  シングル プロセッサのコンピューターでは、計算中心のタスクがユーザー入力や I\/O タスクと共存することはできますが、計算中心タスクどうしは競合してしまいます。  
  
-   単純な状態変更については、`lock` ステートメント \(Visual Basic では `SyncLock`\) ではなく、<xref:System.Threading.Interlocked> クラスのメソッドの使用を検討します。  `lock` ステートメントは汎用的なツールとして優れていますが、<xref:System.Threading.Interlocked> クラスは、分離不可能な状態であることが必要な更新のパフォーマンスに優れています。  内部的には、競合がない場合は、単一の lock プレフィックスが実行されます。  コードの校閲で、次に示す例のようなコードを探します。  最初の例では、状態変数をインクリメントしています。  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     `lock` ステートメントの代わりに <xref:System.Threading.Interlocked.Increment%2A> メソッドを次のように使用すると、パフォーマンスを向上できます。  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  .NET Framework Version 2.0 では、1 より大きなインクリメントでのアトミック更新を <xref:System.Threading.Interlocked.Add%2A> メソッドで実現できます。  
  
     2 番目の例では、参照型の変数を、null 参照 \(Visual Basic では `Nothing`\) の場合にのみ更新しています。  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     この代わりに <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドを次のように使用すると、パフォーマンスを向上できます。  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  .NET Framework Version 2.0 では、<xref:System.Threading.Interlocked.CompareExchange%2A> メソッドに、任意の参照型のタイプ セーフな置換に使用できるジェネリック オーバーロードがあります。  
  
## クラス ライブラリに関する推奨事項  
 マルチスレッド用のクラス ライブラリをデザインするときには、次のガイドラインを検討します。  
  
-   可能な限り、同期の必要を避けるようにします。  これは、頻繁に使用するコードの場合に特に言えます。  たとえば、競合状態をなくすのではなく、競合状態に対応できるようにアルゴリズムを調整できる場合があります。  不要な同期があると、パフォーマンスが低下し、デッドロックや競合状態が発生する可能性が生じます。  
  
-   静的なデータ \(Visual Basic では `Shared`\) は既定でスレッド セーフにします。  
  
-   インスタンス データは既定でスレッド セーフにしないようにします。  スレッド セーフなコードを作成するロックを追加すると、パフォーマンスが低下し、ロックの競合が増加し、デッドロックが発生する可能性が生じます。  一般的なアプリケーション モデルでは、一度にユーザー コードを実行するスレッドは 1 つだけにして、スレッド セーフを実現する必要を最小限に抑えます。  この理由から、.NET Framework のクラス ライブラリは既定ではスレッド セーフではないことが必要です。  
  
-   静的状態を変更する静的メソッドは提供しないでください。  一般的なサーバーのシナリオでは、静的状態は要求間で共有されます。つまり、複数のスレッドがそのコードを同時に実行できます。  これにより、スレッド処理のバグが発生する可能性が高くなります。  要求間で共有されないインスタンスにデータをカプセル化するデザイン パターンの使用を検討してください。  加えて、静的なデータを同期する場合は、状態を変更する呼び出しが静的メソッド間にあると、デッドロックや冗長な同期が生じる可能性があり、パフォーマンスに悪影響を及ぼします。  
  
## 参照  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)