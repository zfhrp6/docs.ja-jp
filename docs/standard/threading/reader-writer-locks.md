---
title: "読み取り/書き込みロック"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a>読み取り/書き込みロック
<xref:System.Threading.ReaderWriterLockSlim>クラスにより、複数のスレッドを同時に、リソースを読み取ることがリソースに書き込むために排他ロックを待機するスレッドが必要です。  
  
 使用する場合があります、<xref:System.Threading.ReaderWriterLockSlim>をアプリケーションに共有リソースにアクセスするスレッド間の協調的同期を提供します。 ロックが取得されて、<xref:System.Threading.ReaderWriterLockSlim>自体です。  
  
 任意のスレッド同期機構を使用するスレッドをバイパスできませんによって提供されるロックを確認する必要があります、<xref:System.Threading.ReaderWriterLockSlim>です。 これを実現する 1 つの方法は、共有リソースをカプセル化するクラスをデザインします。 このクラスは、プライベート共有リソースにアクセスする使用されていると、プライベート メンバー<xref:System.Threading.ReaderWriterLockSlim>同期します。 例については、コード例を参照してください、<xref:System.Threading.ReaderWriterLockSlim>クラスです。 <xref:System.Threading.ReaderWriterLockSlim>個々 のオブジェクトを同期するために使用するのに十分なが効率的です。  
  
 読み取りの時間を最小限に抑えるおよび書き込み操作にアプリケーションを構成します。 長い書き込み操作、書き込みロックが排他的なので、直接のスループットに影響します。 操作のブロックの待機中のライターの長い読み取りおよび読み取りアクセス権を要求するスレッドはもブロックされますには、少なくとも 1 つのスレッドが書き込みアクセスを待機している場合。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]が 2 つのリーダー ライター ロック<xref:System.Threading.ReaderWriterLockSlim>と<xref:System.Threading.ReaderWriterLock>です。 <xref:System.Threading.ReaderWriterLockSlim>すべての新しい開発をお勧めします。 <xref:System.Threading.ReaderWriterLockSlim>ような<xref:System.Threading.ReaderWriterLock>再帰、アップグレード、およびロックの状態をダウン グレードの規則が簡素化されますが、します。 <xref:System.Threading.ReaderWriterLockSlim>多くの場合の潜在的なデッドロックを回避できます。 さらに、パフォーマンスの<xref:System.Threading.ReaderWriterLockSlim>よりも大幅に向上が<xref:System.Threading.ReaderWriterLock>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
