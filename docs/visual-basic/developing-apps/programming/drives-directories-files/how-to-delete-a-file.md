---
title: "方法: Visual Basic でファイルを削除する | Microsoft Docs"
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.openlocfilehash: f6cf3192d6983b6222815c5c77a3dfd0b3845650
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a>方法: Visual Basic でファイルを削除する
`My.Computer.FileSystem` オブジェクトの `DeleteFile` メソッドを使用すると、ファイルを削除することができます。 削除したファイルを**ごみ箱**に送るかどうか、ファイルを削除することをユーザーに確認するかどうか、ユーザーが操作をキャンセルした場合の処理方法などが、オプションとして用意されています。  
  
### <a name="to-delete-a-text-file"></a>テキスト ファイルを削除するには  
  
-   `DeleteFile` メソッドを使用してファイルを削除します。 次のコードは、`test.txt` という名前のファイルを削除する方法の例です。  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>テキスト ファイルを削除して、ユーザーがファイルを削除することを確認するには  
  
-   `showUI` を `AllDialogs` に設定し、`DeleteFile` メソッドを使用してファイルを削除します。 次のコードは、`test.txt` という名前のファイルを、ユーザーに削除するファイルを確認した上で削除する方法の例です。  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>テキスト ファイルを削除してごみ箱に送るには  
  
-   `recycle` パラメーターに `SendToRecycleBin` を指定し、`DeleteFile` メソッドを使用してファイルを削除します。 次のコードは、`test.txt` という名前のファイルを削除して**ごみ箱**に送る方法の例です。  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   ファイルが使用中の場合 (<xref:System.IO.IOException>)。  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
-   ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。  
  
-   ファイルの削除に必要なアクセス許可がユーザーにないか、またはファイルが読み取り専用である (<xref:System.UnauthorizedAccessException>)。  
  
-   部分信頼の状況下で、必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。  
  
-   ユーザーが操作を取り消し、`onUserCancel` が `ThrowException` に設定されている (<xref:System.OperationCanceledException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [方法: ディレクトリにあるファイルのコレクションを取得する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
