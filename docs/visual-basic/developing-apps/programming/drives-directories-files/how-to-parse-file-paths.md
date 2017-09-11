---
title: "方法 : Visual Basic でファイル パスを解析する"
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
- file names, parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6327d661c6f1fe7647cc64b56d7f72f1f3455467
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="efdd4-102">方法 : Visual Basic でファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="efdd4-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="efdd4-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> オブジェクトには、ファイル パスを解析するときに役立つメソッドがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="efdd4-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="efdd4-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> メソッドは、2 つのパスを受け取り、適切な書式で結合されたパスを返します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="efdd4-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> メソッドは、指定されたパスの親の絶対パスを返します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="efdd4-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドは、 <xref:System.IO.FileInfo> オブジェクトを返します。このオブジェクトを照会すると、ファイルのプロパティ (名前やパスなど) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="efdd4-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="efdd4-107">ファイル名の拡張子に基づいてファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="efdd4-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="efdd4-108">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="efdd4-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="efdd4-109">ファイルの名前とパスを確認するには</span><span class="sxs-lookup"><span data-stu-id="efdd4-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="efdd4-110"><xref:System.IO.FileInfo.DirectoryName%2A> オブジェクトの <xref:System.IO.FileInfo.Name%2A> および <xref:System.IO.FileInfo> プロパティを使用して、ファイルの名前とパスを確認します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="efdd4-111">この例は、名前とパスを確認し、それらを表示します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-111">This example determines the name and path and displays them.</span></span>  
  
     <span data-ttu-id="efdd4-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="efdd4-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span></span>  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="efdd4-113">ファイルの名前とディレクトリを結合して完全パスを作成するには</span><span class="sxs-lookup"><span data-stu-id="efdd4-113">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="efdd4-114">`CombinePath` メソッドを使用し、ディレクトリと名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-114">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="efdd4-115">この例では、前の例で作成した文字列 `folderPath` と `fileName` を受け取って、両者を結合し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="efdd4-115">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     <span data-ttu-id="efdd4-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="efdd4-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efdd4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="efdd4-117">See Also</span></span>  
 <span data-ttu-id="efdd4-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="efdd4-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="efdd4-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span><span class="sxs-lookup"><span data-stu-id="efdd4-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span></span>   
 <span data-ttu-id="efdd4-120"><xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="efdd4-120"><xref:System.IO.FileInfo></span></span>   
 <span data-ttu-id="efdd4-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span><span class="sxs-lookup"><span data-stu-id="efdd4-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span></span>   
 [<span data-ttu-id="efdd4-122">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="efdd4-122">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

