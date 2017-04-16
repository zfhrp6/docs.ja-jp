---
title: "方法 : ファイルからテキストを読み取る | Microsoft Docs"
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
  - "データ ストリーム, 読み取り (ファイルからテキストを)"
  - "I/O [.NET Framework], 読み取り (ファイルからテキストを)"
  - "読み取り (データを), テキスト ファイル"
  - "読み取り (テキスト ファイルを)"
  - "ストリーム, 読み取り (ファイルからテキストを)"
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
caps.latest.revision: 23
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# 方法 : ファイルからテキストを読み取る
次に、.NET デスクトップ アプリを使用してテキスト ファイルから同期でテキストを読み取る方法と非同期でテキストを読み取る方法の例を示します。  どちらの例でも、<xref:System.IO.StreamReader> クラスのインスタンスを作成する場合に、ファイルの相対パスまたは絶対パスを指定します。  次の例では、TestFile.txt という名前のファイルがアプリケーションと同じフォルダーにあることを前提とします。  
  
 Windows ランタイムではファイルに対する読み取りと書き込みに別のストリーム型が用意されているため、これらのコード例は Windows ストア アプリの開発には適用されません。  Windows ストア アプリのコンテキスト内のファイルからテキストを読み取る方法を示す例については、「[クイック スタート: ファイルの読み取りと書き込み](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)」を参照してください。  .NET Framework ストリームと Windows ランタイム ストリームを変換する方法を示す例は、「[方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)」を参照してください。  
  
## 使用例  
 最初の例では、コンソール アプリケーション内での同期読み取り操作を示します。  この例では、ストリーム リーダーを使用してテキスト ファイルを開き、内容を文字列にコピーして、文字列をコンソールに出力します。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## 使用例  
 2 番目の例では、Windows Presentation Foundation \(WPF\) アプリケーション内での非同期読み取り操作を示します。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## 参照  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.File.OpenText%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 [非同期ファイル I\/O](../../../docs/standard/io/非同期ファイル-i-o.md)   
 [NIB: How to: Create a Directory Listing](http://msdn.microsoft.com/ja-jp/4d2772b1-b991-4532-a8a6-6ef733277e69)   
 [クイック スタート: ファイルの読み取りと書き込み](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)   
 [方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [方法 : ログ ファイルを開いて情報を追加する](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [方法 : ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [方法 : 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [方法 : 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)