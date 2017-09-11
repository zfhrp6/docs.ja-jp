---
title: "方法: 特定のパターンに一致するファイルを検索する (Visual Basic)"
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
- files, finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: 23
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
ms.openlocfilehash: 5e5d7dc692bf68ebccc459e9cf3f92c3683b8145
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="b575c-102">方法: 特定のパターンに一致するファイルを検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b575c-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="b575c-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> メソッドは、ファイルのパス名を表す文字列の読み取り専用のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="b575c-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="b575c-104">`wildCards` パラメーターを使用して、特定のパターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b575c-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="b575c-105">サブディレクトリを検索対象に含めるには、`searchType` パラメーターを `SearchOption.SearchAllSubDirectories` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b575c-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="b575c-106">指定したパターンに一致するファイルがない場合は、空のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="b575c-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b575c-107">`System.IO` 名前空間の `DirectoryInfo` クラスを使用してファイルの一覧を返す方法については、「<xref:System.IO.DirectoryInfo.GetFiles%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b575c-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="b575c-108">特定のパターンに一致するファイルを検索するには</span><span class="sxs-lookup"><span data-stu-id="b575c-108">To find files with a specified pattern</span></span>  
  
-   <span data-ttu-id="b575c-109">検索するディレクトリの名前とパス、およびパターンを指定して、`GetFiles` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b575c-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="b575c-110">次の例では、ディレクトリ内にある拡張子が `.dll` のファイルがすべて返され、`ListBox1` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="b575c-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     <span data-ttu-id="b575c-111">[!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b575c-111">[!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b575c-112">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="b575c-112">.NET Framework Security</span></span>  
 <span data-ttu-id="b575c-113">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b575c-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b575c-114">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b575c-115">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="b575c-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b575c-116">`directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b575c-117">`directory` が既存のファイルを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b575c-118">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b575c-119">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="b575c-120">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="b575c-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b575c-121">ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="b575c-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b575c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b575c-122">See Also</span></span>  
 <span data-ttu-id="b575c-123"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A></span><span class="sxs-lookup"><span data-stu-id="b575c-123"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A></span></span>   
 <span data-ttu-id="b575c-124">[方法: 特定のパターンに一致するサブディレクトリを検索する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="b575c-124">[How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span></span>  
 <span data-ttu-id="b575c-125">[トラブルシューティング : テキスト ファイルの読み取りと書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="b575c-125">[Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span></span>  
 [<span data-ttu-id="b575c-126">方法: ディレクトリにあるファイルのコレクションを取得する</span><span class="sxs-lookup"><span data-stu-id="b575c-126">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

