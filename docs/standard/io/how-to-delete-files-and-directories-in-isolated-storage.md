---
title: "方法 : 分離ストレージでファイルおよびディレクトリを削除する"
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
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="03c59-102">方法 : 分離ストレージでファイルおよびディレクトリを削除する</span><span class="sxs-lookup"><span data-stu-id="03c59-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="03c59-103">ディレクトリと、分離ストレージ ファイル内のファイルを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="03c59-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="03c59-104">ストア内でファイルとディレクトリの名前はオペレーティング システムに依存、仮想ファイル システムのルートに対して相対的に指定されました。</span><span class="sxs-lookup"><span data-stu-id="03c59-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="03c59-105">Windows オペレーティング システムで区別することはできません。</span><span class="sxs-lookup"><span data-stu-id="03c59-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="03c59-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>クラスは、ディレクトリとファイルを削除するための 2 つのメソッドを提供します。:<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>と<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>です。</span><span class="sxs-lookup"><span data-stu-id="03c59-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="03c59-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException>ファイルまたは存在しないディレクトリを削除しようとする場合に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="03c59-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="03c59-108">名前にワイルドカード文字を含める場合は<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>をスロー、<xref:System.IO.IsolatedStorage.IsolatedStorageException>例外、および<xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>をスロー、<xref:System.ArgumentException>例外。</span><span class="sxs-lookup"><span data-stu-id="03c59-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="03c59-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>メソッド ディレクトリには、任意のファイルまたはサブディレクトリが含まれている場合は失敗します。</span><span class="sxs-lookup"><span data-stu-id="03c59-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="03c59-110">使用することができます、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>と<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>を既存のファイルとディレクトリを取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="03c59-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="03c59-111">ストアの仮想ファイル システムを検索する方法に関する詳細については、次を参照してください。[する方法: 既存のファイルを検索し、分離ストレージ内のディレクトリ](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)です。</span><span class="sxs-lookup"><span data-stu-id="03c59-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03c59-112">例</span><span class="sxs-lookup"><span data-stu-id="03c59-112">Example</span></span>  
 <span data-ttu-id="03c59-113">次のコード例では、作成し、いくつかのディレクトリとファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="03c59-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="03c59-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="03c59-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="03c59-115">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="03c59-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
