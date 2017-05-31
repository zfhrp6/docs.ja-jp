---
title: "方法 : Visual Basic でバイナリ ファイルに書き込む | Microsoft Docs"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.openlocfilehash: 0d86e39b7150b4ae8fc4de0498b0b786c5669bb4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>方法 : Visual Basic でバイナリ ファイルに書き込む
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> メソッドは、データをバイナリ ファイルに書き込みます。 `append` パラメーターが `True` の場合、データはファイルに追加されます。それ以外の場合は、ファイル内のデータが上書きされます。  
  
 指定されたパスのファイル名を除く部分が有効でない場合は、<xref:System.IO.DirectoryNotFoundException> 例外がスローされます。 パスが有効でもファイルが存在しない場合は、ファイルが作成されます。  
  
### <a name="to-write-to-a-binary-file"></a>バイナリ ファイルに書き込むには  
  
-   `WriteAllBytes` メソッドを使い、ファイルのパス、ファイルの名前、書き込むバイトを指定します。 この例では、データ配列 `CustomerData` を `CollectedData.dat` という名前のファイルに追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   文字列の長さが 0 である、空白文字だけが含まれる、または無効な文字が含まれるために、パスが無効である (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)。  
  
-   `File` が存在しないパスを指定している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。  
  
-   他のプロセスがファイルを使用している、または I/O エラーが発生した (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義された最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   ユーザーがパスを表示するために必要なアクセス許可がない (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [方法: ファイルにテキストを書き込む](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
