---
title: "方法 : ログ ファイルを開いて情報を追加する | Microsoft Docs"
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
  - "ログ ファイル、開く"
  - "ストリーム、オープンと追加 (ログ ファイルの)"
  - "ログ ファイル、追加"
  - "I/O [.NET Framework]、ログ ファイル"
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : ログ ファイルを開いて情報を追加する
<xref:System.IO.StreamWriter> と <xref:System.IO.StreamReader> は、文字をストリームに書き込んだり、文字をストリームから読み取ったりします。  入力用として `log.txt` ファイルを開くか、ファイルが存在しない場合は作成し、ファイルの末尾に情報を追加するコードの例を次に示します。  その後で、ファイルの内容を表示するために標準出力に書き込みます。  この例に代わる方法として、情報を 1 つの文字列または文字列配列として格納できます。また、<xref:System.IO.File.WriteAllText%2A> または <xref:System.IO.File.WriteAllLines%2A> メソッドを使用して同じ機能を実行することもできます。  
  
> [!NOTE]
>  Visual Basic では、ログ ファイルの作成、またはログ ファイルへの書き込みを行う場合に、<xref:Microsoft.VisualBasic.Logging.Log> クラスまたは <xref:Microsoft.VisualBasic.FileIO.FileSystem> クラスに用意されているメソッドとプロパティを使用することもできます。  
  
## 使用例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.IO.StreamWriter>   
 <xref:System.IO.StreamReader>   
 <xref:System.IO.File.AppendText%2A?displayProperty=fullName>   
 <xref:System.IO.File.OpenText%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 [方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [方法 : ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [方法 : ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [方法 : 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [方法 : 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)