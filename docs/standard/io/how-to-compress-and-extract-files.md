---
title: "方法 : ファイルを圧縮して抽出する"
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
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33c9249692998aea8c22ddbf75a5a9b7bdf28708
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="d385a-102">方法 : ファイルを圧縮して抽出する</span><span class="sxs-lookup"><span data-stu-id="d385a-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="d385a-103"><xref:System.IO.Compression> 名前空間には、ファイルおよびストリームを圧縮および展開するための次の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d385a-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="d385a-104">これらの型を使用して、圧縮ファイルの内容を読み取り、変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="d385a-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="d385a-105">圧縮ファイルを操作するときに実行できる機能の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d385a-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d385a-106">例</span><span class="sxs-lookup"><span data-stu-id="d385a-106">Example</span></span>  
 <span data-ttu-id="d385a-107">この例では、<xref:System.IO.Compression.ZipFile> クラスを使用して .zip ファイル名拡張子を持つ圧縮ファイルの作成と抽出を行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d385a-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="d385a-108">フォルダーの内容を新しい .zip ファイルに圧縮し、その内容を新しいフォルダーに抽出します。</span><span class="sxs-lookup"><span data-stu-id="d385a-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="d385a-109"><xref:System.IO.Compression.ZipFile> クラスを使用するには、プロジェクトの `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d385a-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d385a-110">例</span><span class="sxs-lookup"><span data-stu-id="d385a-110">Example</span></span>  
 <span data-ttu-id="d385a-111">次の例は、既存の .zip ファイルの内容を反復処理し、拡張子が .txt のファイルを抽出する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d385a-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="d385a-112"><xref:System.IO.Compression.ZipArchive> クラスを使用して既存の .zip ファイルにアクセスし、<xref:System.IO.Compression.ZipArchiveEntry> クラスを使用して圧縮ファイル内の個々のエントリを検査します。</span><span class="sxs-lookup"><span data-stu-id="d385a-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="d385a-113"><xref:System.IO.Compression.ZipArchiveEntry> オブジェクトの拡張メソッド (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="d385a-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="d385a-114">拡張メソッドは、<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> クラスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d385a-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d385a-115"><xref:System.IO.Compression.ZipFileExtensions> クラスを使用するには、プロジェクトの `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d385a-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d385a-116">例</span><span class="sxs-lookup"><span data-stu-id="d385a-116">Example</span></span>  
 <span data-ttu-id="d385a-117">次の例では、<xref:System.IO.Compression.ZipArchive> クラスを使用して既存の .zip ファイルにアクセスし、新しいファイルを圧縮ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d385a-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="d385a-118">新しいファイルは、既存の .zip ファイルに追加するときに圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="d385a-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d385a-119">例</span><span class="sxs-lookup"><span data-stu-id="d385a-119">Example</span></span>  
 <span data-ttu-id="d385a-120">また、<xref:System.IO.Compression.GZipStream> クラスと <xref:System.IO.Compression.DeflateStream> クラスを使用してデータを圧縮および展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="d385a-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="d385a-121">圧縮と展開には同じ圧縮アルゴリズムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d385a-121">They use the same compression algorithm.</span></span> <span data-ttu-id="d385a-122">拡張子が .gz のファイルに書き込まれた圧縮済み <xref:System.IO.Compression.GZipStream> オブジェクトは、<xref:System.IO.Compression.GZipStream> で提供されているメソッドに加えて、多くの一般的なツールを使用して展開できます。</span><span class="sxs-lookup"><span data-stu-id="d385a-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="d385a-123">この例では、<xref:System.IO.Compression.GZipStream> クラスを使用してファイルのディレクトリを圧縮および展開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d385a-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d385a-124">参照</span><span class="sxs-lookup"><span data-stu-id="d385a-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="d385a-125">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="d385a-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
