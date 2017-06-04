---
title: "方法 : 文字列から文字を読み取る | Microsoft Docs"
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
  - "読み取り (文字列から文字を)"
  - "データ ストリーム、読み取り (文字列から文字を)"
  - "I/O [.NET Framework]、読み取り (文字列から文字を)"
  - "読み取り (データを)、文字列"
  - "ストリーム、読み取り (文字列から文字を)"
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 文字列から文字を読み取る
次のコード例は文字列からの文字の同期的にと非同期的に読み込む方法を説明します。  
  
## 使用例  
 この例では、文字列から 13 文字を同期的に読み取り、配列に格納し、その文字を表示します。  次に、文字列内の残りの文字を読み取り、6 番目の要素で開始される配列に格納し、その配列の内容を表示します。  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## 使用例  
 次の例 <xref:System.Windows.Controls.TextBox> のコントロールからのすべての文字を非同期的に読み取り、配列に格納します。  これは <xref:System.Windows.Controls.TextBlock> のコントロールに改行に続く行に、非同期的に各文字または空白文字を書き込みます。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## 参照  
 <xref:System.IO.StringReader>   
 <xref:System.IO.StringReader.Read%2A?displayProperty=fullName>   
 [非同期ファイル I\/O](../../../docs/standard/io/非同期ファイル-i-o.md)   
 [NIB: How to: Create a Directory Listing](http://msdn.microsoft.com/ja-jp/4d2772b1-b991-4532-a8a6-6ef733277e69)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [方法 : ログ ファイルを開いて情報を追加する](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [方法 : ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [方法 : ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [方法 : 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)