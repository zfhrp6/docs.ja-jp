---
title: "How to: Rename a File in Visual Basic | Microsoft Docs"
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
  - "I/O [Visual Basic], renaming files"
  - "files, renaming"
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Rename a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトの `RenameFile` メソッドを使用すると、ファイルの現在の位置、現在のファイル名、および新しいファイル名を指定して、ファイルの名前を変更できます。  このメソッドでは、ファイルを移動することはできません。ファイルを移動して名前を変更するには、`MoveFile` メソッドを使用します。  
  
### ファイルの名前を変更するには  
  
-   `My.Computer.FileSystem.RenameFile` メソッドを使用してファイルの名前を変更します。  この例では、`Test.txt` というファイル名を `SecondTest.txt` に変更します。  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-rename-a-file_1.vb)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、このスニペットは **\[ファイル システム \- ドライブ、フォルダー、およびファイルの処理\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   `newName` にパス情報が含まれている \(<xref:System.ArgumentException>\)。  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   `newName` が `Nothing` または空の文字列である \(<xref:System.ArgumentNullException>\)。  
  
-   ソース ファイルが有効でないか、または存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   `newName` で指定したのと同じ名前のファイルまたはディレクトリが既に存在する \(<xref:System.IO.IOException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ユーザーに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>   
 [方法: ファイルを移動する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)   
 [Creating, Deleting, and Moving Files and Directories](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)   
 [How to: Create a Copy of a File in the Same Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)