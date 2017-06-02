---
title: "方法: Visual Basic でディレクトリにあるファイルのコレクションを取得する | Microsoft Docs"
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
- folders, working with
- files, accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
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
ms.openlocfilehash: 1884195983856b3331b0c40e5b3844b0731e75ac
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>方法: Visual Basic でディレクトリにあるファイルのコレクションを取得する
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> メソッドのオーバーロードは、ディレクトリ内のファイルの名前を表す、文字列の読み取り専用のコレクションを返します。  
  
-   指定されたディレクトリ内を検索し、サブディレクトリを検索しない単純なファイル検索には <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> オーバーロードを使用します。  
  
-   検索に追加オプションを指定するには、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> オーバーロードを使用します。 `wildCards` パラメーターを使用して、検索パターンを指定できます。 検索にサブディレクトリを含めるには、`searchType` パラメーターを <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName> に設定します。  
  
 指定したパターンに一致するファイルがない場合は、空のコレクションが返されます。  
  
### <a name="to-list-files-in-a-directory"></a>ディレクトリ内のファイルをリストするには  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> メソッドのオーバーロードのいずれかを使用して、検索するディレクトリの名前とパスを `directory` パラメーターに指定します。 次の例では、ディレクトリ内のすべてのファイルが返され、`ListBox1` に追加されます。  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)  
  
-   `directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   `directory` が既存のファイルを指している (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)  
  
-   ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [方法: 特定のパターンに一致するファイルを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [方法: 特定のパターンに一致するサブディレクトリを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)

