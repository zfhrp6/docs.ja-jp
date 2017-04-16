---
title: "方法: ディレクトリとファイルを列挙する | Microsoft Docs"
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
  - "I/O [.NET Framework]、列挙 (ディレクトリとファイルを)"
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 18
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法: ディレクトリとファイルを列挙する
名前の一連の列挙可能なコレクションを返すメソッドを使用して、ディレクトリとファイルを列挙できます。  また、<xref:System.IO.DirectoryInfo>、<xref:System.IO.FileInfo>、または <xref:System.IO.FileSystemInfo> の各オブジェクトの列挙可能なコレクションを返すメソッドも使用できます。  列挙可能なコレクションには、ディレクトリや大量のファイルを使用すると、配列よりもパフォーマンスが優れています。  
  
 これらのメソッドから取得した列挙可能なコレクションを使用して、<xref:System.Collections.Generic.List%601> クラスなどのコレクション クラスのコンストラクターの <xref:System.Collections.Generic.IEnumerable%601> パラメーターを指定することもできます。  
  
 ディレクトリまたはファイルの名前のみを取得するには、<xref:System.IO.Directory> クラスの列挙メソッドを使用します。  ディレクトリまたはファイルのその他のプロパティを取得するには、<xref:System.IO.DirectoryInfo> クラスおよび <xref:System.IO.FileSystemInfo> クラスを使用します。  
  
 列挙可能なコレクションを返すメソッドの説明を次の表に示します。  
  
|列挙する対象|返される列挙可能なコレクション|使用するメソッド|  
|------------|---------------------|--------------|  
|ディレクトリ|ディレクトリ名|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=fullName>|  
||ディレクトリ情報 \(<xref:System.IO.DirectoryInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName>|  
|ファイル|ファイル名|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=fullName>|  
||ファイル情報 \(<xref:System.IO.FileInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName>|  
|ファイル システム情報|ファイル システム エントリ|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=fullName>|  
||ファイル システム情報 \(<xref:System.IO.FileSystemInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=fullName>|  
  
 <xref:System.IO.SearchOption> の列挙体に用意されている <xref:System.IO.SearchOption> の検索オプションを使用して、親ディレクトリのサブディレクトリ内のすべてのファイルを列挙できますが、承認されていないアクセスの例外 \(<xref:System.UnauthorizedAccessException>\) は列挙体が不完全になる可能性があります。  このような例外が発生する可能性がある場合は、まずディレクトリを列挙してからファイルを列挙することで、例外をキャッチして続行できます。  
  
### ディレクトリ名を列挙するには  
  
-   <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=fullName> メソッドを使用して、指定したパスに存在する最上位ディレクトリ名のリストを取得します。  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### ディレクトリとそのサブディレクトリ内のファイル名を列挙するには  
  
-   ディレクトリと \(必要に応じて\) サブディレクトリを検索し、指定された検索パターンと一致するファイル名の一覧を取得するに <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=fullName> のメソッドを使用します。  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### DirectoryInfo オブジェクトのコレクションを列挙するには  
  
-   <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName> メソッドを使用して、最上位ディレクトリのコレクションを取得します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### すべてのディレクトリ内の FileInfo オブジェクトのコレクションを列挙するには  
  
-   <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName> メソッドを使用して、すべてのディレクトリ内の指定した検索パターンに一致するファイルのコレクションを取得します。  この例では、まず最上位ディレクトリを列挙して発生の可能性がある承認されていないアクセスの例外をキャッチし、次にファイルを列挙します。  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## 参照  
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)