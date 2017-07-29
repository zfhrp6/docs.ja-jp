---
title: "方法: Visual Basic でコンマ区切りのテキスト ファイルを読み取る"
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
- files, parsing
- text files, tasks
- reading text files, comma-delimited
- text files, reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2ae6a3f315a8e433386319d1aa1a7f48726a19bb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>方法: Visual Basic でコンマ区切りのテキスト ファイルを読み取る
`TextFieldParser` オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。 区切り形式のファイルか、固定幅フィールドのテキストを使用したファイルかは、`TextFieldType` プロパティで定義します。  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>コンマ区切りテキスト ファイルを解析するには  
  
1.  新規の `TextFieldParser` を作成します。 次のコードは、`MyReader` という名前の `TextFieldParser` を作成し、`test.txt` ファイルを開きます。  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  `TextField` 型と区切り記号を定義します。 次のコードは、`TextFieldType` プロパティを `Delimited`、区切り記号を "," として定義します。  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  ファイル内のフィールドをループします。 破損している行が見つかった場合は、エラーを報告して解析を続行します。 次のコードは、ファイル内をループし、各フィールド順次表示して、不正にフォーマットされているフィールドをレポートします。  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  `While` ブロックと `Using` ブロックをそれぞれ `End While` と `End Using` で閉じます。  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a>例  
 次のコードは、`test.txt` ファイルから読み取りを行う例です。  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。 例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。  
  
-   指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。 (<xref:System.Security.SecurityException>).  
  
-   パスが長すぎる (<xref:System.IO.PathTooLongException>)。  
  
-   ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [方法: 固定幅のテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [方法: 複数の書式を持つテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [TextFieldParser オブジェクトによるテキスト ファイルの解析](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [チュートリアル: Visual Basic によるファイルとディレクトリの操作](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)

