---
title: "How to: Read From Fixed-width Text Files in Visual Basic | Microsoft Docs"
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
  - "fixed-width text file"
  - "reading text files, fixed-width"
  - "files, parsing"
  - "text files, tasks"
  - "text files, reading"
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read From Fixed-width Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`TextFieldParser` オブジェクトを使用すると、ログなどの構造化されたテキスト ファイルを簡単かつ効率的に解析できます。  
  
 `TextFieldType` プロパティでは、解析対象のファイルが区切り記号入りファイルと固定幅のテキスト フィールドを持つファイルのどちらであるかを定義します。  固定幅のテキスト ファイルでは、最後のフィールドを可変幅にすることができます。  最後のフィールドが可変幅であることを指定するには、そのフィールドの幅を 0 以下として定義します。  
  
### 固定幅のテキスト ファイルを解析するには  
  
1.  新しい `TextFieldParser` を作成します。  次のコードは、`Reader` という名前の `TextFieldParser` を作成し、`test.log` ファイルを開きます。  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  `TextFieldType` プロパティを `FixedWidth` として定義し、幅と形式を定義します。  次のコードは、テキストの列を定義します。最初は幅が 5 文字、その次は 10、その次は 11、その次は可変幅です。  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  ファイル内の各フィールドをループします。  破損している行がある場合は、エラーを報告し、解析を続けます。  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  `While` ブロックと `Using` ブロックを `End While` と `End Using` で閉じます。  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## 使用例  
 この例では、`test.log` ファイルを読み取ります。  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   指定の書式を使用して行を解析できない \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外メッセージは、例外が発生した行を表し、<xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティには、行内のテキストが割り当てられる。  
  
-   指定のファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   部分信頼の状況で、ファイルにアクセスするための十分なアクセス許可がユーザーにない。  \(<xref:System.Security.SecurityException>\).  
  
-   パスが長すぎる \(<xref:System.IO.PathTooLongException>\)。  
  
-   ユーザーがファイルにアクセスするのに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [How to: Read From Comma\-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [例外のトラブルシューティング : Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)