---
title: "How to: Create a Copy of a File in the Same Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "File.Copy"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]"
  - "files, copying"
  - "CopyFile method, copying files in Visual Basic"
  - "I/O [Visual Basic], copying files"
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Create a Copy of a File in the Same Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem.CopyFile` メソッドを使用すると、ファイルをコピーできます。  そのパラメーターを使用して、既存のファイルを上書きしたり、ファイルの名前を変更したり、操作の進行状況を表示したり、ユーザーが操作をキャンセルできるようにしたりできます。  
  
### ファイルのコピーを同じフォルダーに作成するには  
  
-   `CopyFile` メソッドを使用します。その際、対象のファイルと場所を指定します。  次の例では、`test.txt` のコピーを `test2.txt` という名前で作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-create-a-copy-of-_0_1.vb)]  
  
### ファイルのコピーを同じフォルダーに作成し、既存のファイルを上書きするには  
  
-   `CopyFile` メソッドを使用します。その際、対象のファイルと場所を指定し、`overwrite` を `True` に設定します。  次の例では、`test.txt` のコピーを `test2.txt` という名前で作成し、同じ名前のファイルが既に存在する場合は上書きします。  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-create-a-copy-of-_0_2.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   システムが絶対パスを取得できなかった \(<xref:System.ArgumentException>\)。  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   ソース ファイルが有効でないか、または存在しない \(<xref:System.IO.FileNotFoundException>\)。  
  
-   パスを組み合わせると既存のディレクトリと同じになる \(<xref:System.IO.IOException>\)。  
  
-   移動先にファイルが既に存在し、`overwrite` が `False` に設定されている \(<xref:System.IO.IOException>\)。  
  
-   ユーザーがファイルにアクセスするのに必要なアクセス許可がない \(<xref:System.IO.IOException>\)。  
  
-   移動先フォルダーの同名のファイルが使用中である \(<xref:System.IO.IOException>\).  
  
-   パス内のファイル名またはフォルダー名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   `ShowUI` が `True` に、`onUserCancel` が `ThrowException` に、それぞれ設定されている状況で、ユーザーが操作をキャンセルした \(<xref:System.OperationCanceledException>\)。  
  
-   `ShowUI` が `True` に、`onUserCancel` が `ThrowException` に、それぞれ設定されている状況で、未指定の I\/O エラーが発生した \(<xref:System.OperationCanceledException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   ユーザーに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [方法 : 特定のパターンを持つファイルをディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)