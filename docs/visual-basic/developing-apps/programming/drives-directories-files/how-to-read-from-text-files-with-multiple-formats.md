---
title: "方法: Visual Basic で複数の書式を持つテキスト ファイルを読み取る | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method, parsing structured text files
- PeekChars method, determining format of text
- reading text files, multiple formats
- I/O [Visual Basic], reading text files
- text files, reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6df284f7204b0731063db10cf026aed863f99fa9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>方法: Visual Basic で複数の書式を持つテキスト ファイルを読み取る
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトには、ログなどの構造化されたテキスト ファイルを簡単かつ効率的に解析する方法が備わっています。 `PeekChars` メソッドを使用して、ファイルを解析するときに各行の書式を判断すると、複数の書式を持つファイルを処理できます。  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>複数の書式を持つテキスト ファイルを解析するには  
  
1.  testfile.txt という名前のテキスト ファイルをプロジェクトに追加します。 次の内容をテキスト ファイルに追加します。  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  予期される形式と、エラーが報告されたときに使用される形式を定義します。 各配列の最後のエントリは -1 です。そのため、最後のフィールドは可変幅であると見なされます。 これは、配列の最後のエントリが 0 以下の場合に発生します。  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  幅と形式を定義して、新しい <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを作成します。  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  各行をループし、読み取り前に書式を調べます。  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  エラーをコンソールに書き込みます。  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a>例  
 この例では、`testfile.txt` ファイルを読み取ります。  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   指定した形式で行を解析することができない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。 例外の原因となった行が例外メッセージで報告され、<xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティには、その行に含まれているテキストが代入されます。  
  
-   指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。 (<xref:System.Security.SecurityException>)。  
  
-   パスが長すぎる (<xref:System.IO.PathTooLongException>)。  
  
-   ファイルにアクセスするために必要なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 [方法: コンマ区切りのテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [方法: 固定幅のテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [TextFieldParser オブジェクトによるテキスト ファイルの解析](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
