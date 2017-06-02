---
title: "Managed and Unmanaged Threading in Windows | Microsoft Docs"
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
  - "threading [.NET Framework], unmanaged"
  - "threading [.NET Framework], managed"
  - "managed threading"
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# Managed and Unmanaged Threading in Windows
共通言語ランタイムにより作成されたスレッド、マネージ環境に入ってコードを実行するランタイム外部で作成されたスレッドなど、すべてのスレッドの管理は、<xref:System.Threading.Thread> クラスを使用して行われます。 ランタイムは、プロセス内のスレッドのうち、マネージ実行環境内でコードを実行したすべてのスレッドを監視します。 その他のスレッドは追跡しません。 ランタイムがマネージ オブジェクトを COM オブジェクトとしてアンマネージ環境に公開するため、スレッドは COM 相互運用を使用してマネージ実行環境に入ることができます。また、COM [DllGetClassObject](https://msdn.microsoft.com/en-us/library/ms680760.aspx) 関数やプラットフォーム呼び出しを介してマネージ実行環境に入ることもできます。  
  
 ただしアンマネージ スレッドが COM 呼び出し可能ラッパーなどを介してランタイムに入ると、システムがそのスレッド ローカル ストアで内部マネージ <xref:System.Threading.Thread> オブジェクトを検索します。 このオブジェクトが見つかった場合、ランタイムは既にこのスレッドを認識しています。 見つからない場合、ランタイムは新しい <xref:System.Threading.Thread> オブジェクトを作成し、そのスレッドのスレッド ローカル ストアにインストールします。  
  
 マネージ スレッド処理では、<xref:System.Threading.Thread.GetHashCode%2A?displayProperty=fullName> は安定したマネージ スレッド ID です。 この値は、取得されたアプリケーション ドメインに関係なく、スレッドの有効期間にわたって他のスレッドの値と競合することはありません。  
  
> [!NOTE]
>  オペレーティング システム **ThreadId** とマネージ スレッドの間には固定的な関係はありません。これは、アンマネージ ホストがマネージ スレッドとアンマネージ スレッドの間の関係を制御できるためです。 特に、高度なホストはファイバー API を使用して、多数のマネージ スレッドを同一オペレーティング システム スレッドに対してスケジュールしたり、マネージ スレッドを異なるオペレーティング システム スレッド間で移動したりできます。  
  
## WIn32 スレッド処理とマネージ スレッド処理の対応付け  
 Win32 スレッド処理要素とほぼそれに対応するランタイムの対応付けを次の表に示します。 この対応付けは、同一の機能性を示すものではありません。 たとえば **TerminateThread** は **finally** 句の実行やリソースの解放は行わず、また防止することはできません。 ただし <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> はすべてのロールバック コードを実行し、すべてのリソースを解放します。また、<xref:System.Threading.Thread.ResetAbort%2A> を使用して拒否することができます。 機能について推測する前に、このドキュメントを詳しくお読みください。  
  
|Win32|共通言語ランタイム|  
|-----------|---------------|  
|**CreateThread**|**Thread** と <xref:System.Threading.ThreadStart> の組み合わせ|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName>|  
|**Sleep**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>|  
|スレッド ハンドルの **WaitForSingleObject**|<xref:System.Threading.Thread.Join%2A?displayProperty=fullName>|  
|**ExitThread**|同等の機能がありません|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=fullName>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=fullName>|  
|同等の機能がありません|<xref:System.Threading.Thread.Name%2A?displayProperty=fullName>|  
|同等の機能がありません|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName>|  
|**CoInitializeEx** \(OLE32.DLL\) に類似|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName>|  
  
## マネージ スレッドと COM アパートメント  
 マネージ スレッドには、[シングル スレッド](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx) アパートメントをホストするか、[マルチ スレッド](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) アパートメントをホストするかを示すようマークすることができます。 \(COM スレッド アーキテクチャの詳細については、「[プロセス、スレッド、アパートメント](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx)」を参照してください。\)<xref:System.Threading.Thread.GetApartmentState%2A> クラスの <xref:System.Threading.Thread.SetApartmentState%2A>、<xref:System.Threading.Thread.TrySetApartmentState%2A>、および <xref:System.Threading.Thread> の各スレッドは、スレッドのアパートメント状態を返して割り当てます。 状態が設定されていない場合、<xref:System.Threading.Thread.GetApartmentState%2A> は <xref:System.Threading.ApartmentState?displayProperty=fullName> を返します。  
  
 プロパティは、スレッドが <xref:System.Threading.ThreadState?displayProperty=fullName> 状態の場合にのみ設定することができます。設定できるのは、1 つのスレッドにつき 1 回だけです。  
  
 スレッド開始前にアパートメントの状態が設定されていない場合、このスレッドはマルチスレッド アパートメント \(MTA\) として初期化されます。 ファイナライザー スレッドと、<xref:System.Threading.ThreadPool> により制御されるすべてのスレッドは MTA です。  
  
> [!IMPORTANT]
>  アプリケーションのスタートアップ コードでは、アパートメントの状態を制御する方法は、<xref:System.MTAThreadAttribute> または <xref:System.STAThreadAttribute> をエントリ ポイント プロシージャに適用する方法だけです。 .NET Framework 1.0 と 1.1 では、<xref:System.Threading.Thread.ApartmentState%2A> プロパティを最初のコード行として設定できます。 .NET Framework 2.0 ではこの設定は許可されていません。  
  
 COM に対して公開されるマネージ オブジェクトは、フリー スレッド マーシャラーを集約した場合と同様に動作します。 つまり、フリースレッドな方法ですべての COM アパートメントから呼び出すことができます。 このフリー スレッドな動作を示さないマネージ オブジェクトは、<xref:System.EnterpriseServices.ServicedComponent> または <xref:System.Runtime.InteropServices.StandardOleMarshalObject> から派生したオブジェクトだけです。  
  
 マネージ環境では、コンテキストおよびコンテキストにバインディングされたインスタンスを使用しない場合には <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> はサポートされません。[Enterprise Services](../Topic/System.EnterpriseServices.md) を使用する場合は、オブジェクトは <xref:System.EnterpriseServices> \(<xref:System.ContextBoundObject> から派生したオブジェクト\) から派生したものでなければなりません。  
  
 マネージ コードは、COM オブジェクトを呼び出すときには常に COM 規則に従います。 つまり、OLE32 によって示される COM アパートメント プロキシと COM\+ 1.0 コンテキスト ラッパーを介して呼び出します。  
  
## ブロッキングの問題  
 アンマネージ コードでスレッドをブロックしているオペレーティング システムに対し、そのスレッドがアンマネージ呼び出しを実行する場合、ランタイムは <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> または <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> に対してその呼び出しを制御しません。<xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> では、スレッドが再びマネージ コードに入ると、ランタイムはスレッドを **Abort** 対象としてマークし、スレッドを制御します。 アンマネージ ブロックではなくマネージ ブロックを使用することをお勧めします。<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>、<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>、<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>、<xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName>、<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=fullName>、<xref:System.Threading.Thread.Join%2A?displayProperty=fullName>、<xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=fullName> などはすべて <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> と <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> に応答します。 また、スレッドがシングルスレッド アパート内にある場合、これらのマネージ ブロック操作はすべて、スレッドがブロックされている間でもアパートメント内で正しくメッセージ ポンプを行います。  
  
## 参照  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName>   
 <xref:System.Threading.ThreadState>   
 <xref:System.EnterpriseServices.ServicedComponent>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.Monitor>