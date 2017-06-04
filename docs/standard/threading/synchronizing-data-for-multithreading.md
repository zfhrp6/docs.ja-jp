---
title: "Synchronizing Data for Multithreading | Microsoft Docs"
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
  - "synchronization, threads"
  - "threading [.NET Framework], synchronizing threads"
  - "managed threading"
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Synchronizing Data for Multithreading
複数のスレッドが同じオブジェクトのプロパティとメソッドを呼び出す場合は、これらの呼び出しを同期することが重要です。  同期しないと、1 つのスレッドが行っていることを別のスレッドが中断し、オブジェクトが無効な状態になってしまうことがあります。  メンバーがこのような干渉を受けないように保護されているクラスを、スレッド セーフと呼びます。  
  
 共通言語基盤には、インスタンスと静的メンバーへのアクセスを同期するいくつかの方法が用意されています。  
  
-   同期されたコード領域。  <xref:System.Threading.Monitor> クラス、またはこのクラスのコンパイラ サポートを使用して、パフォーマンスを向上させながら、同期を必要とするコード ブロックだけを同期できます。  
  
-   手動同期。  .NET Framework クラス ライブラリに用意されている同期オブジェクトを使用できます。  <xref:System.Threading.Monitor> クラスについての説明が記載されている「[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
-   同期されたコンテキスト。  <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> を使用すると、<xref:System.ContextBoundObject> オブジェクトに対して単純な自動同期を有効にできます。  
  
-   <xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間のコレクション クラス。  これらのクラスには、同期された追加操作および削除操作が組み込まれています。  詳細については、「[スレッド セーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)」を参照してください。  
  
 共通言語ランタイムにはスレッド モデルが用意されていて、要件に応じたさまざまな方法で同期することができる多数のカテゴリにクラスを分類できます。  次の表で、各同期カテゴリで提供されるフィールドおよびメソッドに対する同期サポートを示します。  
  
|分類|グローバル フィールド|静的フィールド|静的メソッド|インスタンス フィールド|インスタンス メソッド|特定のコード ブロック|  
|--------|-----------------|-------------|------------|------------------|-----------------|-----------------|  
|同期なし|No|No|No|No|No|No|  
|同期されたコンテキスト|No|No|No|Yes|Yes|No|  
|同期されたコード領域|No|No|マークされている場合のみ|No|マークされている場合のみ|マークされている場合のみ|  
|手動同期|手動|手動|手動|手動|手動|手動|  
  
## 同期なし  
 これは、オブジェクトに対する既定の設定です。  どのスレッドも、すべてのメソッドやフィールドにいつでもアクセスできます。  ただし、これらのオブジェクトにアクセスできるスレッドは一度に 1 つだけです。  
  
## 手動同期  
 .NET Framework クラス ライブラリには、スレッドを同期するためのさまざまなクラスが用意されています。  「[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
## 同期されたコード領域  
 <xref:System.Threading.Monitor> クラスまたはコンパイラ キーワードを使用して、コード ブロック、インスタンス メソッド、および静的メソッドを同期できます。  同期された静的フィールドはサポートされません。  
  
 Visual Basic および C\# のいずれも、コード ブロックに特定の言語キーワードのマークを付けることをサポートしています。特定の言語キーワードとは、C\# では `lock` ステートメント、Visual Basic では `SyncLock` ステートメントです。  コードがスレッドによって実行されると、ロックの取得が試みられます。  ロックが既に別のスレッドに取得されている場合は、ロックが使用できるようになるまで、そのスレッドがブロックされます。  同期されているコード ブロック部分の実行をスレッドが終了すると、終了方法に関係なく、ロックが解放されます。  
  
> [!NOTE]
>  `lock` ステートメントおよび `SyncLock` ステートメントは、<xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> および <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> を使用して実装されるため、<xref:System.Threading.Monitor> の他のメソッドを、同期された領域内でこれらと組み合わせて使用できます。  
  
 また、メソッドを **MethodImplAttribute** および **MethodImplOptions.Synchronized** で修飾することもできます。この処理は、**Monitor** またはメソッド全体をロックするためのコンパイラ キーワードの 1 つを使用した場合と同じ結果になります。  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> を使用すると、同期されたコード領域へのアクセスの待機などのブロック操作から、スレッドを切り離すことができます。  また、この **Thread.Interrupt** を使用することで、<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> などの操作からスレッドを切り離すこともできます。  
  
> [!IMPORTANT]
>  `static` メソッド \(Visual Basic では `Shared` メソッド\) をプロテクトするために、型 \(C\# の `typeof(MyType)`、Visual Basic の `GetType(MyType)`、または C\+\+ の `MyType::typeid`\) をロックしないでください。  代わりに、プライベート静的オブジェクトを使用してください。  同様に、C\# の `this` \(Visual Basic の場合は `Me`\) を使用してインスタンス メソッドをロックしないでください。  代わりに、プライベート オブジェクトを使用してください。  クラスまたはインスタンスは、独自のコード以外のコードでもロックできますが、デッドロックやパフォーマンス上の問題を引き起こす可能性があります。  
  
### コンパイラ サポート  
 Visual Basic と C\# は、どちらも <xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName> と <xref:System.Threading.Monitor.Exit%2A?displayProperty=fullName> を使用してオブジェクトをロックする言語キーワードをサポートします。  Visual Basic は [SyncLock](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md) ステートメントをサポートし、C\# は [lock](../Topic/lock%20Statement%20\(C%23%20Reference\).md) ステートメントをサポートします。  
  
 どちらの場合も、コード ブロックで例外がスローされると、**lock** または **SyncLock** によって取得されたロックが自動的に解放されます。  C\# コンパイラおよび Visual Basic コンパイラは、**try** ブロックおよび **finally** ブロックを生成します。try ブロックは先頭に **Monitor.Enter** を含み、**finally** ブロックは **Monitor.Exit** を含みます。  **lock** ブロックまたは **SyncLock** ブロック内で例外がスローされると、**finally** ハンドラーが実行されて、任意のクリーンアップ処理を実行できるようになります。  
  
## 同期されたコンテキスト  
 任意の **ContextBoundObject** で **SynchronizationAttribut** を使用して、すべてのインスタンス メソッドおよびインスタンス フィールドを同期できます。  同じコンテキスト ドメイン内のすべてのオブジェクトは、同じロックを共有します。  複数のスレッドがメソッドやフィールドにアクセスできますが、これらのオブジェクトに一度にアクセスできるのは 1 つのスレッドだけです。  
  
## 参照  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)   
 [SyncLock Statement](../../../ocs/visual-basic/language-reference/statements/synclock-statement.md)   
 [lock ステートメント](../Topic/lock%20Statement%20\(C%23%20Reference\).md)