---
title: "How to: Read From Text Files in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "extended characters, reading"
  - "reading text files"
  - "reading data, text files"
  - "examples [Visual Basic], reading text files"
  - "text files, reading"
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read From Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトの <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> メソッドを使用すると、テキスト ファイルを読み取ることができます。  ファイルの内容が ASCII や UTF\-8 などのエンコーディングを使用している場合、ファイル エンコーディングを指定できます。  
  
 読み取るファイルで拡張文字が使用されている場合、ファイル エンコーディングを指定する必要があります。  
  
> [!NOTE]
>  ファイルから 1 回に 1 行のテキストを読み取るには、`My.Computer.FileSystem` オブジェクトの <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> メソッドを使用します。  `OpenTextFileReader` メソッドは <xref:System.IO.StreamReader> オブジェクトを返します。  `StreamReader` オブジェクトの <xref:System.IO.StreamReader.ReadLine%2A> メソッドを使用して、ファイルから 1 回に 1 行を読み取ることができます。  `StreamReader` オブジェクトの <xref:System.IO.StreamReader.EndOfStream%2A> メソッドを使用して、ファイルの最後かどうかをテストできます。  
  
### テキスト ファイルを読み取るには  
  
-   `My.Computer.FileSystem` オブジェクトの `ReadAllText` メソッドを使用して、ファイルのパスを指定し、テキスト ファイルの内容を文字列に読み取ります。  次の例は、test.txt の内容を文字列に読み取り、メッセージ ボックスに表示します。  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### エンコードされているテキスト ファイルを読み取るには  
  
-   `My.Computer.FileSystem` オブジェクトの `ReadAllText` メソッドを使用して、ファイルのパスとファイル エンコードの種類を指定し、テキスト ファイルの内容を文字列に読み取ります。  次の例は、UTF32 ファイルである test.txt の内容を文字列に読み取り、メッセージ ボックスに表示します。  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効である場合。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである、のいずれかの理由が考えられる \(<xref:System.ArgumentException>\)。  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)  
  
-   ファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   他のプロセスがファイルを使用しているか、または I\/O エラーが発生した \(<xref:System.IO.IOException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   文字列をバッファーに書き込むための十分なメモリがない \(<xref:System.OutOfMemoryException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
 ファイル名からファイルの内容を判断しないでください。  たとえば、Form1.vb というファイルは [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のソース ファイルではない可能性もあります。  
  
 アプリケーションでデータを使用する前に、入力をすべて検証してください。  ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [How to: Read From Comma\-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [How to: Read From Fixed\-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)