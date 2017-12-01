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
# <a name="how-to-compress-and-extract-files"></a>方法 : ファイルを圧縮して抽出する
<xref:System.IO.Compression>名前空間は、圧縮および圧縮解除ファイルおよびストリームの次の種類を格納します。 閲覧、圧縮されたファイルの内容を変更してこれらの型を使用することもできます。  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 次の例では、圧縮されたファイルを操作するときに実行できる機能のいくつかを示します。  
  
## <a name="example"></a>例  
 この例は、作成しを使用してファイル名拡張子が .zip の圧縮ファイルを抽出する方法を示しています、<xref:System.IO.Compression.ZipFile>クラスです。 新しい .zip ファイルに、フォルダーの内容を圧縮し、その新しいフォルダーにそのコンテンツを抽出します。 使用する、<xref:System.IO.Compression.ZipFile>クラスを参照する必要がある、`System.IO.Compression.FileSystem`プロジェクト内のアセンブリ。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、既存の .zip ファイルの内容を反復処理し、.txt 拡張子を持つファイルを抽出する方法を示します。 使用して、<xref:System.IO.Compression.ZipArchive>既存の .zip ファイルにアクセスするクラスと<xref:System.IO.Compression.ZipArchiveEntry>圧縮ファイル内の個々 のエントリを検査するクラス。 拡張メソッドを使用して (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) の<xref:System.IO.Compression.ZipArchiveEntry>オブジェクト。 拡張メソッドがで使用できる、<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>クラスです。 使用する、<xref:System.IO.Compression.ZipFileExtensions>クラスを参照する必要がある、`System.IO.Compression.FileSystem`プロジェクト内のアセンブリ。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.IO.Compression.ZipArchive>クラスの既存の .zip ファイルにアクセスして、圧縮ファイルに新しいファイルに追加します。 既存の .zip ファイルに追加すると、新しいファイルが圧縮されます。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>例  
 使用することも、<xref:System.IO.Compression.GZipStream>と<xref:System.IO.Compression.DeflateStream>クラスして、データを圧縮します。 同じ圧縮アルゴリズムを使用します。 圧縮された<xref:System.IO.Compression.GZipStream>によって提供されるメソッドだけでなく多くの一般的なツールを使用して、拡張子を持つファイルに書き込まれるオブジェクトの圧縮を解除できる<xref:System.IO.Compression.GZipStream>です。 この例は、圧縮し、を使用してファイルのディレクトリを圧縮解除する方法を示します、<xref:System.IO.Compression.GZipStream>クラスです。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
