---
title: '方法 : 文字列から文字を読み取る'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4023d8e801da542414aac1fddaf7aef5bf1e98f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="f712f-102">方法 : 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="f712f-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="f712f-103">次のコード例は、文字列から同期で文字を読み取る方法と非同期で文字を読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f712f-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f712f-104">例</span><span class="sxs-lookup"><span data-stu-id="f712f-104">Example</span></span>  
 <span data-ttu-id="f712f-105">この例では、文字列から同期的に 13 文字を読み取り、配列に格納し、これらの文字を表示します。</span><span class="sxs-lookup"><span data-stu-id="f712f-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="f712f-106">次に、文字列の残りの文字を読み取り、6 番目の要素で始まる配列に格納し、配列の内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="f712f-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="f712f-107">例</span><span class="sxs-lookup"><span data-stu-id="f712f-107">Example</span></span>  
 <span data-ttu-id="f712f-108">次の例では、<xref:System.Windows.Controls.TextBox> コントロールから非同期的にすべての文字を読み取り、配列に格納します。</span><span class="sxs-lookup"><span data-stu-id="f712f-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="f712f-109">次に、<xref:System.Windows.Controls.TextBlock> コントロールへの改行が続く個別の行に、各文字または空白文字を非同期的に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f712f-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f712f-110">参照</span><span class="sxs-lookup"><span data-stu-id="f712f-110">See Also</span></span>  
 <xref:System.IO.StringReader>  
 <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f712f-111">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="f712f-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="f712f-112">NIB: 方法: ディレクトリ一覧を作成する</span><span class="sxs-lookup"><span data-stu-id="f712f-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="f712f-113">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="f712f-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="f712f-114">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="f712f-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="f712f-115">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="f712f-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="f712f-116">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="f712f-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="f712f-117">方法: 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="f712f-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="f712f-118">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="f712f-118">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
