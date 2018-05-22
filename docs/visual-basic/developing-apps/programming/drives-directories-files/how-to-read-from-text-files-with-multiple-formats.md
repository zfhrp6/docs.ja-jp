---
title: '方法: Visual Basic で複数の書式を持つテキスト ファイルを読み取る'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 2c67e358e418ed8cbfddd9a8e7b03a60e46d6356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="9fa27-102">方法: Visual Basic で複数の書式を持つテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9fa27-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="9fa27-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。</span><span class="sxs-lookup"><span data-stu-id="9fa27-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="9fa27-104">`PeekChars` メソッドを使用して、ファイルを解析するときに各行の書式を判断すると、複数の書式を持つファイルを処理できます。</span><span class="sxs-lookup"><span data-stu-id="9fa27-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="9fa27-105">複数の書式を持つテキスト ファイルを解析するには</span><span class="sxs-lookup"><span data-stu-id="9fa27-105">To parse a text file with multiple formats</span></span>  
  
1.  <span data-ttu-id="9fa27-106">testfile.txt という名前のテキスト ファイルをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="9fa27-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="9fa27-107">次の内容をテキスト ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="9fa27-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  <span data-ttu-id="9fa27-108">予期される形式と、エラーが報告されたときに使用される形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="9fa27-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="9fa27-109">各配列の最後のエントリは -1 です。そのため、最後のフィールドは可変幅であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="9fa27-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="9fa27-110">これは、配列の最後のエントリが 0 以下の場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="9fa27-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  <span data-ttu-id="9fa27-111">新しい <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> オブジェクトを作成し、幅と形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="9fa27-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  <span data-ttu-id="9fa27-112">各行をループし、読み取り前に書式を調べます。</span><span class="sxs-lookup"><span data-stu-id="9fa27-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  <span data-ttu-id="9fa27-113">エラーをコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9fa27-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="9fa27-114">例</span><span class="sxs-lookup"><span data-stu-id="9fa27-114">Example</span></span>  
 <span data-ttu-id="9fa27-115">この例では、`testfile.txt` ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="9fa27-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9fa27-116">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9fa27-116">Robust Programming</span></span>  
 <span data-ttu-id="9fa27-117">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9fa27-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9fa27-118">指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="9fa27-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="9fa27-119">例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。</span><span class="sxs-lookup"><span data-stu-id="9fa27-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="9fa27-120">指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="9fa27-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="9fa27-121">部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。</span><span class="sxs-lookup"><span data-stu-id="9fa27-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="9fa27-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9fa27-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="9fa27-123">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="9fa27-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9fa27-124">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="9fa27-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa27-125">参照</span><span class="sxs-lookup"><span data-stu-id="9fa27-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [<span data-ttu-id="9fa27-126">方法: コンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9fa27-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="9fa27-127">方法: 固定幅のテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="9fa27-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="9fa27-128">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="9fa27-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
