---
title: "方法 : ログ ファイルを開いて情報を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="0e931-102">方法 : ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="0e931-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="0e931-103"><xref:System.IO.StreamWriter>および<xref:System.IO.StreamReader>する文字の書き込みおよびストリームから文字を読み取る。</span><span class="sxs-lookup"><span data-stu-id="0e931-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="0e931-104">次のコード例が開き、`log.txt`入力には、ファイルまたはファイルの末尾に情報を追加し、既に存在しない場合は、ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e931-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="0e931-105">ファイルの内容は表示するための標準出力に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="0e931-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="0e931-106">この例を代わりに、情報を 1 つの文字列または文字列の配列として格納でした、<xref:System.IO.File.WriteAllText%2A>または<xref:System.IO.File.WriteAllLines%2A>メソッドは、同じ機能を実現するを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0e931-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e931-107">メソッドおよびプロパティを使用する Visual Basic ユーザーは選択、<xref:Microsoft.VisualBasic.Logging.Log>クラスまたは<xref:Microsoft.VisualBasic.FileIO.FileSystem>作成またはログ ファイルに書き込むのためのクラスです。</span><span class="sxs-lookup"><span data-stu-id="0e931-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e931-108">例</span><span class="sxs-lookup"><span data-stu-id="0e931-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0e931-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e931-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="0e931-110">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="0e931-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="0e931-111">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="0e931-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="0e931-112">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="0e931-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="0e931-113">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="0e931-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="0e931-114">方法: 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="0e931-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="0e931-115">方法: 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="0e931-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="0e931-116">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="0e931-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
