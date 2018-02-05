---
title: "方法 : 新しく作成されたデータ ファイルに対して読み書きする"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 04ded71a23ba4cabab0a22e0d66c1084a726d8c8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="51824-102">方法 : 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="51824-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="51824-103"><xref:System.IO.BinaryWriter> クラスおよび <xref:System.IO.BinaryReader?displayProperty=nameWithType> クラスは、文字列ではない形式でデータを書き込んだり読み取ったりするために使用します。</span><span class="sxs-lookup"><span data-stu-id="51824-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="51824-104">`Test.data` と呼ばれる新しい空のファイル ストリームに対するデータの書き込みと読み取りを実行するコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="51824-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="51824-105">現在のディレクトリにデータ ファイルを作成した後、そのファイルに関連付けた <xref:System.IO.BinaryWriter> オブジェクトと <xref:System.IO.BinaryReader> オブジェクトを作成し、<xref:System.IO.BinaryWriter> オブジェクトを使用して整数 0 ～ 10 を `Test.data` に書き込みます。ファイル ポインターはファイルの末尾に残っています。</span><span class="sxs-lookup"><span data-stu-id="51824-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="51824-106"><xref:System.IO.BinaryReader> オブジェクトはファイル ポインターを起点に戻してから、指定された内容を読み出します。</span><span class="sxs-lookup"><span data-stu-id="51824-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51824-107">例</span><span class="sxs-lookup"><span data-stu-id="51824-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="51824-108">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="51824-108">Robust Programming</span></span>  
 <span data-ttu-id="51824-109">`Test.data` が既に現在のディレクトリに存在する場合は、<xref:System.IO.IOException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="51824-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="51824-110">ファイル ストリームを初期化するときにファイル モード オプション <xref:System.IO.FileMode.Create?displayProperty=nameWithType> を使用すると、例外がスローされずに新しいファイルが必ず作成されます。</span><span class="sxs-lookup"><span data-stu-id="51824-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51824-111">参照</span><span class="sxs-lookup"><span data-stu-id="51824-111">See Also</span></span>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [<span data-ttu-id="51824-112">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="51824-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="51824-113">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="51824-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="51824-114">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="51824-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="51824-115">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="51824-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="51824-116">方法: 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="51824-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="51824-117">方法: 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="51824-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="51824-118">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="51824-118">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
