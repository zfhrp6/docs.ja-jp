---
title: "方法 : 分離ストレージでストアを列挙する"
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
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="0003a-102">方法 : 分離ストレージでストアを列挙する</span><span class="sxs-lookup"><span data-stu-id="0003a-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="0003a-103">使用して、現在のユーザーのすべての分離ストアを列挙することができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType>静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0003a-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="0003a-104">このメソッドは、<xref:System.IO.IsolatedStorage.IsolatedStorageScope>値を返す、<xref:System.IO.IsolatedStorage.IsolatedStorageFile>列挙子。</span><span class="sxs-lookup"><span data-stu-id="0003a-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="0003a-105">ストアを列挙する必要があります、<xref:System.Security.Permissions.IsolatedStorageFilePermission>を指定するアクセス許可、<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>値。</span><span class="sxs-lookup"><span data-stu-id="0003a-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="0003a-106">呼び出す場合は、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>メソッドを<xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>の配列を返します<xref:System.IO.IsolatedStorage.IsolatedStorageFile>現在のユーザーに対して定義されているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0003a-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0003a-107">例</span><span class="sxs-lookup"><span data-stu-id="0003a-107">Example</span></span>  
 <span data-ttu-id="0003a-108">次のコード例は、ユーザーおよびアセンブリ別に分離されたいくつかのファイルを作成し、使用して、それらのファイルを取得するストアを取得、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0003a-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0003a-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0003a-109">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="0003a-110">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="0003a-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
