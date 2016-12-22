---
title: "How to: Read From Comma-Delimited Text Files in Visual Basic | Microsoft Docs"
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
  - "files, parsing"
  - "text files, tasks"
  - "reading text files, comma-delimited"
  - "text files, reading"
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read From Comma-Delimited Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`TextFieldParser` オブジェクトを使用すると、ログなどの構造化されたテキスト ファイルを簡単かつ効率的に解析できます。  区切り記号が使用されたファイルと固定幅のテキスト フィールドを持つファイルのどちらであるかは、`TextFieldType` プロパティで定義します。  
  
### コンマ区切りのテキスト ファイルを解析するには  
  
1.  新しい `TextFieldParser` を作成します。  次のコードは、`MyReader` という名前の `TextFieldParser` を作成し、`test.txt` ファイルを開きます。  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  `TextField` の型と区切り記号を定義します。  次のコードは、`TextFieldType` プロパティを `Delimited` と定義し、区切り記号を "," と定義します。  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  ファイル内の各フィールドをループします。  破損している行がある場合は、エラーを報告し、解析を続けます。  次のコードは、ファイルをループし、各フィールドを順番に表示して、書式に誤りのあるフィールドを報告します。  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  `While` ブロックと `Using` ブロックを `End While` と `End Using` で閉じます。  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## 使用例  
 この例では、`test.txt` ファイルを読み取ります。  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   指定の書式を使用して行を解析できない \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外メッセージは、例外が発生した行を表し、<xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティには、行内のテキストが割り当てられる。  
  
-   指定のファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   部分信頼の状況で、ファイルにアクセスするための十分なアクセス許可がユーザーにない。  \(<xref:System.Security.SecurityException>\).  
  
-   パスが長すぎる \(<xref:System.IO.PathTooLongException>\)。  
  
-   ユーザーがファイルにアクセスするのに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [How to: Read From Fixed\-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [例外のトラブルシューティング : Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)