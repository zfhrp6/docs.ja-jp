---
title: "方法: ファイルにテキストを書き込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fbbe0ec007911460dc2bda8c681775da9a6cb91
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="9e826-102">方法: ファイルにテキストを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e826-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="9e826-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> メソッドを利用し、テキストをファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9e826-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="9e826-104">指定したファイルが存在しない場合は、作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e826-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="9e826-105">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="9e826-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="9e826-106">テキストをファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="9e826-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="9e826-107">ファイルにテキストを書き込むには `WriteAllText` メソッドを使い、ファイルと書き込むテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e826-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="9e826-108">この例では、`test.txt` という名前のファイルに既に存在するテキストの最後に、`"This is new text."` という行を書き込んで追加します。</span><span class="sxs-lookup"><span data-stu-id="9e826-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="9e826-109">一連の文字列をファイルに書き込むには</span><span class="sxs-lookup"><span data-stu-id="9e826-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="9e826-110">文字列のコレクションをループ処理します。</span><span class="sxs-lookup"><span data-stu-id="9e826-110">Loop through the string collection.</span></span> <span data-ttu-id="9e826-111">`WriteAllText` メソッドを使って、テキストをファイルに書き込みます。書き込むファイルと追加する文字列を指定し、`append` を `True` に設定します。</span><span class="sxs-lookup"><span data-stu-id="9e826-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="9e826-112">この例では、`Documents and Settings` ディレクトリにあるファイルの名前を `FileList.txt` に書き込み、読みやすくするために各ファイル名の間に改行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="9e826-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9e826-113">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9e826-113">Robust Programming</span></span>  
 <span data-ttu-id="9e826-114">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9e826-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9e826-115">パスが正しくない。長さが 0 の文字列である、空白だけが含まれている、使用できない文字が含まれている、デバイス パスである (先頭が \\\\.\\)、のいずれかの理由が考えられる (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="9e826-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="9e826-116">パスが `Nothing` であるため、有効でない (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="9e826-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9e826-117">`File` が、存在しないパスを指している (<xref:System.IO.FileNotFoundException> または <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="9e826-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="9e826-118">他のプロセスがファイルを使用しているか、または I/O エラーが発生した (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="9e826-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="9e826-119">パスがシステムで定義されている最大長を超えている (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="9e826-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9e826-120">パス内のファイル名またはディレクトリ名にコロン (:) が含まれているか、または形式が無効である (<xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="9e826-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="9e826-121">ユーザーがパスを参照するのに必要なアクセス許可がない (<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="9e826-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="9e826-122">ディスクがいっぱいになっており、`WriteAllText` の呼び出しが失敗する (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="9e826-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="9e826-123">部分的に信頼されているコンテキストで実行している場合は、特権不足のため例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="9e826-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="9e826-124">詳しくは、「[コード アクセス セキュリティの基礎](../../../../framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9e826-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e826-125">参照</span><span class="sxs-lookup"><span data-stu-id="9e826-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [<span data-ttu-id="9e826-126">方法: テキスト ファイルからデータを読み取る</span><span class="sxs-lookup"><span data-stu-id="9e826-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
