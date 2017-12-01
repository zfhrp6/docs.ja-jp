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
# <a name="how-to-enumerate-directories-and-files"></a>方法: ディレクトリとファイルを列挙する
ディレクトリとファイル名の文字列の列挙可能なコレクションを返すメソッドを使用して列挙できます。 列挙可能なコレクションを返すメソッドを使用することもできます。 <xref:System.IO.DirectoryInfo>、 <xref:System.IO.FileInfo>、または<xref:System.IO.FileSystemInfo>オブジェクト。 列挙可能なコレクションは、ディレクトリおよびファイルの大規模なコレクションを操作する場合、配列よりも優れたパフォーマンスを提供します。  
  
 指定するこれらのメソッドから取得した列挙可能なコレクションを使用することができます、<xref:System.Collections.Generic.IEnumerable%601>などのコレクションのコンス トラクターのパラメーターのクラス、<xref:System.Collections.Generic.List%601>クラスです。  
  
 ディレクトリまたはファイルの名前のみを取得する場合は、列挙メソッドを使用して、<xref:System.IO.Directory>クラスです。 ディレクトリまたはファイルの他のプロパティを取得する場合は、使用、<xref:System.IO.DirectoryInfo>と<xref:System.IO.FileSystemInfo>クラスです。  
  
 次の表は、列挙可能なコレクションを返す方法のガイドを提供します。  
  
|列挙するには|列挙可能なコレクションを返す|使用する方法|  
|------------------|-------------------------------------|-------------------|  
|ディレクトリ|ディレクトリ名|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||ディレクトリ情報 (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|ファイル|ファイル名|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||ファイルの情報 (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|ファイル システム情報|ファイル システム エントリ|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||ファイル システム情報 (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 使用してすぐに親ディレクトリのサブディレクトリにあるすべてのファイルを列挙できますが、<xref:System.IO.SearchOption.AllDirectories>によって提供されるオプションの検索、<xref:System.IO.SearchOption>列挙型、不正アクセス例外 (<xref:System.UnauthorizedAccessException>)、列挙型があります。完了していません。 これらの例外が可能な場合は、例外をキャッチし、最初にディレクトリを列挙して、ファイルを列挙して続行できます。  
  
### <a name="to-enumerate-directory-names"></a>ディレクトリ名を列挙するには  
  
-   使用して、<xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>メソッドを指定されたパス内の最上位レベルのディレクトリ名の一覧を取得します。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>ディレクトリとサブディレクトリ内のファイル名を列挙するには  
  
-   使用して、<xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType>ディレクトリと (必要に応じて) そのサブディレクトリを検索して、指定した検索パターンに一致するファイル名の一覧を取得する方法です。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>DirectoryInfo オブジェクトのコレクションを列挙するには  
  
-   使用して、<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>最上位のディレクトリのコレクションを取得します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>すべてのディレクトリに FileInfo オブジェクトのコレクションを列挙するには  
  
-   使用して、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>すべてのディレクトリ内の指定した検索パターンに一致するファイルのコレクションを取得します。 この例では、まず考えられる不正アクセス例外をキャッチする最上位のディレクトリを列挙し、ファイルを列挙します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
