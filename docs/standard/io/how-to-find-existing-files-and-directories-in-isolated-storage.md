---
title: "方法 : 分離ストレージ内でファイルおよびディレクトリを検索する"
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
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="968bc-102">方法 : 分離ストレージ内でファイルおよびディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="968bc-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="968bc-103">分離ストレージ内のディレクトリを検索するには、使用、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="968bc-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="968bc-104">このメソッドは、検索パターンを表す文字列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="968bc-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="968bc-105">単一文字 (?) と複数文字 (*) の両方を使用する検索パターンでのワイルドカード文字しますが、名前の最後の部分にワイルドカード文字を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="968bc-105">You can use both single-character (?) and multi-character (*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="968bc-106">たとえば、`directory1/*ect*`は有効な検索文字列が`*ect*/directory2`はありません。</span><span class="sxs-lookup"><span data-stu-id="968bc-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="968bc-107">ファイルを検索するには、使用、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="968bc-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="968bc-108">適用する検索文字列にワイルドカード文字の制限は、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>にも適用されます<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>です。</span><span class="sxs-lookup"><span data-stu-id="968bc-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="968bc-109">どちらの方法は、再帰的です。<xref:System.IO.IsolatedStorage.IsolatedStorageFile>クラスはすべてのディレクトリまたはユーザーのストア内のファイルを一覧表示するためのメソッドを指定していません。</span><span class="sxs-lookup"><span data-stu-id="968bc-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="968bc-110">ただし、再帰的な方法は、次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="968bc-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="968bc-111">例</span><span class="sxs-lookup"><span data-stu-id="968bc-111">Example</span></span>  
 <span data-ttu-id="968bc-112">次のコード例は、分離ストアのファイルとディレクトリを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="968bc-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="968bc-113">ユーザー、ドメイン、およびアセンブリの分離されたストアが取得されに最初に、`isoStore`変数。</span><span class="sxs-lookup"><span data-stu-id="968bc-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="968bc-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A>メソッドを使用して、いくつかの異なるディレクトリを設定し、<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29>コンス トラクターは、これらのディレクトリにいくつかのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="968bc-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="968bc-115">コードがの結果をループ処理し、`GetAllDirectories`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="968bc-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="968bc-116">このメソッドを使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>を現在のディレクトリ内のすべてのディレクトリ名を検索します。</span><span class="sxs-lookup"><span data-stu-id="968bc-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="968bc-117">これらの名前は、配列に格納し、`GetAllDirectories`呼び出し自体が検出する各ディレクトリに渡します。</span><span class="sxs-lookup"><span data-stu-id="968bc-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="968bc-118">その結果、すべてのディレクトリ名は、配列で返されます。</span><span class="sxs-lookup"><span data-stu-id="968bc-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="968bc-119">次に、コードを呼び出して、`GetAllFiles`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="968bc-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="968bc-120">このメソッドを呼び出す`GetAllDirectories`をすべての名前を調べるには、ディレクトリでは、その後チェック ファイルの各ディレクトリを使用して、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="968bc-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="968bc-121">ディスプレイの配列では、結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="968bc-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="968bc-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="968bc-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="968bc-123">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="968bc-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
