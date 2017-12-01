---
title: "方法: SpinLock のスレッド追跡モードを有効にする"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>方法: SpinLock のスレッド追跡モードを有効にする
<xref:System.Threading.SpinLock?displayProperty=nameWithType>非常に短い待機時間が含まれる場合に使用できる低レベルの相互排他ロックです。 <xref:System.Threading.SpinLock>再入可能ではありません。 スレッドがロックに入った後、再入する前に正しくロックを終了にする必要があります。 通常、ロックを再入力しようとすると、デッドロックが発生し、デッドロックをデバッグが非常に困難になることができます。 開発を支援するため<xref:System.Threading.SpinLock?displayProperty=nameWithType>スレッドが既に保持しているロックを再入力しようとしたときにスローされる例外を発生させるスレッド追跡モードをサポートします。 これは、操作により、あるロックが適切に終了しなかったポイントを簡単に特定できます。 使用してスレッド追跡モードをオンすることができます、<xref:System.Threading.SpinLock>をブール値を受け取るコンス トラクターは入力パラメーター、およびの引数を渡すこと`true`です。 開発およびテスト フェーズを完了すると後、は、パフォーマンス向上のためのスレッド追跡モードをオフにします。  
  
## <a name="example"></a>例  
 次の例では、スレッド追跡モードを示します。 ロックを適切に終了する行については、結果は、次のいずれかの原因となるコーディング エラーをシミュレートするためにコメント アウトします。  
  
-   場合、例外がスローされます、<xref:System.Threading.SpinLock>の引数を使用して作成された`true`(`True` Visual Basic で)。  
  
-   デッドロックに陥る、<xref:System.Threading.SpinLock>の引数を使用して作成された`false`(`False` Visual Basic で)。  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>関連項目  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
