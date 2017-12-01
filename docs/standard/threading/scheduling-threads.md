---
title: "スレッドのスケジューリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a>スレッドのスケジューリング
すべてのスレッドが、スレッド優先順位が割り当てられます。 共通言語ランタイム内で作成されたスレッドは、の優先順位を割り当てられた最初に**ThreadPriority.Normal**です。 ランタイム外部で作成されたスレッドは、マネージ環境に入る前にされていた優先順位を保持します。 取得またはとの任意のスレッドの優先順位を設定することができます、 **Thread.Priority**プロパティです。  
  
 優先度に基づいて実行するためのスレッドがスケジュールされます。 場合でも、ランタイム内のスレッドが、すべてのスレッドは、オペレーティング システムでプロセッサのタイム スライスを割り当てられます。 スレッドが実行される順序を決定するために使用するスケジューリング アルゴリズムの詳細については、各オペレーティング システムによって異なります。 いくつかのオペレーティング システムでは、最初に実行する (実行可能なスレッド) の優先順位が高いスレッドが常にスケジュールします。 優先順位が同じ複数のスレッドが使用可能なすべての場合は、スケジューラを循環その優先順位にあるスレッドの各スレッドに実行するための固定されたタイム スライスを提供します。 優先順位の高いスレッドが実行できるように、実行する優先度の低いスレッドは発生しません。 指定された優先順位で実行可能なスレッドがある場合は、スケジューラは優先順位の低い [次へ] に移動し、実行の優先度のスレッドをスケジュールします。 高い優先順位のスレッドが実行可能になった場合は、低い優先順位のスレッドがプリエンプションの対象し、優先順位の高いスレッドをもう一度実行できます。 上に、オペレーティング システムことができますもスレッドの優先順位を動的に調整、アプリケーションのユーザー インターフェイスがフォア グラウンドとバック グラウンドの間で移動されるとします。 他のオペレーティング システムは、別のスケジューリング アルゴリズムを使用することもできます。  
  
## <a name="see-also"></a>関連項目  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Windows でのマネージ スレッド処理とアンマネージ スレッド処理](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
