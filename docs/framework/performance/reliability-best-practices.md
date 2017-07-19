---
title: "信頼性に関するベスト プラクティス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "非同期の例外処理"
  - "バックアウト コード"
  - "ブロック, 信頼性"
  - "catch ブロック"
  - "CER"
  - "クリーンアップ操作"
  - "制約された実行領域"
  - "アプリケーション間のドメイン共有状態"
  - "サービス拒否 (DoS) 攻撃"
  - "ファイバー"
  - "ファイナライザー, 信頼性"
  - "finally 句"
  - "GC.KeepAlive メソッド"
  - "識別 (ロックを)"
  - "偽装"
  - "リークしたリソース [.NET Framework]"
  - "ロック, 信頼性"
  - "マネージ スレッド"
  - "マーク (ロックを)"
  - "メモリ, 信頼性"
  - "プロセス全体のドメイン共有状態"
  - "再起動 (データベースを)"
  - "信頼性 [.NET Framework]"
  - "信頼性のコントラクト [.NET Framework]"
  - "SafeHandle クラス, 信頼性"
  - "共有状態"
  - "シングルスレッド COM コンポーネント"
  - "スロー リーク"
  - "SQL Server [.NET Framework], 信頼性"
  - "STA に依存しない機能"
  - "中断 (スレッドを)"
  - "同期, 信頼性"
  - "スレッド化 [.NET Framework], 信頼性"
  - "アンマネージ メモリ"
  - "記述 (信頼性の高いコードを)"
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# 信頼性に関するベスト プラクティス
以下の信頼性の規則は SQL Server 向けの規則ですが、ホスト ベースのサーバー アプリケーションにも適用されます。  SQL Server のようなサーバーでは、リソースをリークしたり、停止したりしないことが非常に重要となります。ただし、オブジェクトの状態を変更するすべてのメソッドのバックアウト コードを記述しても、これは実現できません。バックアウト コードによってあらゆる場所でエラーから回復する、100% 信頼できるマネージ コードを作成することが目標ではありません。これは、成功の見込みがほとんどない困難な作業です。共通言語ランタイム \(CLR: Common Language Runtime\) は、完璧なコードの記述を実現できるほど強力な保証をマネージ コードに対して容易に提供できるわけではありません。ASP.NET とは異なり、SQL Server が使用するプロセスは 1 つだけです。このプロセスは、許容範囲を超える長時間にわたってデータベースを停止させなければリサイクルできません。  
  
 このように保証が十分ではなく、単一のプロセスで実行する場合、信頼性の基盤となるのは、必要なときにスレッドの終了やアプリケーション ドメインのリサイクルを行い、予防措置を講じて、ハンドルやメモリなどのオペレーティング システム リソースがリークされないようにすることです。この簡単な信頼性の制約がある場合でも、次のような信頼性の重要な要件が存在します。  
  
-   オペレーティング システム リソースをリークしない。  
  
-   CLR に対してあらゆる形式のすべてのマネージ ロックを示す。  
  
-   <xref:System.AppDomain> のリサイクルが円滑に機能できるように、アプリケーション ドメイン間の共有の状態を破損しない。  
  
 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException>、<xref:System.OutOfMemoryException> の各例外を処理するマネージ コードを記述することは理論上では可能ですが、アプリケーション全体にわたり、このような信頼性の高いコードを記述することを開発者に期待するのは現実的とはいえません。このため、帯域外の例外が発生し、実行中のスレッドが終了することになります。終了したスレッドが共有の状態を編集中だった場合 \(これは、スレッドがロックを保持しているかどうかによって判断できます\)、<xref:System.AppDomain> はアンロードされます。共有の状態を更新するための信頼性のあるバックアウト コードを記述することはできないため、共有の状態を編集中のメソッドを終了すると、その状態は破損することになります。  
  
 .NET Framework Version 2.0 では、信頼性を必要とするホストは SQL Server だけです。SQL Server でアセンブリを実行する場合、データベースでの実行時に無効にする特定の機能が存在する場合でも、そのアセンブリのあらゆる部分に対して信頼性を実現するための作業を行う必要があります。これが必要となるのは、コード分析エンジンはアセンブリ レベルでコードをチェックし、無効になっているコードを区別できないためです。  SQL Server のプログラミングにおけるもう 1 つの考慮事項は、SQL Server は 1 つのプロセス内ですべてのタスクを実行し、<xref:System.AppDomain> のリサイクルは、メモリやオペレーティング システム ハンドルなどのすべてのリソースをクリーンアップするために使用されるということです。  
  
 ファイナライザーやデストラクター、またはバックアウト コードの `try/finally` ブロックに依存することはできません。  これらは、中断されたり呼び出されなかったりする可能性があります。  
  
 <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException>、および <xref:System.OutOfMemoryException> の各非同期例外は、予測不可能な場所 \(場合によっては各マシン語命令\) でスローされる可能性があります。  
  
 SQL では、マネージ スレッドは必ずしも Win32 スレッドであるとは限らず、ファイバーの場合もあります。  
  
 プロセス全体またはアプリケーション ドメイン間における変更可能な共有の状態を安全に変更することは非常に難しいため、できる限り回避する必要があります。  
  
 SQL Server では、メモリ不足の状態は珍しいことではありません。  
  
 SQL Server 内でホストされているライブラリが共有の状態を適切に更新していない場合、データベースが再起動されるまでコードでは回復されない可能性が高くなります。また、極端な場合には、このことが原因で SQL Server プロセスが失敗し、データベースの再起動につながる可能性もあります。データベースを再起動すると、Web サイトを停止したり、会社の業務に影響を及ぼしたりする可能性があり、可用性が損なわれます。メモリやハンドルなどのオペレーティング システム リソースが徐々にリークされると、回復の見込みのない状態で、サーバーがハンドルの割り当てに最終的に失敗する可能性があります。また、サーバーのパフォーマンスが徐々に低下し、顧客のアプリケーションの可用性が低下することもあります。これらのシナリオを回避することが望ましいのは明らかです。  
  
## ベスト プラクティスの規則  
 ここでは、サーバーで実行するマネージ コードに関するコード レビューの内容に重点を置いています。フレームワークの安定性と信頼性を向上させるうえで、これらを理解しておくことが必要です。  これらのチェックは、すべて一般的に推奨される方法であり、サーバーには不可欠です。  
  
 デッドロックまたはリソースの制約が発生した場合、SQL Server はスレッドを中止するか、<xref:System.AppDomain> を破棄します。この状態が発生した場合、実行が保証されるのは、制約された実行領域 \(CER: Constrained Execution Region\) 内のバックアウト コードだけです。  
  
### SafeHandle を使用してリソース リークを回避する  
 <xref:System.AppDomain> のアンロードが発生した場合、`finally` ブロックまたはファイナライザーの実行に依存することはできません。したがって、<xref:System.IntPtr>、<xref:System.Runtime.InteropServices.HandleRef>、またはこれらに類似するクラスではなく、<xref:System.Runtime.InteropServices.SafeHandle> クラスを通じてオペレーティング システム リソースへのすべてのアクセスを抽出することが重要となります。  これは、CLR が、<xref:System.AppDomain> の終了処理の場合に使用するハンドルを追跡し、閉じることができます。<xref:System.Runtime.InteropServices.SafeHandle> は、CLR が必ず実行するクリティカル ファイナライザーを使用します。  
  
 オペレーティング システム ハンドルは、作成された時点から解放されるまでの間、セーフ ハンドルに格納されます。<xref:System.Threading.ThreadAbortException> が発生してハンドルをリークする可能性のある間、ウィンドウは存在しません。また、プラットフォーム呼び出しではハンドルの参照カウントを行うため、ハンドルの有効期間の追跡を終了し、`Dispose` とハンドルを現在使用しているメソッドとの競合状態に伴うセキュリティ上の問題を防ぐことができます。  
  
 オペレーティング システム ハンドルを単にクリーンアップするためにファイナライザーを現在保持しているほとんどのクラスでは、ファイナライザーは今後必要ではなくなります。  代わりに、ファイナライザーは <xref:System.Runtime.InteropServices.SafeHandle> の派生クラスで保持されることになります。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> は、<xref:System.IDisposable.Dispose%2A?displayProperty=fullName> に代わるものではありません。リソースの競合が発生する可能性はやはり存在するため、オペレーティング システム リソースを明示的に破棄することにはパフォーマンス上の利点があります。リソースを明示的に破棄する `finally` ブロックは、実行されない場合もあることを認識してください。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> を使用すると、ハンドルを解放する処理 \(ルーチンを解放したり、ループ内の一連のハンドルを解放したりするオペレーティング システム ハンドルに状態を渡すなど\) を実行する独自の <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> メソッドを実装できます。このメソッドの実行は CLR によって保証されます。<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 実装の作成者は、どのような状況においてもハンドルが確実に解放されるようにする必要があります。  ハンドルを解放できないと、ハンドルはリークされることになり、多くの場合、そのハンドルに関連付けられたネイティブ リソースのリークにつながります。  したがって、<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 実装が呼び出し時に利用できない可能性のあるリソースの割り当てを必要としない、<xref:System.Runtime.InteropServices.SafeHandle> の派生クラスを構築することが非常に重要です。  コードがこのようなエラーを処理し、コントラクトをすべて満たしてネイティブ ハンドルを解放できることを条件に、<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> の実装内で失敗する可能性のあるメソッドを呼び出すことが許可されます。  デバッグのために、<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> は <xref:System.Boolean> の戻り値を返します。この戻り値は、リソースの解放を妨げる深刻なエラーが発生した場合に、`false` に設定されます。  このとき、[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA が有効であれば、問題の特定を支援するためにアクティブになります。  これは、その他の点ではランタイムに影響を及ぼしません。<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> は、同じリソースに対して再度呼び出されることはないため、ハンドルがリークされることになります。  
  
 一部のコンテキストでは、<xref:System.Runtime.InteropServices.SafeHandle> は適切ではありません。<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> メソッドは、<xref:System.GC> ファイナライザー スレッドで実行できるため、特定のスレッドで解放する必要のあるハンドルを <xref:System.Runtime.InteropServices.SafeHandle> にラップする必要はありません。  
  
 ランタイム呼び出し可能ラッパー \(RCW: Runtime Callable Wrapper\) は、追加のコードを必要とせずに CLR によって削除できます。プラットフォーム呼び出しを使用し、`IUnknown*` または <xref:System.IntPtr>として COM オブジェクトを扱う RCW を使用するコードでは、コードは書き直す必要があります。<xref:System.Runtime.InteropServices.SafeHandle> が、マネージ コードへのコールバック アンマネージ解放メソッドの可能性があるため、このシナリオに対して十分でない場合があります。  
  
#### コード分析規則  
 <xref:System.Runtime.InteropServices.SafeHandle> を使用して、オペレーティング システム リソースをカプセル化します。  <xref:System.Runtime.InteropServices.HandleRef> または <xref:System.IntPtr> 型のフィールドは使用しないでください。  
  
### オペレーティング システム リソースのリークを防ぐために、ファイナライザーを実行する必要がないことを確認する  
 ファイナライザーを入念に見直して、ファイナライザーが実行されない場合でも、重大なオペレーティング システム リソースがリークされないようにします。アプリケーションが安定した状態で実行されているときや、SQL Server などのサーバーがシャットダウンしたときに発生する <xref:System.AppDomain> の正常なアンロードとは異なり、<xref:System.AppDomain> が突然アンロードされたときには、オブジェクトは終了されません。アプリケーションの正確さは保証できなくても、リソースをリークしないことでサーバーの整合性を保つ必要があるため、アンロードが突然発生した場合に、リソースがリークされないようにします。<xref:System.Runtime.InteropServices.SafeHandle> を使用して、オペレーティング システム リソースを解放します。  
  
### オペレーティング システム リソースのリークを防ぐために、finally 句を実行する必要がないことを確認する  
 CER 以外の領域では、`finally` 句が実行されるという保証はないため、ライブラリ開発者には、アンマネージ リソースを解放するために `finally` ブロック内のコードに依存しないことが求められます。この解決策として、<xref:System.Runtime.InteropServices.SafeHandle> を使用することをお勧めします。  
  
#### コード分析規則  
 オペレーティング システム リソースのクリーンアップには、`Finalize` ではなく <xref:System.Runtime.InteropServices.SafeHandle> を使用します。  <xref:System.IntPtr> は使用しないでください。<xref:System.Runtime.InteropServices.SafeHandle> を使用して、リソースをカプセル化します。  finally 句を実行する必要がある場合は CER に配置します。  
  
### すべてのロックは既存のマネージ ロック コードを完了する必要がある  
 CLR は、スレッドをただ中止するのではなく、<xref:System.AppDomain> を破棄するために、コードがいつロック状態になっているかを認識する必要があります。スレッドを中止すると、そのスレッドで処理されているデータが矛盾した状態のままになる可能性があるため、危険な場合があります。  したがって、<xref:System.AppDomain> 全体をリサイクルする必要があります。ロックを識別できないと、デッドロックや不正な結果を招くおそれがあります。  ロック領域を識別するには、<xref:System.Threading.Thread.BeginCriticalRegion%2A> メソッドと <xref:System.Threading.Thread.EndCriticalRegion%2A> メソッドを使用します。この 2 つのメソッドは、現在のスレッドにだけ適用される <xref:System.Threading.Thread> クラスの静的メソッドです。これらを使用すると、あるスレッドが別のスレッドのロック カウントを編集するのを防ぐことができます。  
  
 <xref:System.Threading.Monitor.Enter%2A> と <xref:System.Threading.Monitor.Exit%2A> にはこの CLR 通知が組み込まれているため、これらを使用することをお勧めします。これらのメソッドを使用する [lock ステートメント](../Topic/lock%20Statement%20\(C%23%20Reference\).md) を使うこともできます。  
  
 スピン ロックなどの他のロック機構と <xref:System.Threading.AutoResetEvent> は、これらのメソッドを呼び出して、クリティカル セクションに入ったことを CLR に通知します。これらのメソッドはロックを取得するわけではありません。コードがクリティカル セクションで実行されており、スレッドを中止すると、共有の状態が矛盾したままになる可能性があることを CLR に通知します。カスタムの <xref:System.Threading.ReaderWriterLock> クラスなど、独自の種類のロックを定義している場合は、これらのロック カウント メソッドを使用します。  
  
#### コード分析規則  
 <xref:System.Threading.Thread.BeginCriticalRegion%2A> と <xref:System.Threading.Thread.EndCriticalRegion%2A> を使用して、すべてのロックをマークし、識別します。  ループ内で、<xref:System.Threading.Interlocked.CompareExchange%2A>、<xref:System.Threading.Interlocked.Increment%2A>、および <xref:System.Threading.Interlocked.Decrement%2A> を使用しないでください。これらのメソッドの Win32 バリアントのプラットフォーム呼び出しを実行しないでください。ループ内で <xref:System.Threading.Thread.Sleep%2A> を使用しないでください。揮発性フィールドを使用しないでください。  
  
### クリーンアップ コードは、catch の後ではなく、finally または catch ブロックに配置する必要がある  
 クリーンアップ コードを `catch` ブロックの後に配置することはできません。`finally` または `catch` ブロック自体に配置する必要があります。これは、通常推奨される方法です。`finally` ブロックは、例外がスローされたときと `try` ブロックの末尾まで正常に到達したときに同じコードを実行するため、通常はこのブロックが使用されます。<xref:System.Threading.ThreadAbortException> などの予期しない例外がスローされた場合には、クリーンアップ コードは実行されません。`finally` でクリーンアップするすべてのアンマネージ リソースは、リークを防ぐために <xref:System.Runtime.InteropServices.SafeHandle> にラップすることが理想的です。C\# の `using` キーワードを効果的に使用することで、ハンドルなどのオブジェクトを破棄できます。  
  
 <xref:System.AppDomain> のリサイクルによって、ファイナライザー スレッドのリソースをクリーンアップできますが、クリーンアップ コードを適切な場所に配置することも重要です。スレッドがロックを保持せずに非同期例外を受け取った場合、CLR は <xref:System.AppDomain> をリサイクルする必要なく、そのスレッド自体の終了を試みます。リソースが必ずクリーンアップされるようにすることで、より多くのリソースが利用可能になり、有効期間を適切に管理することもできます。あるエラー コードのパスにあるファイルへのハンドルを明示的に閉じずに、<xref:System.Runtime.InteropServices.SafeHandle> ファイナライザーがこれをクリーンアップするまで待機した場合、コードを次回実行したときに、ファイナライザーがまだ実行されていなければ、この同じファイルへのアクセス試行は失敗する可能性があります。このため、クリーンアップ コードが厳密には必要ない場合でも、クリーンアップ コードが存在し、正しく動作することを保証することで、完全かつ迅速にエラーから回復できます。  
  
#### コード分析規則  
 `catch` の後のクリーンアップ コードは、`finally` ブロックにあることが必要です。  finally ブロックで破棄するための呼び出しを挿入します。`catch` ブロックがスローで終了するか、再スローする必要があります。例外が発生する可能性があるコード、例えばネットワーク接続を確立できるかどうかを確認するコードのように、そこで何らかの例外が発生する可能性があるコードでは、通常の状況でも多数の例外をキャッチする必要があるため、そのコードをテストして成功するかどうか確認する必要があります。  
  
### アプリケーション ドメイン間におけるプロセス全体の変更可能な共有の状態は、削除するか、制約された実行領域を使用する必要がある  
 導入部分で説明したように、複数のアプリケーション ドメインにわたるプロセス全体の共有の状態を信頼できる方法で監視するマネージ コードを記述することは、非常に困難であると考えられます。Win32 コード内、CLR 内部、またはリモート処理を使用するマネージ コード内において、プロセス全体の共有の状態はアプリケーション ドメイン間で共有されたある種のデータ構造です。変更可能な共有の状態は、マネージ コードに正確に記述することは非常に難しいため、静的な共有の状態を扱う場合は細心の注意が必要です。プロセス全体またはコンピューター全体の共有の状態がある場合、その状態を削除するか、制約された実行領域 \(CER: Constrained Execution Region\) を使用して共有の状態を保護するための何らかの方法を考えてください。ライブラリの共有の状態が特定または修正されていない場合、<xref:System.AppDomain> の完全なアンロードを必要とする SQL Server などのホストがクラッシュする原因になる可能性があります。  
  
 コードで COM オブジェクトを使用する場合は、アプリケーション ドメイン間でその COM オブジェクトを共有しないようにします。  
  
### プロセス全体またはアプリケーション ドメイン間ではロックは動作しない  
 これまでは、<xref:System.Threading.Monitor.Enter%2A> と [lock ステートメント](../Topic/lock%20Statement%20\(C%23%20Reference\).md) を使用してプロセスのグローバル ロックを作成していました。この状況が発生するのは、共有されていないアセンブリの <xref:System.Type> インスタンス、<xref:System.Threading.Thread> オブジェクト、内部文字列、リモート処理を使用してアプリケーション ドメイン間で共有される一部の文字列など、<xref:System.AppDomain> の非バインド クラスでロックを行う場合などです。これらのロックは、プロセス全体にわたるロックではなくなっています。プロセス全体にわたるアプリケーション ドメイン間のロックの存在を特定するには、ロック内のコードが外部の永続化されたリソース \(ディスク上のファイルや場合によってはデータベースなど\) を使用しているかどうかを確認します。  
  
 保護されたコードが外部リソースを使用している場合、そのコードは複数のアプリケーション ドメインで同時に実行される可能性があるため、<xref:System.AppDomain> 内でロックを取得すると問題が生じる場合があります。これは、1 つのログ ファイルへの書き込み時やプロセス全体のソケットにバインドするときに問題になる可能性があります。これらの変更は、名前付き <xref:System.Threading.Mutex> または <xref:System.Threading.Semaphore> インスタンスを使用する以外には、マネージ コードを使用してプロセスのグローバル ロックを容易に取得する方法はないことを意味します。2 つのアプリケーション ドメインで同時に実行されることのないコードを作成するか、<xref:System.Threading.Mutex> クラスまたは <xref:System.Threading.Semaphore> クラスを使用します。ファイバー モードでの実行は、ミューテックスの取得と解放を同じオペレーティング システム スレッドが行うことを保証できないことを意味するため、既存のコードを変更できない場合は、Win32 の名前付きミューテックスを使用してこの同期を行わないでください。アンマネージ コードを使用してロックを同期するのではなく、マネージ <xref:System.Threading.Mutex> クラス \(名前付き <xref:System.Threading.ManualResetEvent>\)、<xref:System.Threading.AutoResetEvent>、または <xref:System.Threading.Semaphore> を使用して、CLR が認識できる方法でコードのロックを同期します。  
  
#### lock\(typeof\(MyType\)\) を避ける  
 すべてのアプリケーション ドメイン間で共有するコードのコピーを 1 つしか持たない共有アセンブリに含まれる、プライベートおよびパブリック <xref:System.Type> オブジェクトにも問題があります。共有アセンブリの場合、<xref:System.Type> のインスタンスはプロセスごとに 1 つしか存在しません。つまり、複数のアプリケーション ドメインが、まったく同じ <xref:System.Type> インスタンスを共有します。<xref:System.Type> インスタンスのロックを取得すると、<xref:System.AppDomain> だけでなくプロセス全体に影響するロックが取得されます。ある <xref:System.AppDomain> が <xref:System.Type> オブジェクトのロックを取得したときに、そのスレッドが突然中止された場合、ロックは解放されません。このロックによって、他のアプリケーション ドメインがデッドロック状態になる可能性があります。  
  
 静的メソッド内でロックを取得する適切な方法は、静的な内部同期オブジェクトをコードに追加することです。これは、クラス コンストラクターが存在する場合はそのコンストラクターで初期化できますが、存在しない場合は次のように初期化できます。  
  
```  
private static Object s_InternalSyncObject;  
private static Object InternalSyncObject   
{  
    get   
    {  
        if (s_InternalSyncObject == null)   
        {  
            Object o = new Object();  
            Interlocked.CompareExchange(  
                ref s_InternalSyncObject, o, null);  
        }  
        return s_InternalSyncObject;  
    }  
}  
```  
  
 次に、ロックを取得するときに、`InternalSyncObject` プロパティを使用してロック対象のオブジェクトを取得します。クラス コンストラクターで内部同期オブジェクトを初期化した場合は、このプロパティを使用する必要はありません。ロック初期化コードの二重チェックは、この例のように行う必要があります。  
  
```  
public static MyClass SingletonProperty   
{  
    get   
    {  
        if (s_SingletonProperty == null)   
        {  
            lock(InternalSyncObject)   
            {  
                // Do not use lock(typeof(MyClass))   
                if (s_SingletonProperty == null)   
                {  
                    MyClass tmp = new MyClass(…);     
                    // Do all initialization before publishing  
                    s_SingletonProperty = tmp;  
                }  
            }  
        }  
        return s_SingletonProperty;  
    }  
}  
```  
  
#### Lock\(this\) に関する注意  
 パブリックにアクセスできる各オブジェクトのロックを取得することは、通常は許容できます。ただし、そのオブジェクトがサブシステム全体のデッドロックの原因となる可能性がある場合は、前述のデザイン パターンも使用することを検討してください。たとえば、1 つの <xref:System.Security.SecurityManager> オブジェクトのロックによって、<xref:System.AppDomain> 内でデッドロックが発生すると、<xref:System.AppDomain> 全体が使用できなくなります。  この種のパブリックにアクセスできるオブジェクトのロックは取得しないことをお勧めします。通常、個々のコレクションまたは配列のロックは問題ありません。  
  
#### コード分析規則  
 複数のアプリケーション ドメインにわたって使用する可能性のある型のロックを取得したり、同一性をあまり意識しないでください。  <xref:System.Type>、<xref:System.Reflection.MethodInfo>、<xref:System.Reflection.PropertyInfo>、<xref:System.String>、<xref:System.ValueType>、<xref:System.Threading.Thread>、または <xref:System.MarshalByRefObject> から派生したオブジェクトで <xref:System.Threading.Monitor.Enter%2A> を呼び出さないでください。  
  
### GC.KeepAlive 呼び出しを削除する  
 <xref:System.GC.KeepAlive%2A> を使用する必要があるときに使用していなかったり、適切ではないときに使用していたりする既存のコードが多数存在します。クラスがファイナライザーを持たず、オペレーティング システム ハンドルを終了する際に <xref:System.Runtime.InteropServices.SafeHandle> に依存していることを前提として、<xref:System.Runtime.InteropServices.SafeHandle> に変換した後は、クラスで <xref:System.GC.KeepAlive%2A> を呼び出す必要はありません。<xref:System.GC.KeepAlive%2A> の呼び出しを保持するパフォーマンス コストはおそらくごくわずかであるにもかかわらず、既に存在しない場合もある有効期間の問題を解決するために <xref:System.GC.KeepAlive%2A> の呼び出しが必要である、またはこの呼び出しで十分であるという認識は、コードの維持を困難にします。ただし、COM 相互運用の CLR 呼び出し可能ラッパー \(RCW\) を使用する場合は、<xref:System.GC.KeepAlive%2A> はコードでやはり必要となります。  
  
#### コード分析規則  
 <xref:System.GC.KeepAlive%2A> を削除します。  
  
### ホスト保護属性を使用する  
 <xref:System.Security.Permissions.HostProtectionAttribute> \(HPA\) を使用すると、ホスト保護の要件を決定する宣言セキュリティ アクションを使用できます。これにより、ホストは、完全に信頼されるコードであっても、特定のホストには適さない一部のメソッド \(SQL Server の <xref:System.Environment.Exit%2A> や <xref:System.Windows.Forms.MessageBox.Show%2A> など\) の呼び出しを防ぐことができます。  
  
 HPA が影響するのは、共通言語ランタイムをホストし、ホスト保護を実装するアンマネージ アプリケーションだけです \(SQL Server など\)。  この属性を適用すると、セキュリティ アクションによって、クラスまたはメソッドが公開するホスト リソースに基づいたリンク確認要求が作成されます。  クライアント アプリケーション、またはホスト保護されていないサーバー \("evaporates" 属性が適用されたサーバー\) でコードを実行した場合、この属性は検出されないため適用されません。  
  
> [!IMPORTANT]
>  この属性の目的は、セキュリティ動作ではなく、ホスト固有のプログラミング モデルのガイドラインを強制的に適用することです。リンク確認要求はプログラミング モデル要件への準拠性の確認に使用されますが、<xref:System.Security.Permissions.HostProtectionAttribute> はセキュリティ アクセス許可ではありません。  
  
 ホストにプログラミング モデル要件が設定されていない場合、リンク確認要求は発生しません。  
  
 この属性は、次のメソッドまたはクラスを識別します。  
  
-   ホストのプログラミング モデルに適合しないが、害のないメソッドまたはクラス  
  
-   ホストのプログラミング モデルに適合せず、サーバーが管理するユーザー コードを不安定にする可能性があるメソッドまたはクラス  
  
-   ホストのプログラミング モデルに適合せず、サーバー プロセス自体を不安定にする可能性があるメソッドまたはクラス  
  
> [!NOTE]
>  ホスト保護環境で実行する可能性があるアプリケーションで呼び出すクラス ライブラリを作成する場合、<xref:System.Security.Permissions.HostProtectionResource> リソース カテゴリを公開するメンバーにこの属性を適用してください。  この属性を持つ .NET Framework クラス ライブラリのメンバーによって、直接の呼び出し元だけがチェックされます。作成したライブラリ メンバーも、これと同様に直前の呼び出し元のチェックを行う必要があります。  
  
 HPA の詳細については、<xref:System.Security.Permissions.HostProtectionAttribute> のトピックを参照してください。  
  
#### コード分析規則  
 SQL Server の場合、同期またはスレッド処理を導入するために使用するすべてのメソッドは、HPA で識別する必要があります。  これには、状態を共有するメソッド、同期されたメソッド、外部プロセスを管理するメソッドが含まれます。  SQL Server に影響を及ぼす <xref:System.Security.Permissions.HostProtectionResource> 値は、<xref:System.Security.Permissions.HostProtectionResource>、<xref:System.Security.Permissions.HostProtectionResource>、および <xref:System.Security.Permissions.HostProtectionResource> です。  ただし、<xref:System.Security.Permissions.HostProtectionResource> を公開するメソッドは、SQL に影響を及ぼすリソースを使用するこれらの値だけでなく、HPA によって識別する必要があります。  
  
### アンマネージ コード内で無期限にブロックしない  
 マネージ コードではなく、アンマネージ コード内でブロッキングすると、CLR がスレッドを中止できないため、サービス拒否攻撃の原因になる可能性があります。スレッドがブロックされると、CLR は一部の非常に安全性の低い操作を実行しなければ、<xref:System.AppDomain> をアンロードできなくなります。Win32 同期プリミティブを使用したブロッキングは、容認できないブロッキングの一例です。ソケットの `ReadFile` の呼び出しにおけるブロッキングは、できるだけ避ける必要があります。このような操作がタイムアウトする機構を Win32 API で提供するのが理想的です。  
  
 ネイティブに呼び出すメソッドでは、適切な有限のタイムアウトを設定して Win32 呼び出しを使用することが望まれます。ユーザーがタイムアウトを指定できるようにする場合、特定のセキュリティ アクセス許可がなければ無限のタイムアウトを指定できないようにする必要があります。1 つのガイドラインとして、メソッドが 10 秒以上ブロックする場合には、タイムアウトをサポートするバージョンを使用するか、CLR の追加サポートが必要です。  
  
 問題のある API の例を紹介します。パイプ \(匿名パイプと名前付きパイプの両方\) は、タイムアウトを指定して作成できますが、コードでは NMPWAIT\_WAIT\_FOREVER で `CreateNamedPipe` と `WaitNamedPipe` のいずれも呼び出さないようにする必要があります。また、タイムアウトが指定されている場合でも、予測不可能なブロッキングが発生する可能性もあります。匿名パイプで `WriteFile` を呼び出すと、すべてのバイトが書き込まれるまでブロックされます。つまり、バッファーに読み取られていないデータがある場合、リーダーがパイプのバッファー内の領域を解放するまで、`WriteFile` 呼び出しによってブロックされます。ソケットでは、タイムアウト機構を重視する API を必ず使用する必要があります。  
  
#### コード分析規則  
 アンマネージ コード内のタイムアウトのないブロッキングは、サービス拒否攻撃です。  プラットフォーム呼び出しを実行して、`WaitForSingleObject`、`WaitForSingleObjectEx`、`WaitForMultipleObjects`、`MsgWaitForMultipleObjects`、および `MsgWaitForMultipleObjectsEx` を呼び出さないでください。NMPWAIT\_WAIT\_FOREVER は使用しないでください。  
  
### STA に依存する機能を識別する  
 COM シングルスレッド アパートメント \(STA: Single\-Threaded Apartment\) を使用するコードを識別します。SQL Server プロセスでは、STA は無効になります。パフォーマンス カウンターやクリップボードなど、`CoInitialize` に依存する機能は SQL Server 内では無効にする必要があります。  
  
### ファイナライザーに同期の問題がないことを確認する  
 .NET Framework の今後のバージョンでは、複数のファイナライザー スレッドが存在できます。つまり、同じ型の異なるインスタンスのファイナライザーが同時に実行されます。これらは、完全にスレッド セーフである必要はありません。ガベージ コレクターは、オブジェクトの特定のインスタンスのファイナライザーを実行するスレッドは 1 つだけであることを保証します。ただし、オブジェクトの複数の異なるインスタンスで同時に実行するときに、競合状態やデッドロック状態にならないように、ファイナライザーをコーディングする必要があります。ファイナライザーで外部の状態 \(ログ ファイルへの書き込みなど\) を使用する場合は、スレッド処理の問題に対処する必要があります。スレッド セーフにするために、終了処理に依存しないでください。  スレッド ローカル ストレージ \(マネージまたはネイティブ\) を使用して、ファイナライザー スレッドの状態を格納しないでください。  
  
#### コード分析規則  
 ファイナライザーには、同期の問題がないことが必要です。  ファイナライザーで静的に変更可能な状態を使用しないでください。  
  
### アンマネージ メモリはできるだけ避ける  
 オペレーティング システム ハンドルと同様に、アンマネージ メモリもリークされる可能性があります。できれば、[stackalloc](../Topic/stackalloc%20\(C%23%20Reference\).md) を使用してスタックにメモリを割り当てるか、固定されたマネージ オブジェクト \([fixed ステートメント](../Topic/fixed%20Statement%20\(C%23%20Reference\).md) や byte\[\] を使用した <xref:System.Runtime.InteropServices.GCHandle> など\) を使用するようにします。<xref:System.GC> は、最終的にこれらをクリーンアップします。ただし、アンマネージ メモリを割り当てる必要がある場合は、<xref:System.Runtime.InteropServices.SafeHandle> から派生したクラスを使用して、メモリの割り当てをラップするよう考慮してください。  
  
 <xref:System.Runtime.InteropServices.SafeHandle> が適さないケースが少なくとも 1 つあります。メモリの割り当てまたは解放を行う COM メソッド呼び出しでは、ある DLL が `CoTaskMemAlloc` によってメモリを割り当て、別の DLL が `CoTaskMemFree` によってそのメモリを解放するのが一般的です。<xref:System.Runtime.InteropServices.SafeHandle> は、一方の DLL がメモリの有効期間を制御できるようにする代わりに、アンマネージ メモリの有効期間を <xref:System.Runtime.InteropServices.SafeHandle> の有効期間と結び付けようとするため、このような状況で使用することは適切ではありません。  
  
### catch\(Exception\) のすべての使用を見直す  
 ある特定の例外ではなく、すべての例外をキャッチする catch ブロックは、非同期例外もキャッチします。すべての catch\(Exception\) ブロックをチェックし、重要ではないリソースの解放やスキップできるバックアウト コード、および <xref:System.Threading.ThreadAbortException>、<xref:System.StackOverflowException>、または <xref:System.OutOfMemoryException> を処理するために catch ブロック自体に含まれる不正と思われる動作を探します。このコードは、ログを記録する可能性もあれば、特定の例外だけを確認することを想定していたり、例外が発生するたびに、ある特別な原因に当てはまる場合にだけ失敗することを想定していたりする可能性もあります。これらの想定を更新し、<xref:System.Threading.ThreadAbortException> を含めることが必要な場合があります。  
  
 すべての例外をキャッチするすべての場所を、スローされることが予測される特定の種類の例外 \(文字列の書式指定メソッドの <xref:System.FormatException> など\) をキャッチするように変更することを検討します。これにより、catch ブロックが予測不可能な例外に対して実行されなくなります。また、予測不可能な例外をキャッチすることにより、コードに含まれるバグを明らかにすることもできます。原則として、ライブラリ コード内の例外は処理しないでください \(例外をキャッチする必要のあるコードは、呼び出すコード内のデザイン上の欠陥を示す場合があります\)。例外をキャッチし、別の種類の例外をスローして、より多くのデータを提供することが望ましい場合もあります。この場合、入れ子になった例外を使用して、新しい例外の <xref:System.Exception.InnerException%2A> プロパティにエラーの実際の原因を格納します。  
  
#### コード分析規則  
 すべてのオブジェクトを受け取るマネージ コード、またはすべての例外をキャッチするマネージ コード内のすべての catch ブロックを見直します。C\# の場合、これは、`catch` {} と `catch(Exception)` {} の両方にフラグを設定するということです。例外の種類をきわめて特殊なものにするよう考慮するか、コードを見直して、予測不可能な例外の種類をキャッチした場合に不適切に動作しないようにします。  
  
### Win32 スレッドはファイバーであるため、マネージ スレッドが Win32 スレッドであることを想定しない  
 マネージ スレッド ローカル ストレージは使用できますが、アンマネージ スレッド ローカル ストレージを使用することはできません。また、コードが現在のオペレーティング システム スレッドで再度実行されることも想定しないでください。スレッドのロケールと同様に設定を変更しないでください。`InitializeCriticalSection` および `CreateMutex` では、ロック状態に入るオペレーティング システム スレッドがそのロックを終了させる必要があるため、プラットフォーム呼び出しによってこれらを呼び出さないでください。これは、ファイバーを使用するケースではないため、Win32 のクリティカル セクションとミューテックスを SQL で直接使用することはできません。マネージ <xref:System.Threading.Mutex> クラスは、これらのスレッド アフィニティの懸念事項には対処しません。  
  
 マネージ スレッド ローカル ストレージやスレッドの現在の UI カルチャを含め、マネージ <xref:System.Threading.Thread> オブジェクトのほとんどの状態を安全に使用できます。また、現在のマネージ スレッドでのみ既存の静的変数の値をアクセス可能にする <xref:System.ThreadStaticAttribute> を使用することもできます \(これは、CLR でファイバー ローカル ストレージを使用するもう 1 つの方法です\)。プログラミング モデルに関する理由から、SQL での実行時にスレッドの現在のカルチャを変更することはできません。  
  
#### コード分析規則  
 SQL Server はファイバー モードで実行します。スレッド ローカル ストレージは使用しないでください。  プラットフォーム呼び出しによって、`TlsAlloc`、`TlsFree`、`TlsGetValue`、および `TlsSetValue.` を呼び出すことは避けます。  
  
### SQL Server に偽装を処理させる  
 偽装はスレッド レベルで機能し、SQL はファイバー モードで実行できるため、マネージ コードでユーザーを偽装する必要はありません。また、`RevertToSelf` を呼び出す必要もありません。  
  
#### コード分析規則  
 SQL Server に偽装を処理させます。  `RevertToSelf`、`ImpersonateAnonymousToken`、`DdeImpersonateClient`、`ImpersonateDdeClientWindow`、`ImpersonateLoggedOnUser`、`ImpersonateNamedPipeClient`、`ImpersonateSelf`、`RpcImpersonateClient`、`RpcRevertToSelf`、`RpcRevertToSelfEx`、`SetThreadToken` を使用しないでください。  
  
### Thread::Suspend を呼び出さない  
 スレッドを中断する機能は単純な動作のように思われますが、デッドロック状態の原因になる可能性があります。ロックを保持するスレッドが 2 番目のスレッドによって中断されてから、2 番目のスレッドが同じロックを取得しようとすると、デッドロックが発生します。<xref:System.Threading.Thread.Suspend%2A> は、セキュリティ、クラスの読み込み、リモート処理、および現在のリフレクションに干渉する。  
  
#### コード分析規則  
 <xref:System.Threading.Thread.Suspend%2A> を呼び出さないでください。  代わりに、<xref:System.Threading.Semaphore> や <xref:System.Threading.ManualResetEvent> など、同期プリミティブを使用するよう考慮します。  
  
### 制約された実行領域と信頼性のコントラクトを使用して重大な操作を保護する  
 共有の状態を更新する複雑な操作や、完全に成功するか、完全に失敗するかのいずれかであることを必要とする複雑な操作を実行するときには、制約された実行領域 \(CER: Constrained Execution Region\) によって必ず保護します。  これにより、スレッドが突然中止されたり、<xref:System.AppDomain> が突然アンロードされた場合も含め、どのような場合にもコードが実行されることが保証されます。  
  
 CER は、<xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> の呼び出しの直後に配置された特殊な `try/finally` ブロックです。  
  
 CER を使用すると、`try` ブロックを実行する前に、finally ブロックにすべてのコードを準備するよう JIT \(Just\-In\-Time\) コンパイラに指示します。  これにより、どのような場合でも finally ブロック内のコードがビルドされ、実行されることが保証されます。  CER に空の `try` ブロックを配置することはまれです。  CER を使用すると、非同期スレッドの中止とメモリ不足の例外から保護できます。  非常に複雑なコードのスタック オーバーフローを追加処理する CER の形式については、<xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> のトピックを参照してください。  
  
## 参照  
 <xref:System.Runtime.ConstrainedExecution>   
 [SQL Server プログラミングとホスト保護属性](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)