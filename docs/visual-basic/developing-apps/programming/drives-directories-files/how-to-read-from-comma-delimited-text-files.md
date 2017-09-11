---
title: "方法: Visual Basic でコンマ区切りのテキスト ファイルを読み取る"
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
- files, parsing
- text files, tasks
- reading text files, comma-delimited
- text files, reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
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
ms.openlocfilehash: 2ae6a3f315a8e433386319d1aa1a7f48726a19bb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="a83d5-102">方法: Visual Basic でコンマ区切りのテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="a83d5-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="a83d5-103">`TextFieldParser` オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。</span><span class="sxs-lookup"><span data-stu-id="a83d5-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="a83d5-104">区切り形式のファイルか、固定幅フィールドのテキストを使用したファイルかは、`TextFieldType` プロパティで定義します。</span><span class="sxs-lookup"><span data-stu-id="a83d5-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="a83d5-105">コンマ区切りテキスト ファイルを解析するには</span><span class="sxs-lookup"><span data-stu-id="a83d5-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="a83d5-106">新規の `TextFieldParser` を作成します。</span><span class="sxs-lookup"><span data-stu-id="a83d5-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="a83d5-107">次のコードは、`MyReader` という名前の `TextFieldParser` を作成し、`test.txt` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a83d5-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     <span data-ttu-id="a83d5-108">[!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a83d5-108">[!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]</span></span>  
  
2.  <span data-ttu-id="a83d5-109">`TextField` 型と区切り記号を定義します。</span><span class="sxs-lookup"><span data-stu-id="a83d5-109">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="a83d5-110">次のコードは、`TextFieldType` プロパティを `Delimited`、区切り記号を "," として定義します。</span><span class="sxs-lookup"><span data-stu-id="a83d5-110">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     <span data-ttu-id="a83d5-111">[!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a83d5-111">[!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]</span></span>  
  
3.  <span data-ttu-id="a83d5-112">ファイル内のフィールドをループします。</span><span class="sxs-lookup"><span data-stu-id="a83d5-112">Loop through the fields in the file.</span></span> <span data-ttu-id="a83d5-113">破損している行が見つかった場合は、エラーを報告して解析を続行します。</span><span class="sxs-lookup"><span data-stu-id="a83d5-113">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="a83d5-114">次のコードは、ファイル内をループし、各フィールド順次表示して、不正にフォーマットされているフィールドをレポートします。</span><span class="sxs-lookup"><span data-stu-id="a83d5-114">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     <span data-ttu-id="a83d5-115">[!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a83d5-115">[!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]</span></span>  
  
4.  <span data-ttu-id="a83d5-116">`While` ブロックと `Using` ブロックをそれぞれ `End While` と `End Using` で閉じます。</span><span class="sxs-lookup"><span data-stu-id="a83d5-116">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     <span data-ttu-id="a83d5-117">[!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a83d5-117">[!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a83d5-118">例</span><span class="sxs-lookup"><span data-stu-id="a83d5-118">Example</span></span>  
 <span data-ttu-id="a83d5-119">次のコードは、`test.txt` ファイルから読み取りを行う例です。</span><span class="sxs-lookup"><span data-stu-id="a83d5-119">This example reads from the file `test.txt`.</span></span>  
  
 <span data-ttu-id="a83d5-120">[!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a83d5-120">[!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a83d5-121">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="a83d5-121">Robust programming</span></span>  
 <span data-ttu-id="a83d5-122">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a83d5-122">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a83d5-123">指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="a83d5-123">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="a83d5-124">例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。</span><span class="sxs-lookup"><span data-stu-id="a83d5-124">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="a83d5-125">指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="a83d5-125">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a83d5-126">部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。</span><span class="sxs-lookup"><span data-stu-id="a83d5-126">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="a83d5-127">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a83d5-127">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="a83d5-128">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="a83d5-128">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a83d5-129">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="a83d5-129">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a83d5-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a83d5-130">See also</span></span>  
 <span data-ttu-id="a83d5-131"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a83d5-131"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span></span>   
 <span data-ttu-id="a83d5-132">[方法: 固定幅のテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="a83d5-132">[How to: Read From Fixed-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md) </span></span>  
 <span data-ttu-id="a83d5-133">[方法: 複数の書式を持つテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="a83d5-133">[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
 <span data-ttu-id="a83d5-134">[TextFieldParser オブジェクトによるテキスト ファイルの解析](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span><span class="sxs-lookup"><span data-stu-id="a83d5-134">[Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span></span>  
 <span data-ttu-id="a83d5-135">[チュートリアル: Visual Basic によるファイルとディレクトリの操作](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="a83d5-135">[Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
 [<span data-ttu-id="a83d5-136">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="a83d5-136">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)

