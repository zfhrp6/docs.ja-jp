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
# <a name="reader-writer-locks"></a><span data-ttu-id="477d5-102">読み取り/書き込みロック</span><span class="sxs-lookup"><span data-stu-id="477d5-102">Reader-Writer Locks</span></span>
<span data-ttu-id="477d5-103"><xref:System.Threading.ReaderWriterLockSlim>クラスにより、複数のスレッドを同時に、リソースを読み取ることがリソースに書き込むために排他ロックを待機するスレッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="477d5-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="477d5-104">使用する場合があります、<xref:System.Threading.ReaderWriterLockSlim>をアプリケーションに共有リソースにアクセスするスレッド間の協調的同期を提供します。</span><span class="sxs-lookup"><span data-stu-id="477d5-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="477d5-105">ロックが取得されて、<xref:System.Threading.ReaderWriterLockSlim>自体です。</span><span class="sxs-lookup"><span data-stu-id="477d5-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="477d5-106">任意のスレッド同期機構を使用するスレッドをバイパスできませんによって提供されるロックを確認する必要があります、<xref:System.Threading.ReaderWriterLockSlim>です。</span><span class="sxs-lookup"><span data-stu-id="477d5-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="477d5-107">これを実現する 1 つの方法は、共有リソースをカプセル化するクラスをデザインします。</span><span class="sxs-lookup"><span data-stu-id="477d5-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="477d5-108">このクラスは、プライベート共有リソースにアクセスする使用されていると、プライベート メンバー<xref:System.Threading.ReaderWriterLockSlim>同期します。</span><span class="sxs-lookup"><span data-stu-id="477d5-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="477d5-109">例については、コード例を参照してください、<xref:System.Threading.ReaderWriterLockSlim>クラスです。</span><span class="sxs-lookup"><span data-stu-id="477d5-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="477d5-110"><xref:System.Threading.ReaderWriterLockSlim>個々 のオブジェクトを同期するために使用するのに十分なが効率的です。</span><span class="sxs-lookup"><span data-stu-id="477d5-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="477d5-111">読み取りの時間を最小限に抑えるおよび書き込み操作にアプリケーションを構成します。</span><span class="sxs-lookup"><span data-stu-id="477d5-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="477d5-112">長い書き込み操作、書き込みロックが排他的なので、直接のスループットに影響します。</span><span class="sxs-lookup"><span data-stu-id="477d5-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="477d5-113">操作のブロックの待機中のライターの長い読み取りおよび読み取りアクセス権を要求するスレッドはもブロックされますには、少なくとも 1 つのスレッドが書き込みアクセスを待機している場合。</span><span class="sxs-lookup"><span data-stu-id="477d5-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="477d5-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]が 2 つのリーダー ライター ロック<xref:System.Threading.ReaderWriterLockSlim>と<xref:System.Threading.ReaderWriterLock>です。</span><span class="sxs-lookup"><span data-stu-id="477d5-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="477d5-115"><xref:System.Threading.ReaderWriterLockSlim>すべての新しい開発をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="477d5-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="477d5-116"><xref:System.Threading.ReaderWriterLockSlim>ような<xref:System.Threading.ReaderWriterLock>再帰、アップグレード、およびロックの状態をダウン グレードの規則が簡素化されますが、します。</span><span class="sxs-lookup"><span data-stu-id="477d5-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="477d5-117"><xref:System.Threading.ReaderWriterLockSlim>多くの場合の潜在的なデッドロックを回避できます。</span><span class="sxs-lookup"><span data-stu-id="477d5-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="477d5-118">さらに、パフォーマンスの<xref:System.Threading.ReaderWriterLockSlim>よりも大幅に向上が<xref:System.Threading.ReaderWriterLock>です。</span><span class="sxs-lookup"><span data-stu-id="477d5-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="477d5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="477d5-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="477d5-120">スレッド化</span><span class="sxs-lookup"><span data-stu-id="477d5-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="477d5-121">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="477d5-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
