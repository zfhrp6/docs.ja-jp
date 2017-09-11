---
title: "方法: Visual Basic で固定幅のテキスト ファイルを読み取る"
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
- fixed-width text file
- reading text files, fixed-width
- files, parsing
- text files, tasks
- text files, reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
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
ms.openlocfilehash: fc45c6d6e4301b2786fefe947ed011ca95f8a79c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="da3da-102">方法: Visual Basic で固定幅のテキスト ファイルを読み取る</span><span class="sxs-lookup"><span data-stu-id="da3da-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="da3da-103">`TextFieldParser` オブジェクトには、構造化されたテキスト ファイル (ログなど) を簡単にかつ効率的に解析する方法が備わっています。</span><span class="sxs-lookup"><span data-stu-id="da3da-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="da3da-104">解析対象のファイルが区切り形式であるか固定幅フィールドであるかは、`TextFieldType` プロパティで定義します。</span><span class="sxs-lookup"><span data-stu-id="da3da-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="da3da-105">固定幅のテキスト ファイルでは、最終フィールドを可変幅とすることができます。</span><span class="sxs-lookup"><span data-stu-id="da3da-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="da3da-106">最後のフィールドを可変幅として指定するには、その幅に 0 以下の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="da3da-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="da3da-107">固定幅のテキスト ファイルを解析するには</span><span class="sxs-lookup"><span data-stu-id="da3da-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="da3da-108">新しい `TextFieldParser` を作成します。</span><span class="sxs-lookup"><span data-stu-id="da3da-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="da3da-109">次のコードで `Reader` という名前の `TextFieldParser` を作成し、`test.log` ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="da3da-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     <span data-ttu-id="da3da-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="da3da-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span></span>  
  
2.  <span data-ttu-id="da3da-111">`TextFieldType` プロパティを `FixedWidth` として定義し、幅と形式を定義します。</span><span class="sxs-lookup"><span data-stu-id="da3da-111">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="da3da-112">次のコードでは、テキストの列を定義しています。先頭列の幅が 5 文字、2 列目が 10 文字、3 列目が 11 文字、そして 4 列目が可変幅です。</span><span class="sxs-lookup"><span data-stu-id="da3da-112">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     <span data-ttu-id="da3da-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="da3da-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span></span>  
  
3.  <span data-ttu-id="da3da-114">ファイル内のフィールドをループします。</span><span class="sxs-lookup"><span data-stu-id="da3da-114">Loop through the fields in the file.</span></span> <span data-ttu-id="da3da-115">破損している行が見つかった場合は、エラーを報告して解析を続行します。</span><span class="sxs-lookup"><span data-stu-id="da3da-115">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     <span data-ttu-id="da3da-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="da3da-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span></span>  
  
4.  <span data-ttu-id="da3da-117">`While` ブロックと `Using` ブロックをそれぞれ `End While` と `End Using` で閉じます。</span><span class="sxs-lookup"><span data-stu-id="da3da-117">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     <span data-ttu-id="da3da-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="da3da-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="da3da-119">例</span><span class="sxs-lookup"><span data-stu-id="da3da-119">Example</span></span>  
 <span data-ttu-id="da3da-120">次のコードは、`test.log` ファイルから読み取りを行う例です。</span><span class="sxs-lookup"><span data-stu-id="da3da-120">This example reads from the file `test.log`.</span></span>  
  
 <span data-ttu-id="da3da-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="da3da-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="da3da-122">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="da3da-122">Robust programming</span></span>  
 <span data-ttu-id="da3da-123">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="da3da-123">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="da3da-124">指定された形式で行を解析できない (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="da3da-124">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="da3da-125">例外の原因となった行が例外メッセージで報告され、その行に含まれているテキストには <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> プロパティが代入されます。</span><span class="sxs-lookup"><span data-stu-id="da3da-125">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="da3da-126">指定されたファイルが存在しない (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="da3da-126">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="da3da-127">部分信頼の状況下で、ファイルにアクセスするために必要なアクセス許可がユーザーにない。</span><span class="sxs-lookup"><span data-stu-id="da3da-127">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="da3da-128">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="da3da-128">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="da3da-129">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="da3da-129">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="da3da-130">ファイルにアクセスする十分なアクセス許可がユーザーにない (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="da3da-130">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3da-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="da3da-131">See also</span></span>  
 <span data-ttu-id="da3da-132"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="da3da-132"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName></span></span>   
 <span data-ttu-id="da3da-133">[方法: コンマ区切りのテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="da3da-133">[How to: Read From Comma-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span></span>  
 <span data-ttu-id="da3da-134">[方法: 複数の書式を持つテキスト ファイルを読み取る](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="da3da-134">[How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
 <span data-ttu-id="da3da-135">[TextFieldParser オブジェクトによるテキスト ファイルの解析](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span><span class="sxs-lookup"><span data-stu-id="da3da-135">[Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span></span>  
 <span data-ttu-id="da3da-136">[チュートリアル: Visual Basic によるファイルとディレクトリの操作](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="da3da-136">[Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
 [<span data-ttu-id="da3da-137">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="da3da-137">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 

