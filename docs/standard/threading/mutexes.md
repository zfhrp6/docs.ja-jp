---
title: "ミューテックス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2804d0c60657623b558d86386c5e1043422b648c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="mutexes"></a>ミューテックス
<xref:System.Threading.Mutex> オブジェクトを使用して、リソースへの排他的アクセスを提供できます。 <xref:System.Threading.Mutex> クラスは <xref:System.Threading.Monitor> クラスよりも多くのシステム リソースを使用しますが、アプリケーション ドメイン境界を越えてマーシャリングしたり、複数の待機操作とともに使用したり、異なるプロセスのスレッドを同期するために使用できます。 マネージ同期メカニズムの比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 コード例については、<xref:System.Threading.Mutex.%23ctor%2A> コンストラクターのリファレンス ドキュメントを参照してください。  
  
## <a name="using-mutexes"></a>ミューテックスの使用  
 スレッドはミューテックスの <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドを呼び出して、所有権を要求します。 この呼び出しは、ミューテックスを使用できるようになるまで、あるいはオプションのタイムアウト期間を超過するまでブロックします。 所有しているスレッドがない場合、ミューテックスはシグナル状態になります。  
  
 スレッドは <xref:System.Threading.Mutex.ReleaseMutex%2A> メソッドを呼び出して、ミューテックスを解放します。 ミューテックスにはスレッド アフィニティがあります。つまり、ミューテックスはそれを所有するスレッドによってのみ解放することができます。 スレッドが所有していないミューテックスを解放すると、スレッドで <xref:System.ApplicationException> がスローされます。  
  
 <xref:System.Threading.Mutex> クラスは <xref:System.Threading.WaitHandle> から派生するため、<xref:System.Threading.WaitHandle> の静的な <xref:System.Threading.WaitHandle.WaitAll%2A> または <xref:System.Threading.WaitHandle.WaitAny%2A> メソッドを呼び出し、他の待機ハンドルと組み合わせで <xref:System.Threading.Mutex> の所有権を要求することもできます。  
  
 スレッドが <xref:System.Threading.Mutex> を所有している場合、そのスレッドは待機要求呼び出しを繰り返し行うときに、実行をブロックせずに同じ <xref:System.Threading.Mutex> を指定できます。ただし、呼び出しと同じ回数だけ <xref:System.Threading.Mutex> を解放して、その所有権を解放する必要があります。  
  
## <a name="abandoned-mutexes"></a>破棄済みミューテックス  
 <xref:System.Threading.Mutex> を解放せずにスレッドが終了すると、ミューテックスは破棄されたと見なされます。 ミューテックスが保護しているリソースが矛盾した状態で残る可能性があるため、多くの場合、これは重大なプログラミング エラーを示します。 .NET Framework Version 2.0 では、ミューテックスを取得する次のスレッドで <xref:System.Threading.AbandonedMutexException> がスローされます。  
  
> [!NOTE]
>  .NET Framework Version 1.0 および 1.1 では、破棄された <xref:System.Threading.Mutex> はシグナル状態に設定され、次の待機スレッドが所有権を取得します。 待機しているスレッドがない場合、<xref:System.Threading.Mutex> はシグナル状態のままになります。 例外をスローすることはありません。  
  
 システム全体でミューテックスが有効な場合にミューテックスが破棄されたときは、アプリケーションが強制終了されたことを示している可能性があります (たとえば、Windows タスク マネージャを使用した終了)。  
  
## <a name="local-and-system-mutexes"></a>ローカル ミューテックスとシステム ミューテックス  
 ミュー テックスには、ローカル ミューテックスと名前付きシステム ミューテックスという 2 つの種類があります。 名前を受け入れるコンストラクターを使用して <xref:System.Threading.Mutex> オブジェクトを作成すると、そのオブジェクトがその名前のオペレーティング システム オブジェクトに関連付けられます。 名前付きシステム ミューテックスは、オペレーティング システム全体から参照でき、プロセスの動作を同期するために使用できます。 同じ名前付きシステム ミューテックスを表す複数の <xref:System.Threading.Mutex> オブジェクトを作成できます。また、<xref:System.Threading.Mutex.OpenExisting%2A> メソッドを使用して、既存の名前付きシステム ミューテックスを開くことができます。  
  
 ローカル ミューテックスは、現在のプロセス内にのみ存在します。 ローカル <xref:System.Threading.Mutex> オブジェクトを参照するプロセス内のすべてのスレッドから使用できます。 <xref:System.Threading.Mutex> オブジェクトはそれぞれ別のローカル ミューテックスです。  
  
### <a name="access-control-security-for-system-mutexes"></a>システム ミューテックスのアクセス制御セキュリティ  
 .NET Framework Version 2.0 では、名前付きシステム オブジェクトに対して Windows アクセス制御セキュリティを照会して設定できます。 システム オブジェクトはグローバルであり、所有するコード以外のコードによってロックできるため、作成時からシステム ミューテックスを保護することをお勧めします。  
  
 ミューテックスのアクセス制御セキュリティについては、<xref:System.Security.AccessControl.MutexSecurity> および <xref:System.Security.AccessControl.MutexAccessRule> クラス、<xref:System.Security.AccessControl.MutexRights> 列挙体、<xref:System.Threading.Mutex> クラスの <xref:System.Threading.Mutex.GetAccessControl%2A>、<xref:System.Threading.Mutex.SetAccessControl%2A>、<xref:System.Threading.Mutex.OpenExisting%2A> メソッド、<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> コンストラクターに関するページを参照してください。  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)
