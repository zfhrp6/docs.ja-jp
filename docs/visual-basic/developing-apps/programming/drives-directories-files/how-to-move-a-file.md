---
title: "方法: ファイルを移動する (Visual Basic) | Microsoft Docs"
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
  - "ファイル、移動"
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# 方法: ファイルを移動する (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem.MoveFile` メソッドは、ファイルを別のフォルダーに移動するために使用できます。 ターゲットの構造が存在しない場合は作成されます。  
  
### ファイルを移動するには  
  
-   `MoveFile` メソッドを使用し、ソース ファイルおよびターゲット ファイル両方のファイル名と場所を指定して、ファイルを移動します。 この例では、`test.txt` という名前のファイルを `TestDir1` から `TestDir2` に移動します。 ソース ファイル名と同じでも、ターゲット ファイル名を指定することにご注意ください。  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-move-a-file_1.vb)]  
  
### ファイルを移動し、その名前を変更するには  
  
-   `MoveFile` メソッドを使用してファイルを移動します。その際、ソース ファイルのファイル名と場所、ターゲットの場所、ターゲットの場所での新しい名前を指定します。 この例では、`test.txt` という名前のファイルを `TestDir1` から `TestDir2` に移動し、`nexttest.txt` という名前に変更します。  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-move-a-file_2.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである \(先頭が \\\\.\\\)、のいずれかの理由が考えられる \(<xref:System.ArgumentException>\)。  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)  
  
-   `destinationFileName` が `Nothing` または空の文字列である \(<xref:System.ArgumentNullException>\)。  
  
-   ソース ファイルが正しくないか、存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   パスを組み合わせると既存のディレクトリと同じになる、移動先のファイルが既に存在し `overwrite` が `False` に設定されている、移動先ディレクトリにある同じ名前のファイルが使用中である、またはユーザーがファイルにアクセスするのに必要なアクセス許可がない \(<xref:System.IO.IOException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   `showUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定されている状態で、ユーザーが操作をキャンセルしたか、または指定されていない I\/O エラーが発生した \(<xref:System.OperationCanceledException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ユーザーに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>   
 [How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [方法 : ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)