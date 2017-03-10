---
title: "How to: Create a File in Visual Basic | Microsoft Docs"
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
  - "text files, creating"
  - "files, creating"
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

この例では、<xref:System.IO.File> クラスの <xref:System.IO.File.Create%2A> メソッドを使用して、指定したパスに空のテキスト ファイルを作成します。  
  
## 使用例  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-create-a-file_1.vb)]  
  
## コードのコンパイル  
 `file` 変数を使用して、ファイルに書き込みます。  
  
## 信頼性の高いプログラミング  
 ファイルが既に存在する場合は、新しいファイルに置き換えられます。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名の形式に誤りがある。  たとえば、不正な文字が含まれているか、空白のみである \(<xref:System.ArgumentException>\)。  
  
-   パスが読み取り専用である場合 \(<xref:System.IO.IOException>\)。  
  
-   パス名が `Nothing` である場合 \(<xref:System.ArgumentNullException>\)。  
  
-   パス名が長すぎる場合 \(<xref:System.IO.PathTooLongException>\)。  
  
-   パスが無効である場合 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   パスにコロン \(":"\) だけが指定されている場合 \(<xref:System.NotSupportedException>\)。  
  
## .NET Framework セキュリティ  
 部分信頼の環境では、<xref:System.Security.SecurityException> がスローされることがあります。  
  
 <xref:System.IO.File.Create%2A> メソッドの呼び出しでは、<xref:System.Security.Permissions.FileIOPermission> が必要です。  
  
 ユーザーにファイル作成のアクセス許可がない場合には、<xref:System.UnauthorizedAccessException> がスローされます。  
  
## 参照  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [部分信頼コードからのライブラリの使用](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)