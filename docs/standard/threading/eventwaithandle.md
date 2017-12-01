---
title: EventWaitHandle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], EventWaitHandle class
- EventWaitHandle class
- event wait handles [.NET Framework]
- threading [.NET Framework], cross-process synchronization
ms.assetid: 11ee0b38-d663-4617-b793-35eb6c64e9fc
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bd248133bd95ff05246eb36a8e250247fd7ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle"></a>EventWaitHandle
<xref:System.Threading.EventWaitHandle>クラスを通知し、通知を待機して、互いに通信するためにスレッドを使用できます。 イベント待機ハンドルが (単にイベントとも呼ばれます) は、待機ハンドルを待機中の 1 つまたは複数のスレッドを解放するために通知されることができます。 通知を受けると、イベント待機ハンドルは、手動または自動的にリセットされます。 <xref:System.Threading.EventWaitHandle>クラスは、いずれか、ローカル イベント待機ハンドル (ローカル イベント) を表すことができるまたは名前付きシステム イベント (イベントまたはシステム イベント、すべてのプロセスに表示される名前付き) のハンドルを待機します。  
  
> [!NOTE]
>  イベント待機ハンドルは、.NET Framework では、その単語を通常意味という意味でのイベントでがありません。 またはがないデリゲート イベント ハンドラー関係します。 Word「イベント」は使用を参照して、オペレーティング システムのイベントとしてしました従来されているため、および待機ハンドルの通知を待機中のスレッドを示すので説明のために、イベントが発生しました。  
  
 両方のローカルと名前付きイベント待機ハンドルによって保護されて、システムの同期オブジェクトを使用して<xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>する対象のリソースを解放することを確認してください。 使用することができます、<xref:System.Threading.WaitHandle.Dispose%2A>オブジェクトの使用が完了したらすぐにリソースを解放します。  
  
## <a name="event-wait-handles-that-reset-automatically"></a>イベント待機ハンドルを自動的にリセットします。  
 指定して自動リセット イベントを作成する<xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType>を作成するとき、<xref:System.Threading.EventWaitHandle>オブジェクト。 その名前からわかるように、この同期イベントに自動的にリセット シグナルを受け取ると、1 つの待機中のスレッドを解放します。 呼び出して、イベントの信号をその<xref:System.Threading.EventWaitHandle.Set%2A>メソッドです。  
  
 自動リセット イベントは通常、一度に 1 つのスレッドのリソースへの排他アクセスを提供するために使用します。 スレッドが呼び出すことによって、リソースを要求、<xref:System.Threading.WaitHandle.WaitOne%2A>メソッドです。 メソッドを返しますのかどうかはその他のスレッドが保持していない待機ハンドル、`true`し、呼び出し元のスレッドがリソースを制御します。  
  
> [!IMPORTANT]
>  同様に、すべての同期機構には、すべてのコード パスが保護されたリソースにアクセスする前に、適切な待機ハンドルを待機することを確認する必要があります。 スレッドの同期は協調的です。  
  
 自動リセット イベントがシグナル状態にスレッドが待機していないときに、シグナル状態のままになるスレッドが試行されるまでです。 イベントは、スレッドを解放し、すぐにリセットされ、後続のスレッドをブロックします。  
  
## <a name="event-wait-handles-that-reset-manually"></a>手動でリセットされるイベント待機ハンドル  
 指定して、手動リセット イベントを作成する<xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType>を作成するとき、<xref:System.Threading.EventWaitHandle>オブジェクト。 その名前からわかるように、この同期イベント必要があります手動でリセットする通知を受けた後です。 これがリセットされるまで、呼び出すことによってその<xref:System.Threading.EventWaitHandle.Reset%2A>メソッド、イベント ハンドルを待機しているスレッドすぐにブロックなしで実行します。  
  
 手動では、並べてのゲートのようにイベントの動作をリセットします。 イベントがシグナル状態ではないときを並べてで木馬と同様に、待機しているスレッドをブロックします。 呼び出すことによって、イベントを通知するときにその<xref:System.Threading.EventWaitHandle.Set%2A>メソッドを待機中のすべてのスレッドは続行するために解放します。 イベントはまでシグナル状態のまま、<xref:System.Threading.EventWaitHandle.Reset%2A>メソッドが呼び出されます。 これにより、手動リセット イベントは、1 つのスレッドがタスクを終了するまで待機する必要があるスレッドを保持するための望ましい方法です。  
  
 並べてのままの木馬と同様に、オペレーティング システムによってスケジュールされると実行を再開するにはリリースのスレッドの時間がかかります。 場合、<xref:System.Threading.EventWaitHandle.Reset%2A>メソッドはすべてのスレッドの実行が再開する前に、残りのスレッドをもう一度ブロックできます。 再開されるスレッドとブロックされるスレッド ランダムなどの要因によって負荷、システムでは、スレッドの数を待機しているスケジューラのです。 これは、最も一般的な使用パターン、通知を行った後のイベントを通知するスレッドの終了する場合でもこれは問題ではありません。 結局のところ、新しいタスクを開始するイベントをシグナル状態には、スレッドが再開された待機中のスレッドを実行する場合に、待機中のすべてのスレッドが再開されるまでブロックする必要があります。 それ以外の場合、競合状態があり、コードの動作は予測できません。  
  
## <a name="features-common-to-automatic-and-manual-events"></a>自動および手動のイベントに共通の機能  
 通常、1 つまたは複数のスレッドをブロックする<xref:System.Threading.EventWaitHandle>ブロックされていないスレッドを呼び出すまで、 <xref:System.Threading.EventWaitHandle.Set%2A> (自動リセット イベント) の場合の待機中のスレッドの 1 つまたはすべてのパラメーターを解放するメソッド (の場合は手動リセット イベント)。 スレッドがシグナル送信、<xref:System.Threading.EventWaitHandle>し、ブロックには、アトミックな操作として、静的なを呼び出すことによって、<xref:System.Threading.WaitHandle.SignalAndWait%2A?displayProperty=nameWithType>メソッドです。  
  
 <xref:System.Threading.EventWaitHandle>オブジェクトは、静的で使用できる<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType>と<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType>メソッドです。 <xref:System.Threading.EventWaitHandle>と<xref:System.Threading.Mutex>両方のクラスから派生<xref:System.Threading.WaitHandle>、これらの方法で両方のクラスを使用することができます。  
  
### <a name="named-events"></a>名前付きイベント  
 Windows オペレーティング システムでは、名前を持つイベント待機ハンドルを許可します。 名前付きイベントは、システム全体です。 つまり、名前付きのイベントが作成されると、すべてのプロセスのすべてのスレッドから参照です。 したがって、名前付きイベントは、プロセスおよびスレッドの活動を同期するために使用できます。  
  
 作成することができます、<xref:System.Threading.EventWaitHandle>イベント名を指定するコンス トラクターのいずれかを使用して名前付きシステム イベントを表すオブジェクト。  
  
> [!NOTE]
>  名前付きイベントがシステム全体であるため、可能であれば複数<xref:System.Threading.EventWaitHandle>名前付きイベントを同じを表すオブジェクト。 コンス トラクターを呼び出すたびに、または<xref:System.Threading.EventWaitHandle.OpenExisting%2A>メソッドは、新しい<xref:System.Threading.EventWaitHandle>オブジェクトを作成します。 同じ名前を繰り返し指定すると、同じ名前付きイベントを表す複数のオブジェクトが作成します。  
  
 イベントの名前を使用して、警告が表示されます。 これらは、システム全体であるため、同じ名前を使用する別のプロセスでは予期せず、スレッドをブロックできます。 同じコンピューター上で実行される悪意のあるコードが、これをサービス拒否攻撃の土台として使用する可能性があります。  
  
 アクセス制御セキュリティを使用して保護する、<xref:System.Threading.EventWaitHandle>を指定するコンス トラクターを使用して、可能であれば、名前付きイベントを表すオブジェクト、<xref:System.Security.AccessControl.EventWaitHandleSecurity>オブジェクト。 アクセス制御を使用してセキュリティを適用することも、<xref:System.Threading.EventWaitHandle.SetAccessControl%2A>メソッドが、このイベント待機ハンドルが作成された時刻と保護されている時間の間に脆弱性のままにします。 イベントを保護するが、アクセス制御セキュリティにより、悪意のある攻撃を防ぐため、予期しない名前の衝突の問題が解決しません。  
  
> [!NOTE]
>  異なり、<xref:System.Threading.EventWaitHandle>クラス、派生クラス<xref:System.Threading.AutoResetEvent>と<xref:System.Threading.ManualResetEvent>待機ハンドルを表すローカルのみであることができます。 名前付きシステム イベントを表すことはできません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
