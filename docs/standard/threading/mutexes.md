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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1d69c1b943d15b9ad8c80b4d7dbafebc54990ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mutexes"></a>ミューテックス
使用することができます、<xref:System.Threading.Mutex>リソースへの排他アクセスを提供するオブジェクト。 <xref:System.Threading.Mutex>クラスよりも多くのシステム リソースを使用して、<xref:System.Threading.Monitor>クラスが、それをアプリケーション ドメインの境界を越えてマーシャ リングできる、複数の待機時間で使えるおよび異なるプロセスでスレッドを同期するために使用できます。 マネージ同期メカニズムの比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 コード例については、リファレンス ドキュメントを参照して、<xref:System.Threading.Mutex.%23ctor%2A>コンス トラクターです。  
  
## <a name="using-mutexes"></a>ミューテックスの使用  
 スレッドが呼び出す、<xref:System.Threading.WaitHandle.WaitOne%2A>所有権を要求するミュー テックスのメソッドです。 この呼び出しは、ミューテックスを使用できるようになるまで、あるいはオプションのタイムアウト期間を超過するまでブロックします。 所有しているスレッドがない場合、ミューテックスはシグナル状態になります。  
  
 スレッドが呼び出すことにより、ミュー テックスを解放その<xref:System.Threading.Mutex.ReleaseMutex%2A>メソッドです。 ミューテックスにはスレッド アフィニティがあります。つまり、ミューテックスはそれを所有するスレッドによってのみ解放することができます。 スレッドが所有していないミュー テックスを解放する場合、<xref:System.ApplicationException>スレッドでスローされます。  
  
 <xref:System.Threading.Mutex>クラスから派生<xref:System.Threading.WaitHandle>、静的なを呼び出すこともできます<xref:System.Threading.WaitHandle.WaitAll%2A>または<xref:System.Threading.WaitHandle.WaitAny%2A>のメソッド<xref:System.Threading.WaitHandle>の所有権を要求する、<xref:System.Threading.Mutex>を他の組み合わせでは、待機ハンドル。  
  
 スレッドが所有している場合、 <xref:System.Threading.Mutex>、スレッド、同じを指定することができます<xref:System.Threading.Mutex>; の実行をブロックすることがなく待機要求の連続呼び出しでただし、そのリリースする必要があります、<xref:System.Threading.Mutex>所有権を解放する回数だけです。  
  
## <a name="abandoned-mutexes"></a>破棄済みミューテックス  
 スレッドが解放せずに終了した場合、 <xref:System.Threading.Mutex>、ミュー テックスを破棄すると言います。 ミューテックスが保護しているリソースが矛盾した状態で残る可能性があるため、多くの場合、これは重大なプログラミング エラーを示します。 .NET framework version 2.0 では、<xref:System.Threading.AbandonedMutexException>ミュー テックスを取得する次のスレッドでスローされます。  
  
> [!NOTE]
>  .NET Framework version 1.0 および 1.1 では、破棄済み、<xref:System.Threading.Mutex>取得所有権のスレッドが待機してと次のシグナルの状態に設定します。 スレッドが待機していない場合、<xref:System.Threading.Mutex>シグナルの状態のままになります。 例外をスローすることはありません。  
  
 システム全体でミューテックスが有効な場合にミューテックスが破棄されたときは、アプリケーションが強制終了されたことを示している可能性があります (たとえば、Windows タスク マネージャを使用した終了)。  
  
## <a name="local-and-system-mutexes"></a>ローカル ミューテックスとシステム ミューテックス  
 ミュー テックスには、ローカル ミューテックスと名前付きシステム ミューテックスという 2 つの種類があります。 作成する場合、<xref:System.Threading.Mutex>オブジェクトの名前を受け取るコンス トラクターを使用してその名前のオペレーティング システム オブジェクトに関連付けられています。 名前付きシステム ミューテックスは、オペレーティング システム全体から参照でき、プロセスの動作を同期するために使用できます。 複数作成できます<xref:System.Threading.Mutex>名前付きシステム ミュー テックスを同じを表すオブジェクトと、使用することができます、<xref:System.Threading.Mutex.OpenExisting%2A>を開くには、既存のメソッドに名前付きシステム ミュー テックスです。  
  
 ローカル ミューテックスは、現在のプロセス内にのみ存在します。 ローカルへの参照を含むプロセス内の任意のスレッドで使用できます<xref:System.Threading.Mutex>オブジェクト。 各<xref:System.Threading.Mutex>オブジェクトが別のローカル ミュー テックスです。  
  
### <a name="access-control-security-for-system-mutexes"></a>システム ミューテックスのアクセス制御セキュリティ  
 .NET Framework Version 2.0 では、名前付きシステム オブジェクトに対して Windows アクセス制御セキュリティを照会して設定できます。 システム オブジェクトはグローバルであり、所有するコード以外のコードによってロックできるため、作成時からシステム ミューテックスを保護することをお勧めします。  
  
 ミュー テックスのアクセス制御セキュリティについては、次を参照してください、<xref:System.Security.AccessControl.MutexSecurity>と<xref:System.Security.AccessControl.MutexAccessRule>、クラス、<xref:System.Security.AccessControl.MutexRights>列挙体、 <xref:System.Threading.Mutex.GetAccessControl%2A>、 <xref:System.Threading.Mutex.SetAccessControl%2A>、と<xref:System.Threading.Mutex.OpenExisting%2A>のメソッド、<xref:System.Threading.Mutex>クラス、および、 。<xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>コンス トラクターです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)
