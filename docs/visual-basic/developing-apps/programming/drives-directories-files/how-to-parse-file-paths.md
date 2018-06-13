---
title: '方法 : Visual Basic でファイル パスを解析する'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
ms.openlocfilehash: 7479f368558a8a8a07c1e6ed588bdfef21a0b1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585945"
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="0f616-102">方法 : Visual Basic でファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="0f616-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="0f616-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> オブジェクトには、ファイル パスを解析するときに役立つメソッドがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="0f616-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="0f616-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> メソッドは、2 つのパスを受け取り、適切な書式で結合されたパスを返します。</span><span class="sxs-lookup"><span data-stu-id="0f616-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="0f616-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> メソッドは、指定されたパスの親の絶対パスを返します。</span><span class="sxs-lookup"><span data-stu-id="0f616-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="0f616-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> メソッドは、 <xref:System.IO.FileInfo> オブジェクトを返します。このオブジェクトを照会すると、ファイルのプロパティ (名前やパスなど) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="0f616-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="0f616-107">ファイル名の拡張子に基づいてファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="0f616-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="0f616-108">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="0f616-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="0f616-109">ファイルの名前とパスを確認するには</span><span class="sxs-lookup"><span data-stu-id="0f616-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="0f616-110"><xref:System.IO.FileInfo.DirectoryName%2A> オブジェクトの <xref:System.IO.FileInfo.Name%2A> および <xref:System.IO.FileInfo> プロパティを使用して、ファイルの名前とパスを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f616-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="0f616-111">この例は、名前とパスを確認し、それらを表示します。</span><span class="sxs-lookup"><span data-stu-id="0f616-111">This example determines the name and path and displays them.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="0f616-112">ファイルの名前とディレクトリを結合して完全パスを作成するには</span><span class="sxs-lookup"><span data-stu-id="0f616-112">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="0f616-113">`CombinePath` メソッドを使用し、ディレクトリと名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f616-113">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="0f616-114">この例では、前の例で作成した文字列 `folderPath` と `fileName` を受け取って、両者を結合し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="0f616-114">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0f616-115">参照</span><span class="sxs-lookup"><span data-stu-id="0f616-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [<span data-ttu-id="0f616-116">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="0f616-116">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
