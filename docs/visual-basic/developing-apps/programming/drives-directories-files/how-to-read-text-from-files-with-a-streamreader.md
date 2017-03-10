---
title: "How to: Read Text from Files with a StreamReader (Visual Basic) | Microsoft Docs"
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
  - "reading files, text"
  - "text, reading from files"
  - "reading text from files"
  - "files, reading"
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Read Text from Files with a StreamReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトには、<xref:System.IO.TextReader> および <xref:System.IO.TextWriter> を開くためのメソッドがあります。  `OpenTextFileWriter` メソッドと `OpenTextFileReader` メソッドです。これらは高度なメソッドで、**\[すべての候補\]** タブを選択しないと IntelliSense で表示されません。  
  
### テキスト リーダーを使用してファイルから行を読み取るには  
  
-   `OpenTextFileReader` メソッドにファイルを指定して <xref:System.IO.TextReader> を開きます。  この例では、`testfile.txt` という名前のファイルを開き、1 行を読み取って、その行をメッセージ ボックスに表示します。  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-text-from-fi_1.vb)]  
  
## 信頼性の高いプログラミング  
 読み取るファイルはテキスト ファイルである必要があります。  
  
 ファイル名からファイルの内容を判断しないでください。  たとえば、Form1.vb というファイルが Visual Basic のソース ファイルではない可能性もあります。  
  
 アプリケーションでデータを使用する前に、入力をすべて検証してください。  ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。  
  
## .NET Framework セキュリティ  
 ファイルを読み取るには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission> クラスで特権レベルが許可されている必要があります。  部分的に信頼されているコンテキストでプロセスを実行している場合は、特権不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)」を参照してください。  また、ユーザーは、ファイルに対するアクセスも必要です。  詳細については、「[ACL Technology Overview](http://msdn.microsoft.com/ja-jp/06fbf66d-6f02-4378-b863-b2f12e349045)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:System.Windows.Forms.OpenFileDialog>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>   
 [SaveFileDialog コンポーネント](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md)   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)