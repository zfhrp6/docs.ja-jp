---
title: "Mutexes | Microsoft Docs"
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
  - "wait handles"
  - "threading [.NET Framework], Mutex class"
  - "Mutex class, about Mutex class"
  - "threading [.NET Framework], cross-process synchronization"
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Mutexes
<xref:System.Threading.Mutex> オブジェクトを使用すると、リソースへの排他アクセスを提供できます。  <xref:System.Threading.Mutex> クラスは <xref:System.Threading.Monitor> クラスより多くのシステム リソースを使用しますが、アプリケーションのドメイン境界を越えてマーシャリングでき、複数の待機操作と共に使用でき、異なるプロセスのスレッドを同期するために使用できます。  マネージ同期メカニズムの比較については、「[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 コード例については <xref:System.Threading.Mutex.%23ctor%2A> コンストラクターのリファレンス ドキュメントを参照してください。  
  
## ミューテックスの使用  
 スレッドは、ミューテックスの <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを呼び出して所有権を要求します。  この呼び出しは、ミューテックスが使用できるようになるまで、またはオプションのタイムアウト間隔が経過するまでブロックします。  所有しているスレッドがない場合、ミューテックスはシグナル状態になります。  
  
 スレッドは、<xref:System.Threading.Mutex.ReleaseMutex%2A> メソッドを呼び出してミューテックスを解放します。  ミューテックスにはスレッド アフィニティがあり、解放できるのはスレッドが所有するミューテックスだけです。  スレッドが所有していないミューテックスを解放すると、スレッドで <xref:System.ApplicationException> がスローされます。  
  
 <xref:System.Threading.Mutex> クラスは <xref:System.Threading.WaitHandle> から派生し、<xref:System.Threading.WaitHandle> の静的な <xref:System.Threading.WaitHandle.WaitAll%2A> メソッドまたは <xref:System.Threading.WaitHandle.WaitAny%2A> メソッドを呼び出して、他の待機ハンドルと組み合わせて <xref:System.Threading.Mutex> の所有権を要求できます。  
  
 <xref:System.Threading.Mutex> を所有するスレッドは、待機要求呼び出しを繰り返し行うときに、実行をブロックせずに同じ <xref:System.Threading.Mutex> を指定できます。ただし呼び出しと同じ回数だけ <xref:System.Threading.Mutex> を解放して、その所有権を解放する必要があります。  
  
## 放棄されたミューテックス  
 スレッドが <xref:System.Threading.Mutex> を解放せずに終了した場合、ミューテックスは放棄されたと言います。  ミューテックスが保護しているリソースが矛盾した状態で残る可能性があるため、多くの場合、これは重大なプログラミング エラーを示します。  .NET Framework Version 2.0 では、ミューテックスを取得する次のスレッドで <xref:System.Threading.AbandonedMutexException> がスローされます。  
  
> [!NOTE]
>  .NET Framework Version 1.0 および 1.1 では、放棄された <xref:System.Threading.Mutex> はシグナル状態になり、次に待機中のスレッドが所有権を取得します。  待機中のスレッドがない場合、<xref:System.Threading.Mutex> はシグナル状態のままになります。  例外をスローすることはありません。  
  
 システム全体で有効なミューテックスの場合、放棄されたミューテックスは、アプリケーションが \(たとえば Windows タスク マネージャーを使用して\) 強制終了されたことを示す場合があります。  
  
## ローカル ミューテックスとシステム ミューテックス  
 ミューテックスには、ローカル ミューテックスと名前付きシステム ミューテックスの 2 つの種類があります。  名前を受け入れるコンストラクターを使用して <xref:System.Threading.Mutex> オブジェクトを作成すると、そのオブジェクトがその名前のオペレーティング システム オブジェクトに関連付けられます。  名前付きシステム ミューテックスは、オペレーティング システムを介して参照でき、プロセスの活動を同期化する目的で使用できます。  同じ名前付きシステム ミューテックスを表す複数の <xref:System.Threading.Mutex> オブジェクトを作成できます。また、<xref:System.Threading.Mutex.OpenExisting%2A> メソッドを使用して、既存の名前付きシステム ミューテックスを開くことができます。  
  
 ローカル ミューテックスは、現在のプロセス内部でのみ存在します。  ローカル ミューテックスは、ローカル <xref:System.Threading.Mutex> オブジェクトを参照するプロセス内のどのスレッドからでも使用できます。  各 <xref:System.Threading.Mutex> オブジェクトは個別のローカル ミューテックスです。  
  
### システム ミューテックスのアクセス制御セキュリティ  
 .NET Framework Version 2.0 では、名前付きシステム オブジェクトに対して Windows アクセス制御セキュリティを照会して設定できます。  システム オブジェクトはグローバルで、外部のコードでもロックできるため、システム ミューテックスは作成した時点から保護することをお勧めします。  
  
 ミューテックスのアクセス制御セキュリティの詳細については、<xref:System.Security.AccessControl.MutexSecurity> クラスと <xref:System.Security.AccessControl.MutexAccessRule> クラス、<xref:System.Security.AccessControl.MutexRights> 列挙体、<xref:System.Threading.Mutex> クラスの <xref:System.Threading.Mutex.GetAccessControl%2A>、<xref:System.Threading.Mutex.SetAccessControl%2A>、<xref:System.Threading.Mutex.OpenExisting%2A> の各メソッド、および<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> コンストラクターを参照してください。  
  
## 参照  
 <xref:System.Threading.Mutex>   
 <xref:System.Threading.Mutex.%23ctor%2A>   
 <xref:System.Security.AccessControl.MutexSecurity>   
 <xref:System.Security.AccessControl.MutexAccessRule>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [監視](../Topic/Monitors.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)