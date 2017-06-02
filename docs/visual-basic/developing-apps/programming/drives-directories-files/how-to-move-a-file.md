---
title: "方法: ファイルを移動する (Visual Basic) | Microsoft Docs"
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
- files, moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 44e0e81a28d1475a3f3cf6bcb7372b05eb8037bf
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-move-a-file-in-visual-basic"></a>方法: ファイルを移動する (Visual Basic)
`My.Computer.FileSystem.MoveFile` メソッドは、ファイルを別のフォルダーに移動するために使用できます。 ターゲットの構造が存在しない場合は作成されます。  
  
### <a name="to-move-a-file"></a>ファイルを移動するには  
  
-   `MoveFile` メソッドを使用し、ソース ファイルおよびターゲット ファイル両方のファイル名と場所を指定して、ファイルを移動します。 この例では、 `test.txt` という名前のファイルを `TestDir1` から `TestDir2`に移動します。 ソース ファイル名と同じでも、ターゲット ファイル名を指定することにご注意ください。  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>ファイルを移動し、その名前を変更するには  
  
-   `MoveFile` メソッドを使用してファイルを移動します。その際、ソース ファイルのファイル名と場所、ターゲットの場所、ターゲットの場所での新しい名前を指定します。 この例では、 `test.txt` という名前のファイルを `TestDir1` から `TestDir2` に移動し、 `nexttest.txt`という名前に変更します。  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   `destinationFileName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。  
  
-   ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   パスを組み合わせると既存のディレクトリと同じになる、リンク先ファイルが存在し `overwrite` が `False` に設定されている、移動先ディレクトリにある同じ名前のファイルが使用中である、またはユーザーがファイルにアクセスするのに必要なアクセス許可がない (<xref:System.IO.IOException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)  
  
-   `showUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定されている状態で、ユーザーが操作をキャンセルしたか、または指定されていない I/O エラーが発生した (<xref:System.OperationCanceledException>)。  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
-   ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>   
 [方法: ファイルの名前を変更する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [方法: ファイルのコピーを別のディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [方法: ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
