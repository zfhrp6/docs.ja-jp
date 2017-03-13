---
title: "How to: Write Text to Files in Visual Basic | Microsoft Docs"
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
  - "files, writing to"
  - "text, writing to files"
  - "writing to files"
  - "examples [Visual Basic], text files"
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Write Text to Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使用すると、テキストをファイルに書き込むことができます。  指定したファイルが存在しない場合は、新たに作成されます。  
  
## 手順  
  
#### テキストをファイルに書き込むには  
  
-   `WriteAllText` メソッドを使用して、ファイルおよび書き込むテキストを指定し、テキストをファイルに書き込みます。  この例では、`"This is new text."` という行を `test.txt` という名前のファイルに書き込みます。ファイルに既存のテキストがある場合は、この行を追加します。  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### 複数の文字列をファイルに書き込むには  
  
-   文字列コレクションに対し反復処理を行います。  `WriteAllText` メソッドを使用して、テキストをファイルに書き込みます。その際、対象のファイルおよび追加する文字列を指定し、`append` を `True` に設定します。  
  
     この例では、`Documents and Settings` ディレクトリにあるファイルの名前を `FileList.txt` に書き込みます。その際、それぞれの間に復帰を挿入して、読みやすくなるようにします。  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   `File` は存在しないパスを指している \(<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>\)。  
  
-   他のプロセスがファイルを使用しているか、または I\/O エラーが発生した \(<xref:System.IO.IOException>\)  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ディスクの空き領域がなく、`WriteAllText` の呼び出しが失敗した \(<xref:System.IO.IOException>\)。  
  
 部分的に信頼されているコンテキストでプロセスを実行している場合は、特権不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 [How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)