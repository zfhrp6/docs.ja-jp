---
title: '方法 : 分離ストレージ内でファイルの読み取りと書き込みを行う'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90195e4e1a368f8b8b0fcf04fd8d86afce3ea7c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="1598a-102">方法 : 分離ストレージ内でファイルの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="1598a-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="1598a-103">分離ストアのファイルを読み取ったり、それに書き込んだりするには、ストリーム リーダー (<xref:System.IO.StreamReader> オブジェクト) またはストリーム ライター (<xref:System.IO.StreamWriter> オブジェクト) で <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1598a-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1598a-104">例</span><span class="sxs-lookup"><span data-stu-id="1598a-104">Example</span></span>  
 <span data-ttu-id="1598a-105">次のコード例では、分離ストアを取得し、ストア内に TestStore.txt をという名前のファイルが存在するかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="1598a-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="1598a-106">存在しない場合、ファイルが作成され、"Hello Isolated Storage" とファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="1598a-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="1598a-107">TestStore.txt が既に存在する場合、コード例は、ファイルから読み取られます。</span><span class="sxs-lookup"><span data-stu-id="1598a-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="1598a-108">参照</span><span class="sxs-lookup"><span data-stu-id="1598a-108">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [<span data-ttu-id="1598a-109">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="1598a-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="1598a-110">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="1598a-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
