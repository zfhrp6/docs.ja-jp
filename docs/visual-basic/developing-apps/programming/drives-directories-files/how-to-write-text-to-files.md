---
title: "方法: ファイルにテキストを書き込む (Visual Basic)"
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
- writing to files
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
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
ms.openlocfilehash: dc6f02d6092a30113b8cb973be225e140eca19ad
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="f6684-102">方法: ファイルにテキストを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6684-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="f6684-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを利用し、テキストをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f6684-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="f6684-104">指定したファイルが存在しない場合は、作成されます。</span><span class="sxs-lookup"><span data-stu-id="f6684-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="f6684-105">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f6684-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="f6684-106">テキストをファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="f6684-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="f6684-107">ファイルにテキストを書き込むには `WriteAllText` メソッドを使い、ファイルと書き込むテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="f6684-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="f6684-108">この例では、`test.txt` という名前のファイルに既に存在するテキストの最後に、`"This is new text."` という行を書き込んで追加します。</span><span class="sxs-lookup"><span data-stu-id="f6684-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     <span data-ttu-id="f6684-109">[!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6684-109">[!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]</span></span>  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="f6684-110">一連の文字列をファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="f6684-110">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="f6684-111">文字列のコレクションをループ処理します。</span><span class="sxs-lookup"><span data-stu-id="f6684-111">Loop through the string collection.</span></span> <span data-ttu-id="f6684-112">`WriteAllText` メソッドを使って、テキストをファイルに書き込みます。書き込むファイルと追加する文字列を指定し、`append` を `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f6684-112">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="f6684-113">この例では、`Documents and Settings` ディレクトリにあるファイルの名前を `FileList.txt` に書き込み、読みやすくするために各ファイル名の間に改行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f6684-113">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     <span data-ttu-id="f6684-114">[!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f6684-114">[!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6684-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f6684-115">Robust Programming</span></span>  
 <span data-ttu-id="f6684-116">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6684-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f6684-117">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="f6684-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f6684-118">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="f6684-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f6684-119">`File` が、存在しないパスを指している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="f6684-119">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f6684-120">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f6684-120">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f6684-121">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="f6684-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f6684-122">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="f6684-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="f6684-123">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="f6684-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="f6684-124">ディスクがいっぱいになっており、`WriteAllText` の呼び出しが失敗する (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f6684-124">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="f6684-125">部分的に信頼されているコンテキストで実行している場合は、特権不足のため例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="f6684-125">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="f6684-126">詳しくは、「[コード アクセス セキュリティの基礎](https://msdn.microsoft.com/library/33tceax8)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f6684-126">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6684-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6684-127">See Also</span></span>  
 <span data-ttu-id="f6684-128"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="f6684-128"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="f6684-129"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span><span class="sxs-lookup"><span data-stu-id="f6684-129"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A></span></span>   
 [<span data-ttu-id="f6684-130">方法: テキスト ファイルからデータを読み取る</span><span class="sxs-lookup"><span data-stu-id="f6684-130">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)

