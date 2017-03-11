---
title: "How to: Find Subdirectories with a Specific Pattern in Visual Basic | Microsoft Docs"
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
  - "pattern matching"
  - "folders, finding"
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Find Subdirectories with a Specific Pattern in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> メソッドは、ディレクトリ内のサブディレクトリのパス名を表す文字列の読み取り専用のコレクションを返します。  `wildCards` パラメーターを使用して、特定のパターンを指定できます。  サブディレクトリの内容を検索対象に含めるには、`searchType` パラメーターを `SearchOption.SearchAllSubDirectories` に設定します。  
  
 指定したパターンに一致するディレクトリが見つからなかった場合は、空のコレクションが戻ります。  
  
### 特定のパターンに一致するサブディレクトリを検索するには  
  
-   `GetDirectories` メソッドを使用して、検索するディレクトリの名前およびパスを指定します。  次の例では、ディレクトリ構造内のディレクトリのうちで、名前に "Logs" という単語を含むものをすべて取得し、`ListBox1` に追加します。  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-find-subdirectori_1.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   指定したワイルドカード文字の中に、`Nothing`、空の文字列、または空白のみが含まれている \(<xref:System.ArgumentNullException>\)。  
  
-   `directory` が存在しない \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   `directory` は既存のファイルである \(<xref:System.IO.IOException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはフォルダー名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   ユーザーに必要なアクセス許可がない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>   
 [How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)