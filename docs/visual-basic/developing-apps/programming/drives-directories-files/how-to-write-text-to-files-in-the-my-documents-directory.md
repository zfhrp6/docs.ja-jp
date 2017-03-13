---
title: "How to: Write Text to Files in the My Documents Directory in Visual Basic | Microsoft Docs"
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
  - "examples [Visual Basic], text files"
  - "writing to files, in My Documents"
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Write Text to Files in the My Documents Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.FileSystem.SpecialDirectories` オブジェクトを使用すると、**MyDocuments** ディレクトリなどの特別なディレクトリにアクセスできます。  
  
## 手順  
  
#### My Documents ディレクトリに新しいテキスト ファイルを書き込むには  
  
1.  `My.Computer.FileSystem.SpecialDirectories.MyDocuments` プロパティを使用してパスを指定します。  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  `WriteAllText` メソッドを使用して、指定のファイルにテキストを書き込みます。  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## 使用例  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## コードのコンパイル  
 `test.txt` の部分を、書き込みを行うファイルの名前に置き換えてください。  
  
## 信頼性の高いプログラミング  
 このコードでは、ファイルにテキストを書き込むときに生じる可能性のあるすべての例外を再スローしています。  [OpenFileDialog](../Topic/OpenFileDialog%20Component%20\(Windows%20Forms\).md) コンポーネントおよび [SaveFileDialog](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md) コンポーネントなどの Windows フォーム コントロールを使用すると、例外の可能性を減らすことができます。有効なファイル名のみをユーザーが選択できるようになっているからです。  ただし、これらのコントロールを使用しても、完璧とは限りません。  ユーザーがファイルを選択してから、コードが実行されるまでの間に、ファイル システムが変更される可能性があります。  したがって、ファイルを操作するときには、例外処理はほぼ必須です。  
  
## .NET Framework セキュリティ  
 部分的に信頼されているコンテキストでプロセスを実行している場合は、特権不足のため例外がスローされることがあります。  詳細については、「[コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)」を参照してください。  
  
 この例では新しいファイルを作成します。  アプリケーションがファイルを作成する必要がある場合は、フォルダーの作成のアクセス許可が必要になります。  アクセス許可は、アクセス制御リストを使用して設定します。  ファイルが既に存在する場合、アプリケーションに必要なのは書き込みのアクセス許可だけです。  可能な場合は、フォルダーに対する作成の権限を付与するのではなく、配置時にファイルを作成し、1 つのファイルに対する読み取りの権限だけを付与する方が安全です。  また、ルート フォルダーや **Program Files** フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。  詳細については、「[ACL Technology Overview](http://msdn.microsoft.com/ja-jp/06fbf66d-6f02-4378-b863-b2f12e349045)」を参照してください。  
  
## 参照  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>