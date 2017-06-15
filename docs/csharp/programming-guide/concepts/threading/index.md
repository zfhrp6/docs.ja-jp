---
title: "スレッド処理 (c#) |Microsoft ドキュメント"
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
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: e3f213b43c2f05a5afef1db7aec8b9c2695df989
ms.contentlocale: ja-jp
ms.lasthandoff: 06/15/2017

---
# <a name="threading-c"></a>スレッド処理 (C#)
スレッド処理により、c# プログラムで、一度に 1 つ以上の操作を行うことができるように、同時処理を実行します。 たとえば、スレッド処理を使用をユーザーからの入力を監視、バック グラウンド タスクを実行および入力のストリームを同時に処理します。  
  
 スレッドでは、次のプロパティがあります。  
  
-   スレッドは、同時実行処理を実行するプログラムを有効にします。  
  
-   .NET Framework<xref:System.Threading>名前空間ではスレッドをより簡単に使用します。  
  
-   スレッドは、アプリケーションのリソースを共有します。 詳細については、次を参照してください。[スレッドの使用とスレッド処理](https://msdn.microsoft.com/library/e1dx6b2h)です。  
  
 既定では、c# プログラムは 1 つのスレッドがあります。 ただし、補助スレッドを作成され、プライマリ スレッドで同時にコードを実行するために使用します。 これらのスレッドとも呼ばれます*ワーカー スレッド*です。  
  
 タスクを実行する時間がかかる場合またはタイム クリティカルなプライマリ スレッドを停止せず、ワーカー スレッドを使用できます。 たとえば、ワーカー スレッドは、受信要求を満たすため、前回の要求を完了するを待たずにサーバー アプリケーションで使用多くの場合は。 ワーカー スレッドはデスクトップ アプリケーションで""バック グラウンド タスクを実行にも使用できるように、メイン スレッド--ドライブのユーザー インターフェイス要素--ユーザー アクションへの応答は残ります。  
  
 現在のスループットと応答性の問題を解決するスレッドが、デッドロックや競合状態などのリソースの共有の問題が生じる場合もします。 複数のスレッドは、ファイル ハンドルやネットワーク接続などのさまざまなリソースを必要とするタスクに最適です。 同期に関する問題が発生する可能性は、複数のスレッドを 1 つのリソースに割り当てると、複数のスレッドを使用する目的は達成できない他のスレッドが待機しているときに頻繁にブロックされたスレッドを持ちます。  
  
 一般的な方法では、実行時間のかかるワーカー スレッドまたは他のスレッドによって使用されているリソースの多くを必要としないタイム クリティカルなタスクを使用します。 当然ながら、一部のリソース、プログラムでは、複数のスレッドによってアクセスできなければなりません。 このような場合、<xref:System.Threading>名前空間は、スレッドの同期のクラスを提供します。 これらのクラスを含める<xref:System.Threading.Mutex>、 <xref:System.Threading.Monitor>、 <xref:System.Threading.Interlocked>、 <xref:System.Threading.AutoResetEvent>、および<xref:System.Threading.ManualResetEvent>です。  
  
 、複数のスレッドの活動を同期するためにこれらのクラスの一部またはすべてを使用することができますが、スレッド処理の一部のサポートは、c# 言語でサポートされています。 たとえば、 [Lock ステートメント](../../../../csharp/language-reference/keywords/lock-statement.md)暗黙の型を使用して同期機能を提供<xref:System.Threading.Monitor>です。  
  
> [!NOTE]
>  以降で、 [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)]、マルチ スレッド プログラミングを大幅に簡略化、<xref:System.Threading.Tasks.Parallel?displayProperty=fullName>と<xref:System.Threading.Tasks.Task?displayProperty=fullName>クラス、 [Parallel LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688)、内の新しい同時実行コレクション クラス、<xref:System.Collections.Concurrent?displayProperty=fullName>名前空間、およびスレッドではなく、タスクの概念に基づいている新しいプログラミング モデルです。 詳細については、[並列プログラミング](https://msdn.microsoft.com/library/dd460693)に関するページをご覧ください。  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|作成し、スレッドを使用する方法について説明します。|  
|[パラメーターと戻り値のマルチ スレッド プロシージャ (c#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|マルチ スレッド アプリケーションでパラメーターを渡す方法について説明します。|  
|[チュートリアル: BackgroundWorker コンポーネント (c#) でのマルチ スレッド](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|単純なマルチ スレッド アプリケーションを作成する方法を示します。|  
|[スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|スレッドの相互作用を制御する方法について説明します。|  
|[スレッド タイマー (c#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|一定の間隔で個別のスレッド上の手順を実行する方法について説明します。|  
|[スレッド プール (c#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|システムによって管理されるワーカー スレッドのプールを使用する方法について説明します。|  
|[方法: スレッド プール (c#) を使用します。](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|スレッド プール内の複数のスレッドの同期の使用を示します。|  
|[スレッド化](https://msdn.microsoft.com/library/3e8s7xdd)|.NET Framework でのスレッドを実装する方法について説明します。|
