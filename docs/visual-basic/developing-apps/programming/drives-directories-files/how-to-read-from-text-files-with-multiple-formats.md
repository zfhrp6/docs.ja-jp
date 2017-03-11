---
title: "How to: Read From Text Files with Multiple Formats in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TextFieldParser object, reading from a file"
  - "TextFieldType enumeration"
  - "My.Computer.FileSystem.WriteAllText method, parsing structured text files"
  - "WriteAllText method, parsing structured text files"
  - "PeekChars method, determining format of text"
  - "reading text files, multiple formats"
  - "I/O [Visual Basic], reading text files"
  - "text files, reading"
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Read From Text Files with Multiple Formats in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを使用すると、ログなどの構造化されたテキスト ファイルを簡単かつ効率的に解析できます。  `PeekChars` メソッドを使用して、ファイルを解析するときに各行の書式を判断することにより、複数の書式を持つファイルを処理できます。  
  
### 複数の書式を持つテキスト ファイルを解析するには  
  
1.  testfile.txt という名前のテキスト ファイルをプロジェクトに追加します。  次の内容をそのテキスト ファイルに追加します。  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  目的の書式と、エラーが報告されるときに使用する書式を定義します。  各配列の最後のエントリが \-1 なので、最後のフィールドは可変幅と見なされます。  これは、配列の最後のエントリが 0 以下の場合に発生します。  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-text-fi_0_1.vb)]  
  
3.  幅と書式を指定して、新しい <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを作成します。  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-text-fi_0_2.vb)]  
  
4.  各行をループし、読み取り前に書式を調べます。  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-text-fi_0_3.vb)]  
  
5.  エラーをコンソールに書き込みます。  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-text-fi_0_4.vb)]  
  
## 使用例  
 `testfile.txt` ファイルから読み込まれた完全な例を次に示します。  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-text-fi_0_5.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   指定の書式を使用して行を解析できない \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外メッセージは、例外が発生した行を表し、<xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティには、行内のテキストが割り当てられる。  
  
-   指定のファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   部分信頼の状況で、ファイルにアクセスするための十分なアクセス許可がユーザーにない。  \(<xref:System.Security.SecurityException>\).  
  
-   パスが長すぎる \(<xref:System.IO.PathTooLongException>\)。  
  
-   ユーザーがファイルにアクセスするのに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 [How to: Read From Comma\-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [How to: Read From Fixed\-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)