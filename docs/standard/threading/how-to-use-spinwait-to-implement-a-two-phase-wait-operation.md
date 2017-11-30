---
title: "方法: SpinWait を使用して 2 フェーズ待機操作を実装する"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>方法: SpinWait を使用して 2 フェーズ待機操作を実装する
次の例を使用する方法を示しています、 <xref:System.Threading.SpinWait?displayProperty=nameWithType> 2 フェーズ待機操作を実装するオブジェクト。 最初のフェーズでは、同期オブジェクトでは、`Latch`ロックが使用可能になるかどうかを確認中に、いくつかのサイクルを回転します。 ロックが使用可能になる場合、2 番目のフェーズでは、`Wait`メソッドを返しますを使用せず、<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>実行待ち状態です。 それ以外の場合、`Wait`は待機を実行します。  
  
## <a name="example"></a>例  
 この例は、プリミティブ ラッチ同期の非常に基本的な実装を示します。 非常に短い待機時間が予想される場合は、このデータ構造体を使用することができます。 この例はデモ目的でのみです。 ラッチ型機能をプログラムで必要とする場合は、使用を検討して<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>です。  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 ラッチを使用して、<xref:System.Threading.SpinWait>オブジェクトを次の呼び出しまでだけ回転`SpinOnce`により、<xref:System.Threading.SpinWait>スレッドのタイム スライスを生成します。 ラッチと呼び出すことによって、独自のコンテキスト スイッチをその時点では、<xref:System.Threading.WaitHandle.WaitOne%2A>上、<xref:System.Threading.ManualResetEvent>とタイムアウト値の残りの部分で渡すことです。  
  
 ラッチを使用せず、ロックを取得することによってパフォーマンスを向上させることがどのくらいの頻度、ログ出力を示しています、<xref:System.Threading.ManualResetEvent>です。  
  
## <a name="see-also"></a>関連項目  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
