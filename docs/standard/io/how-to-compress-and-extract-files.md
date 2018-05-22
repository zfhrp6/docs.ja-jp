---
title: '方法 : ファイルを圧縮して抽出する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3e535e13fe91e1a5cb9c868428f5edbb9eac03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compress-and-extract-files"></a>方法 : ファイルを圧縮して抽出する
<xref:System.IO.Compression> 名前空間には、ファイルおよびストリームを圧縮および展開するための次の型が含まれています。 これらの型を使用して、圧縮ファイルの内容を読み取り、変更することもできます。  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 圧縮ファイルを操作するときに実行できる機能の例を次に示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.IO.Compression.ZipFile> クラスを使用して .zip ファイル名拡張子を持つ圧縮ファイルの作成と抽出を行う方法を示しています。 フォルダーの内容を新しい .zip ファイルに圧縮し、その内容を新しいフォルダーに抽出します。 <xref:System.IO.Compression.ZipFile> クラスを使用するには、プロジェクトの `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 次の例は、既存の .zip ファイルの内容を反復処理し、拡張子が .txt のファイルを抽出する方法を示しています。 <xref:System.IO.Compression.ZipArchive> クラスを使用して既存の .zip ファイルにアクセスし、<xref:System.IO.Compression.ZipArchiveEntry> クラスを使用して圧縮ファイル内の個々のエントリを検査します。 <xref:System.IO.Compression.ZipArchiveEntry> オブジェクトの拡張メソッド (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) を使用しています。 拡張メソッドは、<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> クラスで使用できます。 <xref:System.IO.Compression.ZipFileExtensions> クラスを使用するには、プロジェクトの `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.IO.Compression.ZipArchive> クラスを使用して既存の .zip ファイルにアクセスし、新しいファイルを圧縮ファイルに追加します。 新しいファイルは、既存の .zip ファイルに追加するときに圧縮されます。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 また、<xref:System.IO.Compression.GZipStream> クラスと <xref:System.IO.Compression.DeflateStream> クラスを使用してデータを圧縮および展開することもできます。 圧縮と展開には同じ圧縮アルゴリズムが使用されます。 拡張子が .gz のファイルに書き込まれた圧縮済み <xref:System.IO.Compression.GZipStream> オブジェクトは、<xref:System.IO.Compression.GZipStream> で提供されているメソッドに加えて、多くの一般的なツールを使用して展開できます。 この例では、<xref:System.IO.Compression.GZipStream> クラスを使用してファイルのディレクトリを圧縮および展開する方法を示します。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
