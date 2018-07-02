---
title: '方法 : ファイルからテキストを読み取る'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7c54e5e55770f3df44819cdf6d2d2c866f7e0fc
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298163"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="a774c-102">方法 : ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="a774c-102">How to: Read Text from a File</span></span>
<span data-ttu-id="a774c-103">次に、.NET デスクトップ アプリを使用してテキスト ファイルから同期でテキストを読み取る方法と非同期でテキストを読み取る方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a774c-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="a774c-104">どちらの例でも、<xref:System.IO.StreamReader> クラスのインスタンスを作成する場合に、ファイルの相対パスまたは絶対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a774c-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="a774c-105">次の例では、TestFile.txt という名前のファイルがアプリケーションと同じフォルダーにあることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="a774c-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="a774c-106">Windows ランタイムではファイルに対する読み取りと書き込みに別のストリーム型が用意されているため、これらのコード例は Windows ストア アプリの開発には適用されません。</span><span class="sxs-lookup"><span data-stu-id="a774c-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="a774c-107">Windows ストア アプリのファイルからテキストを読み取る方法を示す例については、「[Quickstart: Reading and writing files](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10))」 (クイック スタート: ファイルの読み取りと書き込み) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a774c-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/en-us/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="a774c-108">.NET Framework ストリームと Windows ランタイム ストリームを変換する方法を示す例は、「[方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a774c-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a774c-109">例</span><span class="sxs-lookup"><span data-stu-id="a774c-109">Example</span></span>  
 <span data-ttu-id="a774c-110">次の例では、コンソール アプリケーション内での同期読み取り操作を示します。</span><span class="sxs-lookup"><span data-stu-id="a774c-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="a774c-111">この例では、ストリーム リーダーを使用してテキスト ファイルを開き、内容を文字列にコピーして、文字列をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="a774c-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="a774c-112">例</span><span class="sxs-lookup"><span data-stu-id="a774c-112">Example</span></span>  
 <span data-ttu-id="a774c-113">次の例では、Windows Presentation Foundation (WPF) アプリケーション内での非同期読み取り操作を示します。</span><span class="sxs-lookup"><span data-stu-id="a774c-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a774c-114">参照</span><span class="sxs-lookup"><span data-stu-id="a774c-114">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a774c-115">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="a774c-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="a774c-116">NIB: 方法: ディレクトリ一覧を作成する</span><span class="sxs-lookup"><span data-stu-id="a774c-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="a774c-117">クイック スタート: ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="a774c-117">Quickstart: Reading and writing files</span></span>](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [<span data-ttu-id="a774c-118">方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う</span><span class="sxs-lookup"><span data-stu-id="a774c-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [<span data-ttu-id="a774c-119">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="a774c-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="a774c-120">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="a774c-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="a774c-121">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="a774c-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="a774c-122">方法: 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="a774c-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="a774c-123">方法: 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="a774c-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="a774c-124">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="a774c-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
