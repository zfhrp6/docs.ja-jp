---
title: "方法: 分離ストレージの領域不足状態に備える"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="96f0c-102">方法: 分離ストレージの領域不足状態に備える</span><span class="sxs-lookup"><span data-stu-id="96f0c-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="96f0c-103">分離ストレージを使用するコードがによって制約される、[クォータ](../../../docs/standard/io/isolated-storage.md#quotas)データ コンパートメントを分離ストレージ ファイルとディレクトリは存在して最大サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="96f0c-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="96f0c-104">クォータは、セキュリティ ポリシーによって定義され、管理者が設定します。</span><span class="sxs-lookup"><span data-stu-id="96f0c-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="96f0c-105">サイズを超えると、データを書き込もうとしたときに、最大値が許可された場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外がスローされ、操作は失敗します。</span><span class="sxs-lookup"><span data-stu-id="96f0c-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="96f0c-106">これにより、データ ストレージがいっぱいであるために、要求を拒否するようにアプリケーションを引き起こす可能性のある悪意のあるサービス拒否攻撃を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="96f0c-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="96f0c-107">特定の書き込みが試行はこのため、失敗する可能性があるかどうかを判断する際、<xref:System.IO.IsolatedStorage.IsolatedStorage>クラスには、次の 3 つの読み取り専用プロパティが用意されています: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>、および<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>です。</span><span class="sxs-lookup"><span data-stu-id="96f0c-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="96f0c-108">これらのプロパティを使用して、ストアへの書き込みが最大許容サイズを超えたストアを引き起こすかどうかを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="96f0c-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="96f0c-109">同時にアクセスできる分離ストレージを注意してください。そのため、残りの記憶域の容量を計算するときに、記憶域スペースによって消費されるストアに書き込むしようとする時間。</span><span class="sxs-lookup"><span data-stu-id="96f0c-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="96f0c-110">ただし、使用可能記憶域の上限に近づいてかどうかを確認するため、ストアの最大サイズを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="96f0c-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="96f0c-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>プロパティは、適切に機能するアセンブリから証拠によって異なります。</span><span class="sxs-lookup"><span data-stu-id="96f0c-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="96f0c-112">このためでのみこのプロパティを取得する必要があります<xref:System.IO.IsolatedStorage.IsolatedStorageFile>を使用して作成されたオブジェクト、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="96f0c-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="96f0c-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>他の方法で作成されたオブジェクト (から返されたオブジェクトなど、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>メソッド) で正確な最大サイズは返されません。</span><span class="sxs-lookup"><span data-stu-id="96f0c-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f0c-114">例</span><span class="sxs-lookup"><span data-stu-id="96f0c-114">Example</span></span>  
 <span data-ttu-id="96f0c-115">次のコード例は、分離ストアを取得、いくつかのファイルを作成し、取得、<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="96f0c-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="96f0c-116">残りの領域は、バイト単位で報告されます。</span><span class="sxs-lookup"><span data-stu-id="96f0c-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="96f0c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="96f0c-117">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="96f0c-118">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="96f0c-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="96f0c-119">方法: 分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="96f0c-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
