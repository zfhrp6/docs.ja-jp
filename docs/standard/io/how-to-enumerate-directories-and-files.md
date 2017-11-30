---
title: "方法: ディレクトリとファイルを列挙する"
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
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="1e833-102">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="1e833-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="1e833-103">ディレクトリとファイル名の文字列の列挙可能なコレクションを返すメソッドを使用して列挙できます。</span><span class="sxs-lookup"><span data-stu-id="1e833-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="1e833-104">列挙可能なコレクションを返すメソッドを使用することもできます。 <xref:System.IO.DirectoryInfo>、 <xref:System.IO.FileInfo>、または<xref:System.IO.FileSystemInfo>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1e833-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="1e833-105">列挙可能なコレクションは、ディレクトリおよびファイルの大規模なコレクションを操作する場合、配列よりも優れたパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e833-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="1e833-106">指定するこれらのメソッドから取得した列挙可能なコレクションを使用することができます、<xref:System.Collections.Generic.IEnumerable%601>などのコレクションのコンス トラクターのパラメーターのクラス、<xref:System.Collections.Generic.List%601>クラスです。</span><span class="sxs-lookup"><span data-stu-id="1e833-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="1e833-107">ディレクトリまたはファイルの名前のみを取得する場合は、列挙メソッドを使用して、<xref:System.IO.Directory>クラスです。</span><span class="sxs-lookup"><span data-stu-id="1e833-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="1e833-108">ディレクトリまたはファイルの他のプロパティを取得する場合は、使用、<xref:System.IO.DirectoryInfo>と<xref:System.IO.FileSystemInfo>クラスです。</span><span class="sxs-lookup"><span data-stu-id="1e833-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="1e833-109">次の表は、列挙可能なコレクションを返す方法のガイドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1e833-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="1e833-110">列挙するには</span><span class="sxs-lookup"><span data-stu-id="1e833-110">To enumerate</span></span>|<span data-ttu-id="1e833-111">列挙可能なコレクションを返す</span><span class="sxs-lookup"><span data-stu-id="1e833-111">Enumerable collection to return</span></span>|<span data-ttu-id="1e833-112">使用する方法</span><span class="sxs-lookup"><span data-stu-id="1e833-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="1e833-113">ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="1e833-113">Directories</span></span>|<span data-ttu-id="1e833-114">ディレクトリ名</span><span class="sxs-lookup"><span data-stu-id="1e833-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="1e833-115">ディレクトリ情報 (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="1e833-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1e833-116">ファイル</span><span class="sxs-lookup"><span data-stu-id="1e833-116">Files</span></span>|<span data-ttu-id="1e833-117">ファイル名</span><span class="sxs-lookup"><span data-stu-id="1e833-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="1e833-118">ファイルの情報 (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="1e833-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1e833-119">ファイル システム情報</span><span class="sxs-lookup"><span data-stu-id="1e833-119">File system information</span></span>|<span data-ttu-id="1e833-120">ファイル システム エントリ</span><span class="sxs-lookup"><span data-stu-id="1e833-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="1e833-121">ファイル システム情報 (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="1e833-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="1e833-122">使用してすぐに親ディレクトリのサブディレクトリにあるすべてのファイルを列挙できますが、<xref:System.IO.SearchOption.AllDirectories>によって提供されるオプションの検索、<xref:System.IO.SearchOption>列挙型、不正アクセス例外 (<xref:System.UnauthorizedAccessException>)、列挙型があります。完了していません。</span><span class="sxs-lookup"><span data-stu-id="1e833-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="1e833-123">これらの例外が可能な場合は、例外をキャッチし、最初にディレクトリを列挙して、ファイルを列挙して続行できます。</span><span class="sxs-lookup"><span data-stu-id="1e833-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="1e833-124">ディレクトリ名を列挙するには</span><span class="sxs-lookup"><span data-stu-id="1e833-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="1e833-125">使用して、<xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>メソッドを指定されたパス内の最上位レベルのディレクトリ名の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="1e833-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="1e833-126">ディレクトリとサブディレクトリ内のファイル名を列挙するには</span><span class="sxs-lookup"><span data-stu-id="1e833-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="1e833-127">使用して、<xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType>ディレクトリと (必要に応じて) そのサブディレクトリを検索して、指定した検索パターンに一致するファイル名の一覧を取得する方法です。</span><span class="sxs-lookup"><span data-stu-id="1e833-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="1e833-128">DirectoryInfo オブジェクトのコレクションを列挙するには</span><span class="sxs-lookup"><span data-stu-id="1e833-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="1e833-129">使用して、<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>最上位のディレクトリのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e833-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="1e833-130">すべてのディレクトリに FileInfo オブジェクトのコレクションを列挙するには</span><span class="sxs-lookup"><span data-stu-id="1e833-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="1e833-131">使用して、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>すべてのディレクトリ内の指定した検索パターンに一致するファイルのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="1e833-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="1e833-132">この例では、まず考えられる不正アクセス例外をキャッチする最上位のディレクトリを列挙し、ファイルを列挙します。</span><span class="sxs-lookup"><span data-stu-id="1e833-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1e833-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e833-133">See Also</span></span>  
 [<span data-ttu-id="1e833-134">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="1e833-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
