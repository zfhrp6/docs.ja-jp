---
title: タイマー
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="timers"></a>タイマー
タイマーとは、指定時刻に指定のデリゲートを呼び出す軽量オブジェクトのことです。 スレッド プール内の 1 つのスレッドが、待機操作を実行します。  
  
 <xref:System.Threading.Timer?displayProperty=nameWithType> クラスの使用法は単純です。 **Timer** を作成するには、コールバック メソッドへの <xref:System.Threading.TimerCallback> デリゲート、コールバックに渡される状態を表すオブジェクト、最初に発生する時間、コールバック呼び出しの間隔を表す時間を渡します。 保留中のタイマーを取り消すには、**Timer.Dispose** 関数を呼び出します。  
  
> [!NOTE]
>  他にも 2 つのタイマー クラスがあります。 <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> クラスは、ビジュアルなデザイナーを操作するコントロールで、ユーザー インターフェイスのコンテキストで使用するように設計されています。このクラスは、ユーザー インターフェイス スレッドでイベントを発生させます。 <xref:System.Timers.Timer?displayProperty=nameWithType> クラスは <xref:System.ComponentModel.Component> から派生するため、ビジュアルなデザイナーで使用できます。このクラスもイベントを発生させますが、イベントは <xref:System.Threading.ThreadPool> スレッドで発生します。 <xref:System.Threading.Timer?displayProperty=nameWithType> クラスは <xref:System.Threading.ThreadPool> スレッドでコールバックを行い、イベント モデルは使用しません。 またこのクラスは、状態オブジェクトをコールバック メソッドに提供します。他のタイマーは状態オブジェクトを提供しません。 このクラスは、非常に軽量です。  
  
 次のコード例は、1 秒 (1000 ミリ秒) 後に起動し、**Enter** キーを押すまで 1 秒ごとに時を刻むタイマーを開始します。 実行中にタイマーがガベージ コレクションの対象とならないように、このタイマーへの参照を含む変数はクラス レベルのフィールドとします。 積極的なガベージ コレクションの詳細については、「<xref:System.GC.KeepAlive%2A>」を参照してください。  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Timer>  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
