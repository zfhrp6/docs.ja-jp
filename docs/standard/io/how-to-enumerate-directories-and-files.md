---
title: '方法: ディレクトリとファイルを列挙する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd7b7542e5cf9352e965717368399dcf4a9ecd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-directories-and-files"></a>方法: ディレクトリとファイルを列挙する
名前の文字列の列挙可能なコレクションを返すメソッドを使用して、ディレクトリとファイルを列挙することができます。 <xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo>、または <xref:System.IO.FileSystemInfo> オブジェクトの列挙可能なコレクションを返すメソッドを使用することもできます。 列挙可能なコレクションでは、ディレクトリとファイルの大きなコレクションを操作する際に配列よりも優れたパフォーマンスが得られます。  
  
 これらのメソッドから取得される列挙可能なコレクションを使用して、<xref:System.Collections.Generic.List%601> クラスなどのコレクション クラスのコンストラクターに対して <xref:System.Collections.Generic.IEnumerable%601> パラメーターを指定することもできます。  
  
 ディレクトリまたはファイルの名前のみを取得する場合は、<xref:System.IO.Directory> クラスの列挙メソッドを使用します。 ディレクトリまたはファイルの他のプロパティを取得する場合は、<xref:System.IO.DirectoryInfo> および <xref:System.IO.FileSystemInfo> クラスを使用します。  
  
 次の表では、列挙コレクションを返すメソッドのガイドを提供します。  
  
|列挙対象|返される列挙可能なコレクション|使用するメソッド|  
|------------------|-------------------------------------|-------------------|  
|ディレクトリ|ディレクトリ名|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||ディレクトリ情報 (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|ファイル|ファイル名|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||ファイル情報 (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|ファイル システム情報|ファイル システム エントリ|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||ファイル システム情報 (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <xref:System.IO.SearchOption> 列挙で提供される <xref:System.IO.SearchOption.AllDirectories> 検索オプションを使用して、親ディレクトリのサブディレクトリ内のすべてのファイルをすぐに列挙することはできますが、未承認アクセスの例外 (<xref:System.UnauthorizedAccessException>) によって、列挙が不完全になる可能性があります。 このような例外が考えられる場合は、その例外をキャッチして作業を続行します。その場合、最初にディレクトリを列挙してからファイルを列挙します。  
  
### <a name="to-enumerate-directory-names"></a>ディレクトリ名を列挙するには  
  
-   <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> メソッドを使用して、指定されたパスの最上位レベルのディレクトリ名のリストを取得します。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>ディレクトリとサブディレクトリ内のファイル名を列挙するには  
  
-   <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> メソッドを使用して、ディレクトリと (必要に応じて) そのサブディレクトリを検索し、指定された検索パターンに一致するファイル名のリストを取得します。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>DirectoryInfo オブジェクトのコレクションを列挙するには  
  
-   <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> メソッドを使用して、最上位レベルのディレクトリのコレクションを取得します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>すべてのディレクトリ内の FileInfo オブジェクトのコレクションを列挙するには  
  
-   <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> メソッドを使用して、すべてのディレクトリ内の指定された検索パターンに一致するファイルのコレクションを取得します。 この例では、まず、最上位レベルのディレクトリを列挙して考えられる未承認アクセス例外をキャッチしてから、ファイルを列挙します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>参照  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)
