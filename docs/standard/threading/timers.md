---
title: "タイマー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a>タイマー
タイマーとは、指定時刻に指定のデリゲートを呼び出す軽量オブジェクトのことです。 スレッド プール内の 1 つのスレッドが、待機操作を実行します。  
  
 <xref:System.Threading.Timer?displayProperty=nameWithType> クラスの使用法は単純です。 作成する、**タイマー**渡す、<xref:System.Threading.TimerCallback>コールバック、最初に発生時刻、およびコールバック呼び出しの間隔を表す時間に渡される状態を表すオブジェクトをコールバック メソッドにデリゲートします。 保留中のタイマーをキャンセルする、 **Timer.Dispose**関数。  
  
> [!NOTE]
>  他にも 2 つのタイマー クラスがあります。 <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> クラスは、ビジュアルなデザイナーを操作するコントロールで、ユーザー インターフェイスのコンテキストで使用するように設計されています。このクラスは、ユーザー インターフェイス スレッドでイベントを発生させます。 <xref:System.Timers.Timer?displayProperty=nameWithType> クラスは <xref:System.ComponentModel.Component> から派生するため、ビジュアルなデザイナーで使用できます。このクラスもイベントを発生させますが、イベントは <xref:System.Threading.ThreadPool> スレッドで発生します。 <xref:System.Threading.Timer?displayProperty=nameWithType> クラスは <xref:System.Threading.ThreadPool> スレッドでコールバックを行い、イベント モデルは使用しません。 またこのクラスは、状態オブジェクトをコールバック メソッドに提供します。他のタイマーは状態オブジェクトを提供しません。 このクラスは、非常に軽量です。  
  
 次のコード例は、キーを押すまで 1 秒ごとに 1 秒 (1000 ミリ秒) とタイマー刻みの後に開始するタイマーを開始、 **Enter**キー。 実行中にタイマーがガベージ コレクションの対象とならないように、このタイマーへの参照を含む変数はクラス レベルのフィールドとします。 積極的なガベージ コレクションの詳細については、「<xref:System.GC.KeepAlive%2A>」を参照してください。  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Timer>  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
