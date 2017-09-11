---
title: "方法 : Visual Basic でバイナリ ファイルに書き込む"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.openlocfilehash: ae6f275dd86a53c6b6251feb08210a775adba0b0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="63e66-102">方法 : Visual Basic でバイナリ ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="63e66-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="63e66-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> メソッドは、バイナリ ファイルにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="63e66-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="63e66-104">`append` パラメーターが `True` の場合、データはファイルに追加されます。それ以外の場合は、ファイル内のデータが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="63e66-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="63e66-105">指定されたパスのファイル名を除く部分が有効でない場合は、<xref:System.IO.DirectoryNotFoundException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="63e66-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="63e66-106">パスが有効でもファイルが存在しない場合は、ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="63e66-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="63e66-107">バイナリ ファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="63e66-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="63e66-108">`WriteAllBytes` メソッドを使い、ファイルのパス、ファイルの名前、書き込むバイトを指定します。</span><span class="sxs-lookup"><span data-stu-id="63e66-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="63e66-109">この例では、データ配列 `CustomerData` を `CollectedData.dat` という名前のファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="63e66-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     <span data-ttu-id="63e66-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="63e66-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="63e66-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="63e66-111">Robust Programming</span></span>  
 <span data-ttu-id="63e66-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="63e66-112">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="63e66-113">文字列の長さが 0 である、空白文字だけが含まれる、または無効な文字が含まれるために、パスが無効である</span><span class="sxs-lookup"><span data-stu-id="63e66-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="63e66-114">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="63e66-114">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="63e66-115">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="63e66-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="63e66-116">`File` が、存在しないパスを指している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="63e66-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="63e66-117">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="63e66-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="63e66-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="63e66-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="63e66-119">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="63e66-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="63e66-120">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="63e66-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e66-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="63e66-121">See Also</span></span>  
 <span data-ttu-id="63e66-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span><span class="sxs-lookup"><span data-stu-id="63e66-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span></span>   
 [<span data-ttu-id="63e66-123">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="63e66-123">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)

