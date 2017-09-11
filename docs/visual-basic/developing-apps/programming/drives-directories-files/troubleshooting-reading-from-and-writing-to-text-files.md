---
title: "トラブルシューティング: テキスト ファイルの読み取りと書き込み (Visual Basic)"
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
- troubleshooting file I/O
- writing text to files, troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files, troubleshooting
- reading text files, troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
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
ms.openlocfilehash: 7f1d26df53445ee9711ebb2840071d2560c5380d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="419b0-102">トラブルシューティング: テキスト ファイルの読み取りと書き込み (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="419b0-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="419b0-103">このトピックでは、テキスト ファイルを使用するときに発生する一般的な問題について説明し、それぞれの対処方法を示します。</span><span class="sxs-lookup"><span data-stu-id="419b0-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="419b0-104">一般的な問題</span><span class="sxs-lookup"><span data-stu-id="419b0-104">Common problems</span></span>  
 <span data-ttu-id="419b0-105">テキスト ファイルを使用するときに特によく発生する問題として、セキュリティ例外、ファイル エンコーディング、無効なパスがあります。</span><span class="sxs-lookup"><span data-stu-id="419b0-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="419b0-106">セキュリティ例外</span><span class="sxs-lookup"><span data-stu-id="419b0-106">Security exceptions</span></span>  
 <span data-ttu-id="419b0-107">セキュリティ エラーが発生した場合、<xref:System.Security.SecurityException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="419b0-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="419b0-108">この問題は、多くの場合、ユーザーに必要なアクセス許可がないことが原因で発生するため、アクセス許可を追加するか、分離ストレージでファイルを操作することで解決できます。</span><span class="sxs-lookup"><span data-stu-id="419b0-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="419b0-109">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="419b0-109">File encodings</span></span>  
 <span data-ttu-id="419b0-110">ファイル エンコーディングは、文字エンコーディングとも呼ばれ、テキストを処理するときの文字の表現方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="419b0-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="419b0-111">エンコーディングが誤っていると、テキスト ファイルに予期しない文字が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="419b0-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="419b0-112">ほとんどのファイルで、言語で処理できる (または処理できない) 文字という観点から、あるエンコードが他のエンコーディングよりも望ましいということがありますが、一般的には Unicode が好まれます。</span><span class="sxs-lookup"><span data-stu-id="419b0-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="419b0-113">詳細については、[ファイル エンコーディング](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) および <xref:System.Text.Encoding> に関する各記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="419b0-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="419b0-114">無効なパス</span><span class="sxs-lookup"><span data-stu-id="419b0-114">Incorrect paths</span></span>  
 <span data-ttu-id="419b0-115">ファイル パス (特に相対パス) を解析するときに、間違ったデータを指定してしまうことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="419b0-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="419b0-116">正しいパスを指定しているかどうかを確認することで、問題の多くを解決できます。</span><span class="sxs-lookup"><span data-stu-id="419b0-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="419b0-117">詳細については、「[方法: ファイル パスを解析する](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="419b0-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419b0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="419b0-118">See also</span></span>  
 <span data-ttu-id="419b0-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="419b0-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="419b0-120">[ファイルの読み取り](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span><span class="sxs-lookup"><span data-stu-id="419b0-120">[Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md) </span></span>  
 <span data-ttu-id="419b0-121">[ファイルへの書き込み](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span><span class="sxs-lookup"><span data-stu-id="419b0-121">[Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md) </span></span>  
 [<span data-ttu-id="419b0-122">TextFieldParser オブジェクトによるテキスト ファイルの解析</span><span class="sxs-lookup"><span data-stu-id="419b0-122">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)

