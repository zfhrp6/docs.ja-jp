---
title: "方法 : Visual Basic でファイルの名前を変更する | Microsoft Docs"
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
- I/O [Visual Basic], renaming files
- files, renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a0a31353ce3ee0c48907f9550f6961260f92b64a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-rename-a-file-in-visual-basic"></a>方法 : Visual Basic でファイルの名前を変更する
`My.Computer.FileSystem` オブジェクトの `RenameFile` メソッドは、現在の場所、ファイル名、および新しいファイル名を指定して、ファイルの名前を変更するために使用します。 このメソッドは、ファイルを移動を使用する目的には使用できません。ファイルを移動して名前を変更するには、`MoveFile` メソッドを使用してください。  
  
### <a name="to-rename-a-file"></a>ファイル名を変更するには  
  
-   `My.Computer.FileSystem.RenameFile` メソッドを使用して、ファイルの名前を変更します。 この例では、 `Test.txt` というファイル名を `SecondTest.txt` に変更しています。  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 このコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでは、スニペットは [**ファイル システム - ドライブ、フォルダー、およびファイルの処理**] にあります。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効である。これには、1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられます (<xref:System.ArgumentException>)。  
  
-   `newName` にパス情報が含まれている (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)。  
  
-   `newName` が `Nothing` または空の文字列である (<xref:System.ArgumentNullException>)。  
  
-   ソース ファイルが有効でないか、存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   `newName` で指定された名前のファイルまたはディレクトリが既に存在する (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義された最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   パスの表示に必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。  
  
-   ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>   
 [方法: ファイルを移動する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)   
 [ファイルおよびディレクトリの作成、削除、および移動](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)   
 [方法: ファイルのコピーを同じディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [方法: ファイルのコピーを別のディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
