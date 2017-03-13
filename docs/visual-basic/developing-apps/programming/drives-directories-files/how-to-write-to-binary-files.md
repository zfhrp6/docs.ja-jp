---
title: "How to: Write to Binary Files in Visual Basic | Microsoft Docs"
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
  - "files, binary access"
  - "WriteAllBytes method"
  - "binary files, writing in Visual Basic"
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Write to Binary Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> メソッドはバイナリ ファイルにデータを書き込みます。  `append` パラメーターが `True` の場合は、ファイルにデータを追加します。その他の場合は、ファイルのデータを上書きします。  
  
 指定したパス \(ファイル名以外\) が有効でない場合は、<xref:System.IO.DirectoryNotFoundException> 例外がスローされます。  パスが有効でファイルが存在しない場合は、ファイルが作成されます。  
  
### バイナリ ファイルに書き込むには  
  
-   `WriteAllBytes` メソッドを使用し、ファイルのパスと名前、および書き込むバイト数を指定します。  この例では、データ配列 `CustomerData` を、`CollectedData.dat` という名前のファイルに追加します。  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## 信頼性の高いプログラミング  
 例外を引き起こす可能性のある状態を次に示します。  
  
-   パスが無効である。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、のいずれかの理由が考えられる。  \(<xref:System.ArgumentException>\).  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   `File` は存在しないパスを指している \(<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>\)。  
  
-   他のプロセスがファイルを使用しているか、または I\/O エラーが発生した \(<xref:System.IO.IOException>\)  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはディレクトリ名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [How to: Write Text to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)