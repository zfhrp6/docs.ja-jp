---
title: "方法 : Visual Basic でテキスト ファイルに追記する | Microsoft Docs"
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
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
caps.latest.revision: 13
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
ms.openlocfilehash: eac2d621ba4fe2afebc9eb73f4723c3a869a23a8
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>方法 : Visual Basic でテキスト ファイルに追記する
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用し、`append` パラメーターが `True` に設定されていることを指定して、テキスト ファイルに追加できます。  
  
### <a name="to-append-to-a-text-file"></a>テキスト ファイルに追加するには  
  
-   `WriteAllText` メソッドを使って、ターゲット ファイルと追加する文字列を指定し、`append` パラメーターを `True` に設定します。  
  
     この例では、文字列 `"This is a test string."` を `Testfile.txt` という名前のファイルに書き込みます。  
  
     [!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-append-to-text-files_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効である。これには、1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられます (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)。  
  
-   `File` が存在しないパスを指定している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。  
  
-   他のプロセスがファイルを使用している、または I/O エラーが発生した (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義された最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   ユーザーがパスを表示するために必要なアクセス許可がない (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [ファイルへの書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
