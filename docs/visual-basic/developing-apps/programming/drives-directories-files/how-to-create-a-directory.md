---
title: "方法 : Visual Basic でディレクトリを作成する"
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
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
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="54d3b-102">方法 : Visual Basic でディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="54d3b-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="54d3b-103">ディレクトリを作成するには、`My.Computer.FileSystem` オブジェクトの `CreateDirectory` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="54d3b-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="54d3b-104">ディレクトリが既にある場合、例外はスローされません。</span><span class="sxs-lookup"><span data-stu-id="54d3b-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="54d3b-105">ディレクトリを作成するには</span><span class="sxs-lookup"><span data-stu-id="54d3b-105">To create a directory</span></span>  
  
-   <span data-ttu-id="54d3b-106">ディレクトリを作成する場所を完全にパスに指定して、`CreateDirectory` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="54d3b-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="54d3b-107">この例では、`C:\Documents and Settings\All Users\Documents` に `NewDirectory` ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="54d3b-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     <span data-ttu-id="54d3b-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="54d3b-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="54d3b-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="54d3b-109">Robust Programming</span></span>  
 <span data-ttu-id="54d3b-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54d3b-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="54d3b-111">ディレクトリ名が不正な場合。</span><span class="sxs-lookup"><span data-stu-id="54d3b-111">The directory name is malformed.</span></span> <span data-ttu-id="54d3b-112">たとえば、不正な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="54d3b-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="54d3b-113">作成するディレクトリの親ディレクトリが読み取り専用である場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="54d3b-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="54d3b-114">ディレクトリ名が `Nothing` の場合 (<xref:System.ArgumentNullException>)｡</span><span class="sxs-lookup"><span data-stu-id="54d3b-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="54d3b-115">ディレクトリ名が長すぎる場合 (<xref:System.IO.PathTooLongException>)｡</span><span class="sxs-lookup"><span data-stu-id="54d3b-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="54d3b-116">ディレクトリ名がコロン ":" の場合 (<xref:System.NotSupportedException>)｡</span><span class="sxs-lookup"><span data-stu-id="54d3b-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="54d3b-117">ユーザーがディレクトリを作成するアクセス許可を持っていない場合 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="54d3b-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="54d3b-118">部分的に信頼されている状況でユーザーにアクセス許可がない場合 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="54d3b-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d3b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="54d3b-119">See Also</span></span>  
 <span data-ttu-id="54d3b-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="54d3b-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span></span>   
 [<span data-ttu-id="54d3b-121">ファイルおよびディレクトリの作成、削除、および移動</span><span class="sxs-lookup"><span data-stu-id="54d3b-121">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

