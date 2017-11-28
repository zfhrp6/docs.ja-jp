---
title: "方法: Visual Basic でバイナリ ファイルを読み取る"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6056f7d33b1137abb19b24246ce6874ff4d008
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="b50a7-102">方法: Visual Basic でバイナリ ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="b50a7-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="b50a7-103">`My.Computer.FileSystem` オブジェクトには、バイナリ ファイルを読み取るための `ReadAllBytes` メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b50a7-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="b50a7-104">バイナリ ファイルを読み取るには</span><span class="sxs-lookup"><span data-stu-id="b50a7-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="b50a7-105">`ReadAllBytes` メソッドを使用します。このメソッドは、ファイルの内容をバイト配列として返します。</span><span class="sxs-lookup"><span data-stu-id="b50a7-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="b50a7-106">次のコードは、`C:/Documents and Settings/selfportrait.jpg` ファイルから読み取りを行う例です。</span><span class="sxs-lookup"><span data-stu-id="b50a7-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   <span data-ttu-id="b50a7-107">大きいバイナリ ファイルの場合は、<xref:System.IO.FileStream> オブジェクトの <xref:System.IO.FileStream.Read%2A> メソッドを使用して、一度に指定した量だけファイルから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="b50a7-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="b50a7-108">その後、各読み取り操作でファイルからメモリに読み込まれる量を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="b50a7-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="b50a7-109">次のコード例では、ファイルをコピーし、各読み取り操作でファイルからメモリに読み込まれる量を呼び出し元が指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b50a7-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b50a7-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b50a7-110">Robust Programming</span></span>  
 <span data-ttu-id="b50a7-111">次の条件を満たす場合は、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b50a7-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="b50a7-112">パスが無効である場合。1) 長さが 0 の文字列である、2) 空白だけが含まれている、3) 無効な文字が含まれている、4) デバイス パスである、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="b50a7-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b50a7-113">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="b50a7-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b50a7-114">ファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="b50a7-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b50a7-115">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="b50a7-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b50a7-116">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="b50a7-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b50a7-117">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="b50a7-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="b50a7-118">文字列をバッファーに書き込むための十分なメモリがない (<xref:System.OutOfMemoryException>)</span><span class="sxs-lookup"><span data-stu-id="b50a7-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="b50a7-119">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="b50a7-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="b50a7-120">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="b50a7-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b50a7-121">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="b50a7-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="b50a7-122">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="b50a7-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="b50a7-123">ファイルの内容が予想どおりでないことがあり、ファイルの内容を読み取るメソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b50a7-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50a7-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b50a7-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="b50a7-125">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="b50a7-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="b50a7-126">方法: 複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="b50a7-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="b50a7-127">クリップボードのデータの格納と読み取り</span><span class="sxs-lookup"><span data-stu-id="b50a7-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
