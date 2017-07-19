---
title: "方法 : ファイルを圧縮して抽出する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "I/O [.NET Framework]、圧縮"
  - "圧縮"
  - "圧縮 (ファイルを)"
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : ファイルを圧縮して抽出する
<xref:System.IO.Compression> の名前空間は、ファイル、およびストリームを圧縮および圧縮解除するための型が含まれています。  、圧縮ファイルの内容を読み取って変更するには、これらの型を使用する:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 次の例では、圧縮ファイルとする関数の中に作業するときに実行されます。  
  
## 使用例  
 この例で <xref:System.IO.Compression.ZipFile> クラスを使用して .zip ファイル名拡張子を持つ圧縮ファイルを作成および取得する方法を示します。  次に新しいフォルダーが完成した新しい抽出 .zip ファイルに含まれ、フォルダーの内容を圧縮します。  <xref:System.IO.Compression.ZipFile> クラスを使用するには、プロジェクトで `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## 使用例  
 次の例は、既存の .zip ファイルの内容を反復処理し .txt の拡張子を持つファイルを取得する方法を示します。  これは <xref:System.IO.Compression.ZipArchive> クラスおよび圧縮ファイルのエントリをチェックする既存の .zip ファイルにアクセスするために <xref:System.IO.Compression.ZipArchiveEntry> クラスを使用します。  これは <xref:System.IO.Compression.ZipArchiveEntry> オブジェクトに拡張メソッド \(<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>\) を使用します。  拡張メソッドは <xref:System.IO.Compression.ZipFileExtensions?displayProperty=fullName> クラスで使用できます。  <xref:System.IO.Compression.ZipFileExtensions> クラスを使用するには、プロジェクトで `System.IO.Compression.FileSystem` アセンブリを参照する必要があります。  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## 使用例  
 次の例は、既存の .zip ファイルにアクセスするために <xref:System.IO.Compression.ZipArchive> クラスを使用して、圧縮ファイルに新しいファイルを追加します。  新しいファイルは既存の .zip ファイルに追加するときに圧縮される取得します。  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## 使用例  
 データを圧縮および圧縮解除するために <xref:System.IO.Compression.GZipStream> と <xref:System.IO.Compression.DeflateStream> クラスを使用できます。  これらは同じ圧縮アルゴリズムを使用します。  .gz の拡張子を持つファイルに書き込まれた <xref:System.IO.Compression.GZipStream> の圧縮オブジェクトは <xref:System.IO.Compression.GZipStream>によって提供されるメソッドに加え、の標準ツールを使用して圧縮解除することができます。  次の例では、<xref:System.IO.Compression.GZipStream> クラスを使用して、ファイルのディレクトリを圧縮および圧縮解除する方法を示します。  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## 参照  
 <xref:System.IO.Compression.ZipArchive>   
 <xref:System.IO.Compression.ZipFile>   
 <xref:System.IO.Compression.ZipArchiveEntry>   
 <xref:System.IO.Compression.DeflateStream>   
 <xref:System.IO.Compression.GZipStream>   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)