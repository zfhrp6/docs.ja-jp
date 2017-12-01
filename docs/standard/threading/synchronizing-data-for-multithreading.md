---
title: "マルチスレッド処理のためのデータの同期"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17eba2f930fda06d643d78c73c117e89ae86928
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="synchronizing-data-for-multithreading"></a>マルチスレッド処理のためのデータの同期
複数のスレッドが同じオブジェクトのプロパティとメソッドを呼び出す場合は、これらの呼び出しを同期することが重要です。 同期しないと、1 つのスレッドが行っていることを別のスレッドが中断し、オブジェクトが無効な状態になってしまう可能性があります。 メンバーがこのように中断されないように保護されているクラスを、スレッドセーフと呼びます。  
  
 共通言語基盤には、インスタンスや静的メンバーへのアクセスを同期するためのいくつかの方法が備わっています。  
  
-   同期されたコード領域。 使用することができます、<xref:System.Threading.Monitor>コード ブロックをだけを同期するためにこのクラスのクラス、またはコンパイラのサポートが必要とパフォーマンスが向上します。  
  
-   手動での同期。 .NET Framework クラス ライブラリによって提供されている同期オブジェクトを使用できます。 参照してください[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)の説明を含む、<xref:System.Threading.Monitor>クラスです。  
  
-   同期されたコンテキスト。 使用することができます、<xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>の単純な自動同期を有効にする<xref:System.ContextBoundObject>オブジェクト。  
  
-   内のコレクション クラス、<xref:System.Collections.Concurrent?displayProperty=nameWithType>名前空間。 これらのクラスには、同期された追加操作および削除操作が組み込まれています。 詳しくは、「[スレッド セーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)」を参照してください。  
  
 共通言語ランタイムにはスレッド モデルが用意されていて、要件に応じたさまざまな方法で同期することができる多数のカテゴリにクラスを分類できます。 次の表に、各同期カテゴリで提供されるフィールドおよびメソッドに対する同期サポートを示します。  
  
|カテゴリ|グローバル フィールド|静的フィールド|静的メソッド|インスタンス フィールド|インスタンス メソッド|特定のコード ブロック|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|同期なし|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|  
|同期されたコンテキスト|いいえ|いいえ|いいえ|はい|はい|いいえ|  
|同期されたコード領域|いいえ|いいえ|マークされている場合にのみ|いいえ|マークされている場合にのみ|マークされている場合にのみ|  
|手動での同期|手動|手動|手動|手動|手動|手動|  
  
## <a name="no-synchronization"></a>同期なし  
 これは、オブジェクトに対する既定の設定です。 すべてのスレッドが、すべてのメソッドまたはフィールドにいつでもアクセスできます。 ただし、これらのオブジェクトにアクセスできるスレッドは一度に 1 つだけです。  
  
## <a name="manual-synchronization"></a>手動での同期  
 .NET Framework クラス ライブラリには、スレッドを同期するための多数のクラスがあります。 「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
## <a name="synchronized-code-regions"></a>同期されたコード領域  
 使用することができます、<xref:System.Threading.Monitor>クラス、またはコードのブロック、インスタンス メソッド、および静的メソッドを同期するためにコンパイラ キーワード。 同期された静的フィールドに対するサポートはありません。  
  
 Visual Basic と C# の両方が、コード ブロックに特定の言語キーワード (C# の `lock` ステートメント、Visual Basic の `SyncLock` ステートメント) のマークを付けることをサポートしています。 スレッドによってコードが実行されると、ロックの取得が試行されます。 別のスレッドによってロックが既に取得されている場合、ロックが使用可能になるまでスレッドはブロックされます。 同期されているコード ブロック部分の実行をスレッドが終了すると、終了方法に関係なく、ロックが解放されます。  
  
> [!NOTE]
>  `lock`と`SyncLock`ステートメントを使用して実装<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>と<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>、他のメソッドの<xref:System.Threading.Monitor>と連携して、同期された地域内で使用できます。  
  
 また、**MethodImplAttribute** および **MethodImplOptions.Synchronized** を使用してメソッドを修飾することもできます。これにより、**Monitor** またはメソッド全体をロックするためのコンパイラ キーワードの 1 つを使用した場合と同じ結果になります。  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>スレッド同期コード領域へのアクセスを待機しているなどのブロッキング操作を中断するために使用します。 **Thread.Interrupt**はのような操作からのスレッドの中断にも使用<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>です。  
  
> [!IMPORTANT]
>  `static` メソッド (Visual Basic では`Shared`) を保護するために、型 (C# の場合は`typeof(MyType)`、Visual Basic の場合は`GetType(MyType)`、C++ の場合は`MyType::typeid`) をロックしないでください。 代わりにプライベート静的オブジェクトを使用します。 同様に、C# の `this` (Visual Basic の場合は `Me`) を使用してインスタンス メソッドをロックしないでください。 代わりにプライベート オブジェクトを使用します。 クラスやインスタンスは、独自のコード以外のコードでもロックできますが、デッドロックやパフォーマンスの問題が発生する可能性があります。  
  
### <a name="compiler-support"></a>コンパイラ サポート  
 Visual Basic と c# の両方を使用する言語のキーワードをサポートして<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>と<xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>オブジェクトをロックします。 Visual Basic は [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) ステートメントをサポートしており、C# は [lock](~/docs/csharp/language-reference/keywords/lock-statement.md) ステートメントをサポートしています。  
  
 両方とも、コード ブロックで例外がスローされると、**lock** または **SyncLock** によって取得されたロックは自動的に解放されます。 C# コンパイラおよび Visual Basic コンパイラは **try**/**finally** ブロックを生成します。tryブロックは先頭に **Monitor.Enter** を含み、**finally** ブロックは **Monitor.Exit** を含みます。 **lock** ブロックまたは **SyncLock** ブロック内部で例外がスローされると、**finally** ハンドラーが実行され、任意のクリーンアップ作業を行えるようになります。  
  
## <a name="synchronized-context"></a>同期されたコンテキスト  
 任意の **ContextBoundObject** で **SynchronizationAttribute** を使用して、すべてのインスタンス メソッドとインスタンス フィールドを同期することができます。 同じコンテキスト ドメイン内のすべてのオブジェクトが同じロックを共有します。 複数のスレッドがメソッドやフィールドにアクセスできますが、これらのオブジェクトに一度にアクセスできるのは 1 つのスレッドだけです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)  
 [同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [SyncLock ステートメント](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock ステートメント](~/docs/csharp/language-reference/keywords/lock-statement.md)
