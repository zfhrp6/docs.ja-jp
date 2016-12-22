---
title: "How to: Retrieve the Contents of the My Documents Directory in Visual Basic | Microsoft Docs"
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
  - "My Documents directory"
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Retrieve the Contents of the My Documents Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> オブジェクトを使用すると、**Desktop** や **My Documents** など、多くの **All Users** ディレクトリを読み取ることができます。  
  
### My Documents フォルダーを読み取るには  
  
-   `ReadAllText` メソッドを使用して、指定したディレクトリの各ファイルからテキストを読み取ります。  次のコードでは、ディレクトリとファイルを指定し、`ReadAllText` を使用して、`patients` という名前の文字列に読み取ります。  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>