---
title: "方法: My Documents ディレクトリの内容を取得する (Visual Basic)"
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
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: 13
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: afe236c4b9245ac256fbcbf6bf453de5d706b80f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>方法: My Documents ディレクトリの内容を取得する (Visual Basic)
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> オブジェクトを使用すると、**My Documents** や **Desktop** など、多くの **All Users** ディレクトリを読み取ることができます。  
  
### <a name="to-read-from-the-my-documents-folder"></a>My Documents フォルダーを読み取るには  
  
-   `ReadAllText` メソッドを使用して、指定したディレクトリの各ファイルからテキストを読み取ります。 次のコードでは、ディレクトリとファイルを指定し、`ReadAllText` を使用して、`patients` という名前の文字列に読み取ります。  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>

