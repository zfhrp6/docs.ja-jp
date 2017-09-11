---
title: "方法 : Visual Basic でテキスト ファイルに追記する"
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
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
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
ms.openlocfilehash: 3425c82ed73e4a6fbded187b9333f4083111e78f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="f3172-102">方法 : Visual Basic でテキスト ファイルに追記する</span><span class="sxs-lookup"><span data-stu-id="f3172-102">How to: Append to Text Files in Visual Basic</span></span>
<span data-ttu-id="f3172-103">`append` パラメーターが `True` に設定されるように指定して、<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを使いテキスト ファイルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="f3172-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="f3172-104">テキスト ファイルに追加するには</span><span class="sxs-lookup"><span data-stu-id="f3172-104">To append to a text file</span></span>  
  
-   <span data-ttu-id="f3172-105">`WriteAllText` メソッドを使って、ターゲット ファイルと追加する文字列を指定し、`append` パラメーターを `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f3172-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="f3172-106">この例では、文字列 `"This is a test string."` を `Testfile.txt` という名前のファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f3172-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     <span data-ttu-id="f3172-107">[!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-append-to-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f3172-107">[!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-append-to-text-files_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f3172-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f3172-108">Robust Programming</span></span>  
 <span data-ttu-id="f3172-109">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f3172-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f3172-110">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="f3172-110">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f3172-111">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="f3172-111">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f3172-112">`File` が、存在しないパスを指している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="f3172-112">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f3172-113">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f3172-113">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f3172-114">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="f3172-114">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f3172-115">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="f3172-115">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="f3172-116">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="f3172-116">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3172-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3172-117">See Also</span></span>  
 <span data-ttu-id="f3172-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span><span class="sxs-lookup"><span data-stu-id="f3172-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span></span>   
 <span data-ttu-id="f3172-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="f3172-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 [<span data-ttu-id="f3172-120">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="f3172-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)

