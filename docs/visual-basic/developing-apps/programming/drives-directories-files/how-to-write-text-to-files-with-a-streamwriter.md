---
title: "方法: StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)"
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
- files, writing to
- text, writing to files
- writing to files, StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
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
ms.openlocfilehash: ea85d57e9af4fdd640733db5dc2fa8b0ab25325c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="e27e6-102">方法: StreamWriter を使用してファイルにテキストを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e27e6-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="e27e6-103">この例では、`My.Computer.FileSystem.OpenTextFileWriter` メソッドで <xref:System.IO.StreamWriter> オブジェクトを開き、そのオブジェクトを使用し、<xref:System.IO.StreamWriter> クラスの <xref:System.IO.TextWriter.WriteLine%2A> メソッドでテキスト ファイルに文字列を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e27e6-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e27e6-104">例</span><span class="sxs-lookup"><span data-stu-id="e27e6-104">Example</span></span>  
 <span data-ttu-id="e27e6-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e27e6-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e27e6-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="e27e6-106">Robust Programming</span></span>  
 <span data-ttu-id="e27e6-107">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e27e6-107">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e27e6-108">ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="e27e6-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e6-109">ディスクの空き領域がない場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="e27e6-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e6-110">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="e27e6-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e27e6-111">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e27e6-111">.NET Framework Security</span></span>  
 <span data-ttu-id="e27e6-112">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e27e6-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="e27e6-113">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="e27e6-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="e27e6-114">ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。</span><span class="sxs-lookup"><span data-stu-id="e27e6-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="e27e6-115">フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="e27e6-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27e6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e27e6-116">See Also</span></span>  
 <span data-ttu-id="e27e6-117"><xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="e27e6-117"><xref:System.IO.StreamWriter></span></span>   
 <span data-ttu-id="e27e6-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span><span class="sxs-lookup"><span data-stu-id="e27e6-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span></span>   
 <span data-ttu-id="e27e6-119">[方法: テキスト ファイルからデータを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="e27e6-119">[How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span></span>  
 [<span data-ttu-id="e27e6-120">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="e27e6-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)

