---
title: "マネージ スレッド処理の基本"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62c207f6074e33813887c6903f5285ee72d14e85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="managed-threading-basics"></a>マネージ スレッド処理の基本
このセクションの最初の 5 つのトピックでは、どのようなときか、マネージ スレッド処理を使用して、いくつかの基本的な機能について説明します。 その他の機能を提供するクラスについては、次を参照してください。[スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)と[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)です。  
  
 このセクションでカバーのトピックの残りの部分には、Windows オペレーティング システムとマネージ スレッド処理とのやり取りなどのトピックが高度な。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、タスク並列ライブラリおよび PLINQ は、マルチ スレッド プログラムでのタスクとデータの並列処理の Api を提供します。 詳細については、[並列プログラミング](../../../docs/standard/parallel-programming/index.md)に関するページをご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)  
 利点と、複数のスレッドの欠点について説明しするまたはスレッドを作成する場合があります、スレッド プールのスレッドを使用できるシナリオの概要を示します。  
  
 [マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 具体的には、ような状況で異なるバージョンの .NET Framework 用のスレッドでハンドルされない例外の動作を説明するその結果、アプリケーションの終了にします。  
  
 [マルチスレッド処理のためのデータの同期](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 複数のスレッドで使用されるクラスのデータを同期する方法について説明します。  
  
 [マネージ スレッドの状態](../../../docs/standard/threading/managed-thread-states.md)  
 基本的なスレッドの状態と、スレッドが実行されているかどうかを検出する方法を説明します。  
  
 [フォアグラウンド スレッドとバックグラウンド スレッド](../../../docs/standard/threading/foreground-and-background-threads.md)  
 フォア グラウンドとバック グラウンド スレッド間の相違点をについて説明します。  
  
 [Windows でのマネージ スレッド処理とアンマネージ スレッド処理](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 マネージ コードとアンマネージ スレッド処理の間のリレーションシップについて説明します、リスト相当するマネージ スレッド処理 Api、Windows 用および COM アパートメントおよびマネージ スレッドの相互作用について説明します。  
  
 [Thread.Suspend、ガベージ コレクション、およびセーフ ポイント](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 スレッドの中断、ガベージ コレクションをについて説明します。  
  
 [スレッド ローカル ストレージ: スレッド相対静的フィールドとデータ スロット](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 スレッドごとの相対ストレージ機構をについて説明します。  
  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 非同期操作または長時間同期操作について説明します、キャンセル トークンを使用して取り消されたことができます。  
  
## <a name="reference"></a>参照  
 <xref:System.Threading.Thread>  
 **Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 実装する安全な方法は、ユーザー インターフェイス オブジェクトと共にマルチ スレッドです。  
  
## <a name="related-sections"></a>関連項目  
 [同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 複数のスレッドの活動を同期するために使用するマネージ クラスについて説明します。  
  
 [マネージ スレッド処理の実施](../../../docs/standard/threading/managed-threading-best-practices.md)  
 に関する一般的な問題について説明するマルチ スレッドおよび問題を回避するための方法です。  
  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)  
 タスク並列ライブラリおよび PLINQ では、非同期およびマルチ スレッドの .NET Framework アプリケーションを作成する作業を大幅に簡素化について説明します。
