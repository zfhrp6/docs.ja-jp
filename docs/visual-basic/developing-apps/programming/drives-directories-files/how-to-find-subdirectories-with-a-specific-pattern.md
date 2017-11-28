---
title: "方法: 特定のパターンに一致するサブディレクトリを検索する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c4549f417e86e82897ca32d8d7cf22aaf462c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="8124e-102">方法: 特定のパターンに一致するサブディレクトリを検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8124e-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="8124e-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> メソッドは、ディレクトリのサブディレクトリのパス名を表す文字列の読み取り専用のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="8124e-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="8124e-104">`wildCards` パラメーターを使用して、特定のパターンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8124e-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="8124e-105">サブディレクトリの内容を検索対象に含めるには、`searchType` パラメーターを `SearchOption.SearchAllSubDirectories` に設定します。</span><span class="sxs-lookup"><span data-stu-id="8124e-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="8124e-106">指定したパターンに一致するディレクトリが見つからなかった場合は、空のコレクションが返されます。</span><span class="sxs-lookup"><span data-stu-id="8124e-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="8124e-107">特定のパターンに一致するサブディレクトリを検索するには</span><span class="sxs-lookup"><span data-stu-id="8124e-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="8124e-108">検索するディレクトリの名前およびパスを指定して、`GetDirectories` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8124e-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="8124e-109">次の例では、ディレクトリ構造内で名前に "Logs" という単語を含むすべてのディレクトリが返され、`ListBox1` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="8124e-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8124e-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="8124e-110">Robust Programming</span></span>  
 <span data-ttu-id="8124e-111">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8124e-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8124e-112">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="8124e-113">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="8124e-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8124e-114">指定したワイルドカード文字の中に 1 つ以上の `Nothing`、空の文字列が含まれている、または空白のみである (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8124e-115">`directory` が存在しない (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="8124e-116">`directory` が既存のファイルを指している (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="8124e-117">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="8124e-118">パス内のファイル名またはフォルダー名にコロン (:) が含まれている、または形式が無効である (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="8124e-119">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="8124e-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="8124e-120">ユーザーに必要な権限がない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="8124e-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8124e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8124e-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [<span data-ttu-id="8124e-122">方法: 特定のパターンに一致するファイルを検索する</span><span class="sxs-lookup"><span data-stu-id="8124e-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
