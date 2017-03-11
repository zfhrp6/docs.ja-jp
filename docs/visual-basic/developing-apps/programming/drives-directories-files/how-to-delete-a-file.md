---
title: "How to: Delete a File in Visual Basic | Microsoft Docs"
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
  - "Delete method"
  - "files, deleting"
  - "files, manipulating"
  - "File object"
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# How to: Delete a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトの `DeleteFile` メソッドを使用すると、ファイルを削除できます。  削除したファイルを**ごみ箱**に送るかどうか、ファイルを削除することをユーザーに確認するかどうか、ユーザーが操作をキャンセルした場合の処理方法などがオプションとして用意されています。  
  
### テキスト ファイルを削除するには  
  
-   `DeleteFile` メソッドを使用してファイルを削除します。  次のコードは、`test.txt` という名前のファイルを削除する方法の例です。  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_1.vb)]  
  
### ユーザーに確認したうえでテキスト ファイルを削除するには  
  
-   `DeleteFile` メソッドを使用してファイルを削除します。その際、`showUI` を `AllDialogs` に設定します。  次のコードは、`test.txt` という名前のファイルを、ユーザーに確認したうえで削除する方法の例です。  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_2.vb)]  
  
### テキスト ファイルを削除してごみ箱に送るには  
  
-   `DeleteFile` メソッドを使用してファイルを削除します。その際、`recycle` パラメーターに `SendToRecycleBin` を指定します。  次のコードは、`test.txt` という名前のファイルを削除して**ごみ箱**に送る方法の例です。  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_3.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはフォルダー名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ファイルが使用中である \(<xref:System.IO.IOException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ファイルが存在しない \(<xref:System.IO.FileNotFoundException>\)  
  
-   ファイルの削除に必要なアクセス許可がユーザーにないか、またはファイルが読み取り専用である \(<xref:System.UnauthorizedAccessException>\)  
  
-   部分信頼の状況でユーザーに十分なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ユーザーが操作をキャンセルし、`onUserCancel` が `ThrowException` に設定されている \(<xref:System.OperationCanceledException>\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)