---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock>構造体は、低レベルで相互排他的な同期プリミティブにロックの取得を待機している間に回転します。 待機時間が短いファイル名と競合が最小限に抑える場合に予想される場合、マルチコア コンピューターでは<xref:System.Threading.SpinLock>他の種類のロックよりも優れてことができます。 ただし、ことをお勧めを使用すること<xref:System.Threading.SpinLock>をプロファイリングして、特定する場合にのみ、<xref:System.Threading.Monitor?displayProperty=nameWithType>メソッドまたは<xref:System.Threading.Interlocked>メソッドは、プログラムのパフォーマンスのパフォーマンスの大幅に低下します。  
  
 <xref:System.Threading.SpinLock>場合でも、それを取得していない、ロック、スレッドのタイム スライスを生成する可能性があります。 これは、スレッドの優先順位の反転を回避し、進捗ガベージ コレクターを有効にします。 使用すると、 <xref:System.Threading.SpinLock>、あるスレッド ロックを保持できるありません非常に短時間の期間より長くなることスレッドがブロックされていないロックを保持していることを確認します。  
  
 スピンロックが値型であるため、明示的に渡す必要があります、参照渡しする場合は、同じロックを参照する 2 つのコピー。  
  
 この型を使用する方法の詳細については、次を参照してください。<xref:System.Threading.SpinLock?displayProperty=nameWithType>です。 例については、次を参照してください。[する方法: 低水準の同期のために使用するスピンロック](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)です。  
  
 <xref:System.Threading.SpinLock>サポートしている、*スレッド*-*追跡*特定の時刻に、ロックが保持しているスレッドを追跡しやすく開発フェーズ中に使用できるモードです。 スレッド追跡モードはデバッグは、非常に便利ですが、オフにすることが、プログラムのリリース バージョンでパフォーマンスが低下する可能性がありますのでことをお勧めします。 詳細については、次を参照してください。[する方法: SpinLock のスレッドを有効にする追跡モード](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
