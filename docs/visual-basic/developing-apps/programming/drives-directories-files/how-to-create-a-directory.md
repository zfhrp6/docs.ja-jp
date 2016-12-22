---
title: "How to: Create a Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "directories [Visual Basic], creating"
  - "folders [Visual Basic], creating"
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.FileSystem` オブジェクトの `CreateDirectory` メソッドを使用すると、ディレクトリを作成できます。  
  
 ディレクトリが既に存在している場合、例外はスローされません。  
  
### ディレクトリを作成するには  
  
-   `CreateDirectory` メソッドに、ディレクトリを作成する場所の完全パスを指定します。  この例では、`NewDirectory` ディレクトリを `C:\Documents and Settings\All Users\Documents` に作成します。  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ディレクトリ名が不適切である。  たとえば、不正な文字が含まれているか、空白のみである \(<xref:System.ArgumentException>\)。  
  
-   作成するディレクトリの親ディレクトリが読み取り専用である \(<xref:System.IO.IOException>\)。  
  
-   ディレクトリ名が `Nothing` である \(<xref:System.ArgumentNullException>\)。  
  
-   ディレクトリ名が長すぎる \(<xref:System.IO.PathTooLongException>\)。  
  
-   ディレクトリ名がコロン \(":"\) である \(<xref:System.NotSupportedException>\)。  
  
-   ディレクトリを作成するためのアクセス許可がユーザーにない \(<xref:System.UnauthorizedAccessException>\)。  
  
-   部分信頼の状況でユーザーにアクセス許可がない \(<xref:System.Security.SecurityException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [Creating, Deleting, and Moving Files and Directories](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)