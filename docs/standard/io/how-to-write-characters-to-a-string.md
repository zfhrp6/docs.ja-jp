---
title: "方法 : 文字列に文字を書き込む"
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
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d409b9f9cada319c64c4b5a1315b8a5abbd731e9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="99193-102">方法 : 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="99193-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="99193-103">次のコード例では、文字列の配列から同期および非同期的に文字が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="99193-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99193-104">例</span><span class="sxs-lookup"><span data-stu-id="99193-104">Example</span></span>  
 <span data-ttu-id="99193-105">次の例では、配列から文字列へ 5 文字が同期的に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="99193-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="99193-106">例</span><span class="sxs-lookup"><span data-stu-id="99193-106">Example</span></span>  
 <span data-ttu-id="99193-107">次の例では、<xref:System.Windows.Controls.TextBox> コントロールから非同期的にすべての文字を読み取り、配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="99193-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="99193-108">次に、<xref:System.Windows.Controls.TextBlock> コントロールへの改行が続く個別の行に、各文字または空白文字を非同期的に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="99193-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="99193-109">参照</span><span class="sxs-lookup"><span data-stu-id="99193-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="99193-110">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="99193-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="99193-111">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="99193-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="99193-112">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="99193-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="99193-113">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="99193-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="99193-114">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="99193-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="99193-115">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="99193-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="99193-116">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="99193-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="99193-117">方法: 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="99193-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
