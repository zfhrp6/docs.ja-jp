---
title: "How to: Read From Binary Files in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "binary files, reading from"
  - "I/O [Visual Basic], reading from binary files"
  - "ReadAllBytes method, reading from binary files"
  - "My.Computer.FileSystem object, reading from binary files"
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read From Binary Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトには、バイナリ ファイルを読み取るための `ReadAllBytes` メソッドが用意されています。  
  
### バイナリ ファイルを読み取るには  
  
-   `ReadAllBytes` メソッドを使用します。このメソッドは、ファイルの内容をバイト配列として返します。  この例では、`C:/Documents and Settings/selfportrait.jpg` ファイルを読み取ります。  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   サイズの大きいバイナリ ファイルの場合は、<xref:System.IO.FileStream> オブジェクトの <xref:System.IO.FileStream.Read%2A> メソッドを使用して、一度に指定の量だけをファイルから読み取ることができます。  その後、各読み取り操作でファイルからメモリに読み込まれる量を制限することができます。  次のコード例では、ファイルをコピーし、各読み取り操作でファイルからメモリに読み込まれる量を呼び出し元が指定できるようにします。  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   パスが無効である場合。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである、のいずれかの理由が考えられる \(<xref:System.ArgumentException>\)  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   ファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)  
  
-   他のプロセスがファイルを使用しているか、または I\/O エラーが発生した \(<xref:System.IO.IOException>\)  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   文字列をバッファーに書き込むための十分なメモリがない \(<xref:System.OutOfMemoryException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
 ファイル名からファイルの内容を判断しないでください。  たとえば、Form1.vb というファイルが Visual Basic のソース ファイルではない可能性もあります。  
  
 アプリケーションでデータを使用する前に、入力をすべて検証してください。  ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)