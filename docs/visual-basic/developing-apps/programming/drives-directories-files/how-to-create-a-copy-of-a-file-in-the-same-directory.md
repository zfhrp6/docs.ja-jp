---
title: "方法 : Visual Basic でファイルのコピーを同じディレクトリに作成する | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
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
ms.openlocfilehash: c7078edf6822cc06c7d3c7933c5df7fdd2a73e6f
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>方法 : Visual Basic でファイルのコピーを同じディレクトリに作成する
ファイルをコピーするには、`My.Computer.FileSystem.CopyFile` メソッドを使用します。 このパラメーターでは、既存のファイルの上書き、ファイルの名前変更、操作の進行状況の表示、ユーザーによる操作のキャンセルが可能になります。  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>ファイルのコピーを同じフォルダーに作成するには  
  
-   ターゲット ファイルと場所を指定し、`CopyFile` メソッドを使用します。 次の例では、`test2.txt` という `test.txt` のコピーを作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>同じフォルダーにファイルのコピーを、既存のファイルを上書きして作成するには  
  
-   ターゲット ファイルと場所を指定し、`overwrite` を `True` に設定して、`CopyFile` メソッドを使用します。 次の例では、`test2.txt` という `test.txt` のコピーを、既存のファイルをその名前で上書きして作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外がスローされる可能性があります。  
  
-   次のいずれかの理由で、パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   システムが絶対パスを取得できなかった (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   ソース ファイルが正しくない、または存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   結合したパスが、既存のディレクトリを指している (<xref:System.IO.IOException>)。  
  
-   リンク先ファイルが存在し、`overwrite` が `False` に設定されている (<xref:System.IO.IOException>)。  
  
-   ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.IO.IOException>)。  
  
-   同じ名前がターゲット フォルダー内のファイルで使用されている (<xref:System.IO.IOException>)。  
  
-   パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException`に設定され、ユーザーが操作をキャンセルしている (<xref:System.OperationCanceledException>)。  
  
-   `ShowUI` が `True` に設定され、`onUserCancel` が `ThrowException` に設定され、未指定の I/O エラーが発生する (<xref:System.OperationCanceledException>)。  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [方法: 特定のパターンを持つファイルをディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [方法: ファイルのコピーを別のディレクトリに作成する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [方法: ディレクトリを別のディレクトリにコピーする](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [方法: ファイルの名前を変更する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
