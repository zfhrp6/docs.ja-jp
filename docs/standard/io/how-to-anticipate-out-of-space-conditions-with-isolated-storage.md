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
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>方法: 分離ストレージの領域不足状態に備える
分離ストレージを使用するコードがによって制約される、[クォータ](../../../docs/standard/io/isolated-storage.md#quotas)データ コンパートメントを分離ストレージ ファイルとディレクトリは存在して最大サイズを指定します。 クォータは、セキュリティ ポリシーによって定義され、管理者が設定します。 サイズを超えると、データを書き込もうとしたときに、最大値が許可された場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外がスローされ、操作は失敗します。 これにより、データ ストレージがいっぱいであるために、要求を拒否するようにアプリケーションを引き起こす可能性のある悪意のあるサービス拒否攻撃を防ぐことができます。  
  
 特定の書き込みが試行はこのため、失敗する可能性があるかどうかを判断する際、<xref:System.IO.IsolatedStorage.IsolatedStorage>クラスには、次の 3 つの読み取り専用プロパティが用意されています: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>、および<xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>です。 これらのプロパティを使用して、ストアへの書き込みが最大許容サイズを超えたストアを引き起こすかどうかを決定することができます。 同時にアクセスできる分離ストレージを注意してください。そのため、残りの記憶域の容量を計算するときに、記憶域スペースによって消費されるストアに書き込むしようとする時間。 ただし、使用可能記憶域の上限に近づいてかどうかを確認するため、ストアの最大サイズを使用することができます。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>プロパティは、適切に機能するアセンブリから証拠によって異なります。 このためでのみこのプロパティを取得する必要があります<xref:System.IO.IsolatedStorage.IsolatedStorageFile>を使用して作成されたオブジェクト、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>、 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>、または<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドです。 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>他の方法で作成されたオブジェクト (から返されたオブジェクトなど、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>メソッド) で正確な最大サイズは返されません。  
  
## <a name="example"></a>例  
 次のコード例は、分離ストアを取得、いくつかのファイルを作成し、取得、<xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>プロパティです。 残りの領域は、バイト単位で報告されます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)  
 [方法: 分離ストレージでストアを取得する](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
