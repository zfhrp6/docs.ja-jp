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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="a7a45-102">方法: My Documents ディレクトリの内容を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7a45-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="a7a45-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> オブジェクトを使用すると、**My Documents** や **Desktop** など、多くの **All Users** ディレクトリを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a7a45-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="a7a45-104">My Documents フォルダーを読み取るには</span><span class="sxs-lookup"><span data-stu-id="a7a45-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="a7a45-105">`ReadAllText` メソッドを使用して、指定したディレクトリの各ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a7a45-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="a7a45-106">次のコードでは、ディレクトリとファイルを指定し、`ReadAllText` を使用して、`patients` という名前の文字列に読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a7a45-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     <span data-ttu-id="a7a45-107">[!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a7a45-107">[!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a45-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7a45-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>

