---
title: "方法 : Visual Basic でファイルを作成する"
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
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
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
ms.openlocfilehash: d06d274b31afad0a437405d1679e0be7548f2e14
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="337b5-102">方法 : Visual Basic でファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="337b5-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="337b5-103">この例では、<xref:System.IO.File> クラスで <xref:System.IO.File.Create%2A> メソッドを使用して、指定したパスに空のテキスト ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="337b5-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="337b5-104">例</span><span class="sxs-lookup"><span data-stu-id="337b5-104">Example</span></span>  
 <span data-ttu-id="337b5-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="337b5-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="337b5-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="337b5-106">Compiling the Code</span></span>  
 <span data-ttu-id="337b5-107">ファイルに書き込むには、`file` 変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="337b5-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="337b5-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="337b5-108">Robust Programming</span></span>  
 <span data-ttu-id="337b5-109">ファイルが既に存在する場合、それは置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="337b5-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="337b5-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="337b5-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="337b5-111">パス名が不適切である場合。</span><span class="sxs-lookup"><span data-stu-id="337b5-111">The path name is malformed.</span></span> <span data-ttu-id="337b5-112">たとえば、不正な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="337b5-113">パスが読み取り専用の場合 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="337b5-114">パス名が `Nothing` の場合 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="337b5-115">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="337b5-116">パスが無効な場合 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="337b5-117">パスがコロン ":" のみである場合 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="337b5-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="337b5-118">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="337b5-118">.NET Framework Security</span></span>  
 <span data-ttu-id="337b5-119">部分信頼環境では、<xref:System.Security.SecurityException> がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="337b5-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="337b5-120"><xref:System.IO.File.Create%2A> メソッドへの呼び出しでは、<xref:System.Security.Permissions.FileIOPermission> が必要です。</span><span class="sxs-lookup"><span data-stu-id="337b5-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="337b5-121">ユーザーがファイルを作成するアクセス許可を持っていない場合、<xref:System.UnauthorizedAccessException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="337b5-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337b5-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="337b5-122">See Also</span></span>  
 <span data-ttu-id="337b5-123"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="337b5-123"><xref:System.IO></span></span>   
 <span data-ttu-id="337b5-124"><xref:System.IO.File.Create%2A></span><span class="sxs-lookup"><span data-stu-id="337b5-124"><xref:System.IO.File.Create%2A></span></span>   
 <span data-ttu-id="337b5-125">[部分信頼コードからのライブラリの使用](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span><span class="sxs-lookup"><span data-stu-id="337b5-125">[Using Libraries from Partially Trusted Code](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span></span>  
 [<span data-ttu-id="337b5-126">コード アクセス セキュリティの基礎</span><span class="sxs-lookup"><span data-stu-id="337b5-126">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

