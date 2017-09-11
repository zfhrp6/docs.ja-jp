---
title: "方法: StreamReader を使用してファイルからテキストを読み取る (Visual Basic)"
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
- reading files, text
- text, reading from files
- reading text from files
- files, reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
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
ms.openlocfilehash: d895b32b1613462a6c8dedcc19040b5040f936ec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="945ca-102">方法: StreamReader を使用してファイルからテキストを読み取る (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="945ca-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="945ca-103">`My.Computer.FileSystem` オブジェクトには、<xref:System.IO.TextReader> および <xref:System.IO.TextWriter> を開くためのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="945ca-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="945ca-104">これらのメソッド (`OpenTextFileWriter` メソッドと `OpenTextFileReader` メソッド) は、高度なメソッドで、**[すべて]** タブを選択しないと IntelliSense で表示されません。</span><span class="sxs-lookup"><span data-stu-id="945ca-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="945ca-105">テキスト リーダーを使用してファイルから行を読み取るには</span><span class="sxs-lookup"><span data-stu-id="945ca-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="945ca-106">`OpenTextFileReader` メソッドにファイルを指定して <xref:System.IO.TextReader> を開きます。</span><span class="sxs-lookup"><span data-stu-id="945ca-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="945ca-107">この例では、`testfile.txt` という名前のファイルを開き、1 行を読み取って、その行をメッセージ ボックスに表示します。</span><span class="sxs-lookup"><span data-stu-id="945ca-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     <span data-ttu-id="945ca-108">[!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="945ca-108">[!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="945ca-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="945ca-109">Robust Programming</span></span>  
 <span data-ttu-id="945ca-110">読み取るファイルは、テキスト ファイルである必要があります。</span><span class="sxs-lookup"><span data-stu-id="945ca-110">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="945ca-111">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="945ca-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="945ca-112">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="945ca-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="945ca-113">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="945ca-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="945ca-114">ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="945ca-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="945ca-115">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="945ca-115">.NET Framework Security</span></span>  
 <span data-ttu-id="945ca-116">ファイルを読み取るには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission> クラスで特権レベルが許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="945ca-116">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="945ca-117">部分的に信頼されているコンテキストで実行している場合は、特権不足のため例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="945ca-117">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="945ca-118">詳しくは、「[コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="945ca-118">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span> <span data-ttu-id="945ca-119">また、ユーザーはファイルへのアクセス許可も必要です。</span><span class="sxs-lookup"><span data-stu-id="945ca-119">The user also needs access to the file.</span></span> <span data-ttu-id="945ca-120">詳細については、「[アクセス制御リスト (ACL: Access Control List) 技術の概要](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="945ca-120">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945ca-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="945ca-121">See Also</span></span>  
 <span data-ttu-id="945ca-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="945ca-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="945ca-123"><xref:System.Windows.Forms.OpenFileDialog></span><span class="sxs-lookup"><span data-stu-id="945ca-123"><xref:System.Windows.Forms.OpenFileDialog></span></span>   
 <span data-ttu-id="945ca-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span><span class="sxs-lookup"><span data-stu-id="945ca-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span></span>   
 <span data-ttu-id="945ca-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A></span><span class="sxs-lookup"><span data-stu-id="945ca-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A></span></span>   
 <span data-ttu-id="945ca-126">[SaveFileDialog コンポーネント](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) </span><span class="sxs-lookup"><span data-stu-id="945ca-126">[SaveFileDialog Component](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) </span></span>  
 [<span data-ttu-id="945ca-127">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="945ca-127">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)

