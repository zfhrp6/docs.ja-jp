---
title: "方法 : 文字列に文字を書き込む | Microsoft Docs"
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
  - "データ ストリーム、書き込み (文字列への文字の)"
  - "書き込み (文字列への文字の)"
  - "ストリーム、書き込み (文字列への文字の)"
  - "I/O [.NET Framework]、書き込み (文字列への文字の)"
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : 文字列に文字を書き込む
次のコード例は文字列に文字配列から文字を同期的にと非同期的に書き込みます。  
  
## 使用例  
 次の例では、配列から文字列に 5 文字を同期的に書き込みます。  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## 使用例  
 次の例 <xref:System.Windows.Controls.TextBox> のコントロールからのすべての文字を非同期的に読み取り、配列に格納します。  これは <xref:System.Windows.Controls.TextBlock> のコントロールに改行に続く行に、非同期的に各文字または空白文字を書き込みます。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.IO.StringWriter>   
 <xref:System.IO.StringWriter.Write%2A?displayProperty=fullName>   
 <xref:System.Text.StringBuilder>   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)   
 [非同期ファイル I\/O](../../../docs/standard/io/非同期ファイル-i-o.md)   
 [方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [方法 : ログ ファイルを開いて情報を追加する](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [方法 : ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [方法 : ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [方法 : 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)