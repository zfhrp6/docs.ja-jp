---
title: "方法: ファイルにテキストを書き込む (Visual Basic) | Microsoft Docs"
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
- files, writing to
- text, writing to files
- writing to files
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: 19
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
ms.openlocfilehash: 8febfbb5d4fb9042f2d9153a81aa18bd279cf3dc
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>方法: ファイルにテキストを書き込む (Visual Basic)
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使うと、ファイルにテキストを書き込むことができます。 指定したファイルが存在しない場合は、作成されます。  
  
## <a name="procedure"></a>プロシージャ  
  
#### <a name="to-write-text-to-a-file"></a>テキストをファイルに書き込むには  
  
-   ファイルにテキストを書き込むには `WriteAllText` メソッドを使い、ファイルと書き込むテキストを指定します。 この例では、`test.txt` という名前のファイルに既に存在するテキストの最後に、`"This is new text."` という行を書き込んで追加します。  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>一連の文字列をファイルに書き込むには  
  
-   文字列のコレクションをループ処理します。 `WriteAllText` メソッドを使って、テキストをファイルに書き込みます。書き込むファイルと追加する文字列を指定し、`append` を `True` に設定します。  
  
     この例では、`Documents and Settings` ディレクトリにあるファイルの名前を `FileList.txt` に書き込み、読みやすくするために各ファイル名の間に改行を挿入します。  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効である。これには、1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられます (<xref:System.ArgumentException>)。  
  
-   パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)。  
  
-   `File` が存在しないパスを指定している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。  
  
-   他のプロセスがファイルを使用している、または I/O エラーが発生した (<xref:System.IO.IOException>)。  
  
-   パスがシステムで定義された最大長を超えている (<xref:System.IO.PathTooLongException>)。  
  
-   パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)。  
  
-   ユーザーがパスを表示するために必要なアクセス許可がない (<xref:System.Security.SecurityException>)。  
  
-   ディスクに空きがなく、`WriteAllText` の呼び出しが失敗する (<xref:System.IO.IOException>)。  
  
 部分的に信頼されたコンテキストで実行している場合、コードは、特権がないために例外をスローする可能性があります。 詳しくは、「[コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 [方法: テキスト ファイルからデータを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
