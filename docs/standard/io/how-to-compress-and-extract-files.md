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
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="d3a05-102">方法 : ファイルを圧縮して抽出する</span><span class="sxs-lookup"><span data-stu-id="d3a05-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="d3a05-103"><xref:System.IO.Compression>名前空間は、圧縮および圧縮解除ファイルおよびストリームの次の種類を格納します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="d3a05-104">閲覧、圧縮されたファイルの内容を変更してこれらの型を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3a05-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="d3a05-105">次の例では、圧縮されたファイルを操作するときに実行できる機能のいくつかを示します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3a05-106">例</span><span class="sxs-lookup"><span data-stu-id="d3a05-106">Example</span></span>  
 <span data-ttu-id="d3a05-107">この例は、作成しを使用してファイル名拡張子が .zip の圧縮ファイルを抽出する方法を示しています、<xref:System.IO.Compression.ZipFile>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3a05-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="d3a05-108">新しい .zip ファイルに、フォルダーの内容を圧縮し、その新しいフォルダーにそのコンテンツを抽出します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="d3a05-109">使用する、<xref:System.IO.Compression.ZipFile>クラスを参照する必要がある、`System.IO.Compression.FileSystem`プロジェクト内のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="d3a05-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d3a05-110">例</span><span class="sxs-lookup"><span data-stu-id="d3a05-110">Example</span></span>  
 <span data-ttu-id="d3a05-111">次の例では、既存の .zip ファイルの内容を反復処理し、.txt 拡張子を持つファイルを抽出する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="d3a05-112">使用して、<xref:System.IO.Compression.ZipArchive>既存の .zip ファイルにアクセスするクラスと<xref:System.IO.Compression.ZipArchiveEntry>圧縮ファイル内の個々 のエントリを検査するクラス。</span><span class="sxs-lookup"><span data-stu-id="d3a05-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="d3a05-113">拡張メソッドを使用して (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) の<xref:System.IO.Compression.ZipArchiveEntry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d3a05-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="d3a05-114">拡張メソッドがで使用できる、<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3a05-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d3a05-115">使用する、<xref:System.IO.Compression.ZipFileExtensions>クラスを参照する必要がある、`System.IO.Compression.FileSystem`プロジェクト内のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="d3a05-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d3a05-116">例</span><span class="sxs-lookup"><span data-stu-id="d3a05-116">Example</span></span>  
 <span data-ttu-id="d3a05-117">次の例では、<xref:System.IO.Compression.ZipArchive>クラスの既存の .zip ファイルにアクセスして、圧縮ファイルに新しいファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="d3a05-118">既存の .zip ファイルに追加すると、新しいファイルが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="d3a05-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="d3a05-119">例</span><span class="sxs-lookup"><span data-stu-id="d3a05-119">Example</span></span>  
 <span data-ttu-id="d3a05-120">使用することも、<xref:System.IO.Compression.GZipStream>と<xref:System.IO.Compression.DeflateStream>クラスして、データを圧縮します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="d3a05-121">同じ圧縮アルゴリズムを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3a05-121">They use the same compression algorithm.</span></span> <span data-ttu-id="d3a05-122">圧縮された<xref:System.IO.Compression.GZipStream>によって提供されるメソッドだけでなく多くの一般的なツールを使用して、拡張子を持つファイルに書き込まれるオブジェクトの圧縮を解除できる<xref:System.IO.Compression.GZipStream>です。</span><span class="sxs-lookup"><span data-stu-id="d3a05-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="d3a05-123">この例は、圧縮し、を使用してファイルのディレクトリを圧縮解除する方法を示します、<xref:System.IO.Compression.GZipStream>クラスです。</span><span class="sxs-lookup"><span data-stu-id="d3a05-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d3a05-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3a05-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="d3a05-125">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="d3a05-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
