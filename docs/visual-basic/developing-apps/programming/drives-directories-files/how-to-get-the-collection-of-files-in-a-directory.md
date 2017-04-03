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
ms.openlocfilehash: d5b36baee302db0214844e0553473a05603090f1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>方法: Visual Basic でディレクトリにあるファイルのコレクションを取得する
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> メソッドのオーバーロードは、ディレクトリ内のファイルの名前を表す、文字列の読み取り専用のコレクションを返します。  
  
-   指定されたディレクトリを検索し、サブディレクトリは検索しない単純なファイル検索には <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> オーバーロードを使用します。  
  
-   検索に追加オプションを指定するには、<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> オーバーロードを使用します。 `wildCards` パラメーターを使用して、検索パターンを指定できます。 検索にサブディレクトリを含めるには、`searchType` パラメーターを <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName> に設定します。  
  
 指定したパターンに一致するファイルがない場合は、空のコレクションが返されます。  
  
### <a name="to-list-files-in-a-directory"></a>ディレクトリ内のファイルをリストするには  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> メソッドのオーバーロードのいずれかを使用して、検索するディレクトリの名前とパスを `directory` パラメーターに指定します。 次の例では、ディレクトリ内のすべてのファイルが返され、`ListBox1` に追加されます。  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効である。これには、1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられます (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)。  
  
-   `directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   `directory` が既存のファイルを指している (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義された最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   パスの表示に必要なアクセス許可がユーザーにない (<xref:System.Security.SecurityException>)。  
  
-   ユーザーに必要なアクセス許可がない (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [方法: 特定のパターンに一致するファイルを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [方法: 特定のパターンに一致するサブディレクトリを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)

