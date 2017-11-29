---
title: "非同期ファイル I-O"
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
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d8a461d79ecdcadc3f880f6a813918cf891abd45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="8fcb0-102">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="8fcb0-102">Asynchronous File I/O</span></span>
<span data-ttu-id="8fcb0-103">非同期操作では、メイン スレッドをブロックすることなくリソース使用量の多い I/O 操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="8fcb0-104">このパフォーマンスに関する考慮事項は、時間のかかるストリーム操作によって UI スレッドがブロックされ、アプリが動作していないと見なされる可能性がある [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリまたは [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] アプリで特に重要です。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-104">This performance consideration is particularly important in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app or [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>  
  
 <span data-ttu-id="8fcb0-105">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]以降の I/O 型には非同期操作を単純化する非同期メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-105">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="8fcb0-106">非同期のメソッドの名前には `Async` が含まれます ( <xref:System.IO.Stream.ReadAsync%2A>、 <xref:System.IO.Stream.WriteAsync%2A>、 <xref:System.IO.Stream.CopyToAsync%2A>、 <xref:System.IO.Stream.FlushAsync%2A>、 <xref:System.IO.TextReader.ReadLineAsync%2A>、 <xref:System.IO.TextReader.ReadToEndAsync%2A>など)。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="8fcb0-107">これらの非同期のメソッドは、 <xref:System.IO.Stream>、 <xref:System.IO.FileStream>、 <xref:System.IO.MemoryStream>などのストリーム クラスと、 <xref:System.IO.TextReader> 、 <xref:System.IO.TextWriter>などのストリームとの間の読み取り/書き込みに使用されるクラスに実装されます。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>  
  
 <span data-ttu-id="8fcb0-108">.NET Framework 4 およびそれ以前のバージョンで非同期 I/O 操作を実装するには、 <xref:System.IO.Stream.BeginRead%2A> 、 <xref:System.IO.Stream.EndRead%2A> などのメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="8fcb0-109">これらのメソッドは、レガシ コードをサポートするために [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] でも使用できますが、非同期 I/O 操作は非同期のメソッドを使用して実装する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-109">These methods are still available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>  
  
 <span data-ttu-id="8fcb0-110">[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]以降、Visual Studio には非同期プログラミング向けの 2 つのキーワードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-110">Starting with [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], Visual Studio provides two keywords for asynchronous programming:</span></span>  
  
 <span data-ttu-id="8fcb0-111">`Async` (Visual Basic) 修飾子または `async` (C#) 修飾子。非同期操作を含むメソッドをマークするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>  
  
 <span data-ttu-id="8fcb0-112">`Await` (Visual Basic) 演算子または `await` (C#) 演算子。非同期のメソッドの結果に適用されます。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>  
  
 <span data-ttu-id="8fcb0-113">非同期 I/O 操作を実装するには、これらのキーワードを非同期のメソッドと組み合わせて使用します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="8fcb0-114">詳細については、「[Async および Await を使用した非同期プログラミング](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-114">For more information, see [Asynchronous Programming with Async and Await](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).</span></span>  
  
 <span data-ttu-id="8fcb0-115">次の例では、2 つの <xref:System.IO.FileStream> オブジェクトを使用して、ファイルをディレクトリ間で非同期にコピーする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="8fcb0-116">非同期のメソッドを呼び出すので、 <xref:System.Web.UI.WebControls.Button.Click> コントロールの <xref:System.Windows.Controls.Button> イベント ハンドラーは `async` 修飾子でマークされていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 <span data-ttu-id="8fcb0-117">次の例は前述の例と似ていますが、 <xref:System.IO.StreamReader> オブジェクトと <xref:System.IO.StreamWriter> オブジェクトを使用して、テキスト ファイルの内容の読み取り/書き込みを非同期で行います。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 <span data-ttu-id="8fcb0-118">次の例では、分離コード ファイルと XAML ファイルを使用して <xref:System.IO.Stream> アプリでファイルを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] として開き、 <xref:System.IO.StreamReader> クラスのインスタンスを使用してその内容を読み取る方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="8fcb0-119">ここでは、非同期のメソッドを使用して、ファイルをストリームとして開き、ファイルの内容を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="8fcb0-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8fcb0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fcb0-120">See Also</span></span>  
 <xref:System.IO.Stream>  
 [<span data-ttu-id="8fcb0-121">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="8fcb0-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="8fcb0-122">Async および Await を使用した非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="8fcb0-122">Asynchronous Programming with Async and Await</span></span>](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
