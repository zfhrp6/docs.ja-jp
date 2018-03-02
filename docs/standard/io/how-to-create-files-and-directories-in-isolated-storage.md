---
title: "方法 : 分離ストレージでファイルおよびディレクトリを作成する"
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
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf6295e7d58d03e7b4bf4e0a00cfc509d289e071
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="d9d92-102">方法 : 分離ストレージでファイルおよびディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="d9d92-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="d9d92-103">分離ストアを取得したら、データを格納するためのファイルとディレクトリを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="d9d92-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="d9d92-104">ストア内では、ファイル名とディレクトリ名は仮想ファイル システムのルートに対して指定されます。</span><span class="sxs-lookup"><span data-stu-id="d9d92-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="d9d92-105">ディレクトリを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> インスタンス メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9d92-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="d9d92-106">存在しないディレクトリのサブディレクトリを指定した場合、両方のディレクトリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d9d92-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="d9d92-107">既に存在するディレクトリを指定した場合、メソッドはディレクトリを作成せずに制御を返し、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="d9d92-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="d9d92-108">ただし、無効な文字を含むディレクトリ名を指定した場合、<xref:System.IO.IsolatedStorage.IsolatedStorageException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d9d92-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="d9d92-109">ファイルを作成するには、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d9d92-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d9d92-110">Windows オペレーティング システムでは、分離ストレージ ファイルおよびディレクトリの名前の大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="d9d92-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="d9d92-111">つまり、`ThisFile.txt` という名前のファイルを作成してから `THISFILE.TXT` という名前の別のファイルを作成した場合、作成されるのは 1 つのファイルのみです。</span><span class="sxs-lookup"><span data-stu-id="d9d92-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="d9d92-112">ファイル名では、表示目的で元の大文字と小文字の区別が保持されます。</span><span class="sxs-lookup"><span data-stu-id="d9d92-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9d92-113">例</span><span class="sxs-lookup"><span data-stu-id="d9d92-113">Example</span></span>  
 <span data-ttu-id="d9d92-114">分離ストア内にファイルおよびディレクトリを作成する方法を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="d9d92-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d9d92-115">参照</span><span class="sxs-lookup"><span data-stu-id="d9d92-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="d9d92-116">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="d9d92-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
