---
title: "マネージ スレッド処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f2a8792818e837f019403aa84c2c2e98db0b2b89
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="managed-threading"></a>マネージ スレッド処理
アプリケーションを開発する場合、対象のコンピューターがプロセッサがシングルまたはマルチのいずれの場合でも、アプリケーションにユーザーとの迅速な対話を提供する必要があります。これはアプリケーションがほかの処理の実行中であっても同じことです。 アプリケーションによるユーザーへの迅速な応答を維持すると同時に、ユーザー イベントの合間やその処理中にプロセッサを使用する最も強力な方法は、複数の実行スレッドを使用することです。 ここでは、スレッド処理の基本概念について、マネージ スレッド処理の概念と使用方法を中心に説明します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=fullName> クラスおよび <xref:System.Threading.Tasks.Task?displayProperty=fullName> クラス、[Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間の新しい同時実行コレクション クラス、スレッドではなくタスクの概念をベースにした新しいプログラミング モデルにより、マルチスレッド プログラミングが大幅に簡略化されています。 詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [マネージ スレッド処理の基本](../../../docs/standard/threading/managed-threading-basics.md)  
 マネージ スレッド処理の概要と、マルチ スレッドをどのようなときに使用するかについて説明します。  
  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)  
 スレッドの作成、開始、一時停止、再開、および中止について説明します。  
  
 [マネージ スレッド処理の実施](../../../docs/standard/threading/managed-threading-best-practices.md)  
 同期のレベル、デッドロックと競合状態の回避方法、シングル プロセッサのコンピューターとマルチ プロセッサのコンピューターの問題など、スレッド処理の各種の注意点について説明します。  
  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 スレッドの動作や、別のスレッドによってアクセスされるオブジェクトのデータを同期するために使用するマネージ クラスについて説明し、スレッド プールのスレッドの概要を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Threading>  
 マネージ スレッドを使用したり同期したりするためのクラスを含みます。  
  
 <xref:System.Collections.Concurrent>  
 複数のスレッドで使用する安全なコレクション クラスを含みます。  
  
 <xref:System.Threading.Tasks>  
 同時処理タスクを作成およびスケジュールするためのクラスを含みます。  
  
## <a name="related-sections"></a>関連項目  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインと、その共通言語インフラストラクチャでの使用に関する概要を示します。  
  
 [非同期ファイル I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 非同期 I/O のパフォーマンス上の利点と基本的な操作について説明します。  
  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 非同期プログラミングの概要を説明します。  
  
 [同期メソッドの非同期呼び出し](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 デリゲートの組み込み機能を使用してスレッド プールのスレッドでメソッドを呼び出す方法を示します。  
  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)  
 アプリケーションで複数のスレッドを簡単に使用できるようにする並列プログラミング ライブラリについて説明します。  
  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 複数のプロセッサを利用するために、クエリを並列で実行するシステムについて説明します。

