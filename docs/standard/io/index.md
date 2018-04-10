---
title: ファイルおよびストリーム入出力
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
caps.latest.revision: 33
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9ebd1a11684afaa143d1f016f31e0a29a3478db
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="file-and-stream-io"></a><span data-ttu-id="24bb7-102">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="24bb7-102">File and Stream I/O</span></span>
<span data-ttu-id="24bb7-103">ファイルおよびストリーム I/O (入出力) とは、ストレージ メディアとの間のデータの転送を指します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-103">File and stream I/O (input/output) refers to the transfer of data either to or from a storage medium.</span></span> <span data-ttu-id="24bb7-104">.NET Framework では、`System.IO` 名前空間に、データ ストリームおよびファイルで同期的および非同期的に読み取りと書き込みを有効にする型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="24bb7-104">In the .NET Framework, the `System.IO` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files.</span></span> <span data-ttu-id="24bb7-105">これらの名前空間には、ファイルを圧縮および圧縮解除する型、パイプとシリアル ポート経由の通信を有効にする型もあります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-105">These namespaces also contain types that perform compression and decompression on files, and types that enable communication through pipes and serial ports.</span></span>  
  
 <span data-ttu-id="24bb7-106">ファイルとは、バイトを順序立てて格納する名前付きのコレクションであり、永続ストレージを保有します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-106">A file is an ordered and named collection of bytes that has persistent storage.</span></span> <span data-ttu-id="24bb7-107">ファイルを操作するときには、ディレクトリ パス、ディスク ストレージ、ファイル名、ディレクトリ名を操作します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-107">When you work with files, you work with directory paths, disk storage, and file and directory names.</span></span> <span data-ttu-id="24bb7-108">これに対し、ストリームは、バッキング ストアの読み取りと書き込みに使用できるバイトのシーケンスです。バッキング ストアは、複数のストレージ メディアのいずれかになります (たとえば、ディスク、メモリ)。</span><span class="sxs-lookup"><span data-stu-id="24bb7-108">In contrast, a stream is a sequence of bytes that you can use to read from and write to a backing store, which can be one of several storage mediums (for example, disks or memory).</span></span> <span data-ttu-id="24bb7-109">ディスク以外にいくつかのバッキング ストアが存在するのと同じように、ファイル ストリーム以外にも、ネットワーク ストリーム、メモリ ストリーム、パイプ ストリームなど、さまざまなストリームが存在します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-109">Just as there are several backing stores other than disks, there are several kinds of streams other than file streams, such as network, memory, and pipe streams.</span></span>  
  
## <a name="files-and-directories"></a><span data-ttu-id="24bb7-110">ファイルとディレクトリ</span><span class="sxs-lookup"><span data-stu-id="24bb7-110">Files and Directories</span></span>  
 <span data-ttu-id="24bb7-111"><xref:System.IO?displayProperty=nameWithType> 名前空間の型を使用して、ファイルとディレクトリを操作できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-111">You can use the types in the <xref:System.IO?displayProperty=nameWithType> namespace to interact with files and directories.</span></span> <span data-ttu-id="24bb7-112">たとえば、ファイルとディレクトリに対するプロパティを取得および設定したり、検索条件に基づいて、ファイルとディレクトリのコレクションを取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-112">For example, you can get and set properties for files and directories, and retrieve collections of files and directories based on search criteria.</span></span>  
  
 <span data-ttu-id="24bb7-113">一般的なファイルおよびディレクトリのクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-113">Here are some commonly used file and directory classes:</span></span>  
  
-   <span data-ttu-id="24bb7-114"><xref:System.IO.File> - ファイルを作成、コピー、削除、移動、およびオープンするための静的メソッドを提供し、<xref:System.IO.FileStream> オブジェクトの作成を支援します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-114"><xref:System.IO.File> - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>  
  
-   <span data-ttu-id="24bb7-115"><xref:System.IO.FileInfo> - ファイルを作成、コピー、削除、移動、およびオープンするためのインスタンス メソッドを提供し、<xref:System.IO.FileStream> オブジェクトの作成を支援します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-115"><xref:System.IO.FileInfo> - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>  
  
-   <span data-ttu-id="24bb7-116"><xref:System.IO.Directory> - ディレクトリやサブディレクトリを作成、移動、および反復処理するための静的メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-116"><xref:System.IO.Directory> - provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>  
  
-   <span data-ttu-id="24bb7-117"><xref:System.IO.DirectoryInfo> - ディレクトリやサブディレクトリを作成、移動、および反復処理するためのインスタンス メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-117"><xref:System.IO.DirectoryInfo> - provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>  
  
-   <span data-ttu-id="24bb7-118"><xref:System.IO.Path> - 複数のプラットフォームにまたがってディレクトリ文字列を処理するためのメソッドおよびプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-118"><xref:System.IO.Path> - provides methods and properties for processing directory strings in a cross-platform manner.</span></span>  
  
 <span data-ttu-id="24bb7-119">これらのクラスに加えて、Visual Basic のユーザーは、ファイル I/O 用の <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> クラスに用意されているメソッドとプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-119">In addition to using these classes, Visual Basic users can use the methods and properties provided by the <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> class for file I/O.</span></span>  
  
 <span data-ttu-id="24bb7-120">「[方法: ディレクトリをコピーする](../../../docs/standard/io/how-to-copy-directories.md)」、「[方法: ディレクトリ リストを作成する](http://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)」、および「[方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-120">See [How to: Copy Directories](../../../docs/standard/io/how-to-copy-directories.md), [How to: Create a Directory Listing](http://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), and [How to: Enumerate Directories and Files](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).</span></span>  
  
## <a name="streams"></a><span data-ttu-id="24bb7-121">ストリーム</span><span class="sxs-lookup"><span data-stu-id="24bb7-121">Streams</span></span>  
 <span data-ttu-id="24bb7-122">抽象基底クラス <xref:System.IO.Stream> は、バイトの読み取りと書き込みをサポートします。</span><span class="sxs-lookup"><span data-stu-id="24bb7-122">The abstract base class <xref:System.IO.Stream> supports reading and writing bytes.</span></span> <span data-ttu-id="24bb7-123">ストリームを表すすべてのクラスは、<xref:System.IO.Stream> クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-123">All classes that represent streams inherit from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="24bb7-124"><xref:System.IO.Stream> クラスとその派生クラスは、データ ソースやリポジトリの共通ビューを提供し、プログラマがオペレーティング システムや基になるデバイスに固有の詳細事項を考慮する必要をなくします。</span><span class="sxs-lookup"><span data-stu-id="24bb7-124">The <xref:System.IO.Stream> class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.</span></span>  
  
 <span data-ttu-id="24bb7-125">ストリームには次の 3 つの基本的な操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-125">Streams involve three fundamental operations:</span></span>  
  
-   <span data-ttu-id="24bb7-126">読み取り - ストリームからバイト配列などのデータ構造体にデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-126">Reading - transferring data from a stream into a data structure, such as an array of bytes.</span></span>  
  
-   <span data-ttu-id="24bb7-127">書き込み - データ ソースからストリームにデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-127">Writing - transferring data to a stream from a data source.</span></span>  
  
-   <span data-ttu-id="24bb7-128">シーク - ストリーム内の現在位置を照会および変更します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-128">Seeking - querying and modifying the current position within a stream.</span></span>  
  
 <span data-ttu-id="24bb7-129">基になるデータ ソースまたはリポジトリによっては、ストリームがサポートできる機能が上記の一部に限られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-129">Depending on the underlying data source or repository, a stream might support only some of these capabilities.</span></span> <span data-ttu-id="24bb7-130">たとえば、<xref:System.IO.Pipes.PipeStream> クラスは、シークをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="24bb7-130">For example, the <xref:System.IO.Pipes.PipeStream> class does not support seeking.</span></span> <span data-ttu-id="24bb7-131">ストリームの <xref:System.IO.Stream.CanRead%2A>、<xref:System.IO.Stream.CanWrite%2A>、および <xref:System.IO.Stream.CanSeek%2A> の各プロパティで、そのストリームがサポートする操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-131">The <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, and <xref:System.IO.Stream.CanSeek%2A> properties of a stream specify the operations that the stream supports.</span></span>  
  
 <span data-ttu-id="24bb7-132">一般的なストリーム クラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-132">Here are some commonly used stream classes:</span></span>  
  
-   <span data-ttu-id="24bb7-133"><xref:System.IO.FileStream> – ファイルの読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-133"><xref:System.IO.FileStream> – for reading and writing to a file.</span></span>  
  
-   <span data-ttu-id="24bb7-134"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 分離ストレージのファイルの読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-134"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – for reading and writing to a file in isolated storage.</span></span>  
  
-   <span data-ttu-id="24bb7-135"><xref:System.IO.MemoryStream> – バッキング ストアとしてメモリの読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-135"><xref:System.IO.MemoryStream> – for reading and writing to memory as the backing store.</span></span>  
  
-   <span data-ttu-id="24bb7-136"><xref:System.IO.BufferedStream> – 読み取り操作と書き込み操作のパフォーマンスを向上します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-136"><xref:System.IO.BufferedStream> – for improving performance of read and write operations.</span></span>  
  
-   <span data-ttu-id="24bb7-137"><xref:System.Net.Sockets.NetworkStream> – ネットワーク ソケットを介して読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-137"><xref:System.Net.Sockets.NetworkStream> – for reading and writing over network sockets.</span></span>  
  
-   <span data-ttu-id="24bb7-138"><xref:System.IO.Pipes.PipeStream> – 匿名パイプと名前付きパイプを介して読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-138"><xref:System.IO.Pipes.PipeStream> – for reading and writing over anonymous and named pipes.</span></span>  
  
-   <span data-ttu-id="24bb7-139"><xref:System.Security.Cryptography.CryptoStream> – データ ストリームを暗号変換にリンクします。</span><span class="sxs-lookup"><span data-stu-id="24bb7-139"><xref:System.Security.Cryptography.CryptoStream> – for linking data streams to cryptographic transformations.</span></span>  
  
 <span data-ttu-id="24bb7-140">ストリームを非同期的に操作する例については、「[非同期ファイル I/O](../../../docs/standard/io/asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-140">For an example of working with streams asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="readers-and-writers"></a><span data-ttu-id="24bb7-141">リーダーとライター</span><span class="sxs-lookup"><span data-stu-id="24bb7-141">Readers and Writers</span></span>  
 <span data-ttu-id="24bb7-142"><xref:System.IO?displayProperty=nameWithType> 名前空間には、ストリームからエンコードされた文字を読み取ったり、ストリームに書き込んだりするための型も用意されています。</span><span class="sxs-lookup"><span data-stu-id="24bb7-142">The <xref:System.IO?displayProperty=nameWithType> namespace also provides types for reading encoded characters from streams and writing them to streams.</span></span> <span data-ttu-id="24bb7-143">通常、ストリームはバイトの入出力用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="24bb7-143">Typically, streams are designed for byte input and output.</span></span> <span data-ttu-id="24bb7-144">リーダー型とライター型は、ストリームが操作を完了できるように、バイトとの間でエンコードされた文字の変換を処理します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-144">The reader and writer types handle the conversion of the encoded characters to and from bytes so the stream can complete the operation.</span></span> <span data-ttu-id="24bb7-145">各リーダー クラスとライター クラスは、クラスの `BaseStream` プロパティから取得できるストリームに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-145">Each reader and writer class is associated with a stream, which can be retrieved through the class's `BaseStream` property.</span></span>  
  
 <span data-ttu-id="24bb7-146">一般的なリーダー クラスとライター クラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-146">Here are some commonly used reader and writer classes:</span></span>  
  
-   <span data-ttu-id="24bb7-147"><xref:System.IO.BinaryReader> および <xref:System.IO.BinaryWriter> – バイナリ値としてプリミティブ データ型の読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-147"><xref:System.IO.BinaryReader> and <xref:System.IO.BinaryWriter> – for reading and writing primitive data types as binary values.</span></span>  
  
-   <span data-ttu-id="24bb7-148"><xref:System.IO.StreamReader> および <xref:System.IO.StreamWriter> – 文字とバイトを相互変換するエンコーディング値を使用して、文字の読み取りと書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-148"><xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> – for reading and writing characters by using an encoding value to convert the characters to and from bytes.</span></span>  
  
-   <span data-ttu-id="24bb7-149"><xref:System.IO.StringReader> および <xref:System.IO.StringWriter> – 文字列から文字を読み取り、文字列に文字を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-149"><xref:System.IO.StringReader> and <xref:System.IO.StringWriter> – for reading and writing characters to and from strings.</span></span>  
  
-   <span data-ttu-id="24bb7-150"><xref:System.IO.TextReader> および <xref:System.IO.TextWriter> – バイナリ データを除く、文字と文字列の読み取りと書き込みを行う他のリーダーとライターの抽象基底クラスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-150"><xref:System.IO.TextReader> and <xref:System.IO.TextWriter> – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.</span></span>  
  
 <span data-ttu-id="24bb7-151">「[方法: ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)」、「[方法: ファイルにテキストを書き込む](../../../docs/standard/io/how-to-write-text-to-a-file.md)」、「[方法: 文字列から文字を読み取る](../../../docs/standard/io/how-to-read-characters-from-a-string.md)」、および「[方法: 文字列に文字を書き込む](../../../docs/standard/io/how-to-write-characters-to-a-string.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-151">See [How to: Read Text from a File](../../../docs/standard/io/how-to-read-text-from-a-file.md), [How to: Write Text to a File](../../../docs/standard/io/how-to-write-text-to-a-file.md), [How to: Read Characters from a String](../../../docs/standard/io/how-to-read-characters-from-a-string.md), and [How to: Write Characters to a String](../../../docs/standard/io/how-to-write-characters-to-a-string.md).</span></span>  
  
## <a name="asynchronous-io-operations"></a><span data-ttu-id="24bb7-152">非同期 I/O 操作</span><span class="sxs-lookup"><span data-stu-id="24bb7-152">Asynchronous I/O Operations</span></span>  
 <span data-ttu-id="24bb7-153">大量のデータを読み取ったり書き込んだりすると、リソースが大量に消費されることがあります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-153">Reading or writing a large amount of data can be resource-intensive.</span></span> <span data-ttu-id="24bb7-154">アプリケーションのユーザーに対する応答性を維持する必要がある場合は、これらのタスクを非同期的に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-154">You should perform these tasks asynchronously if your application needs to remain responsive to the user.</span></span> <span data-ttu-id="24bb7-155">同期 I/O 操作の場合、大量のリソースを消費する操作が完了するまで UI スレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-155">With synchronous I/O operations, the UI thread is blocked until the resource-intensive operation has completed.</span></span>  <span data-ttu-id="24bb7-156">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを開発するときには非同期 I/O 操作を使用して、アプリが動作しなくなったと受け取られないようにします。</span><span class="sxs-lookup"><span data-stu-id="24bb7-156">Use asynchronous I/O operations when developing [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps to prevent creating the impression that your app has stopped working.</span></span>  
  
 <span data-ttu-id="24bb7-157">`Async`、<xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.FlushAsync%2A>、および <xref:System.IO.Stream.ReadAsync%2A> の各メソッドのように、非同期メンバーの名前には <xref:System.IO.Stream.WriteAsync%2A> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="24bb7-157">The asynchronous members contain `Async` in their names, such as the <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>,  <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> methods.</span></span> <span data-ttu-id="24bb7-158">これらのメソッドは、`async` キーワードおよび `await` キーワードと共に使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-158">You use these methods with the `async` and `await` keywords.</span></span>  
  
 <span data-ttu-id="24bb7-159">詳細については、「[非同期ファイル I/O](../../../docs/standard/io/asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-159">For more information, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="compression"></a><span data-ttu-id="24bb7-160">[圧縮]</span><span class="sxs-lookup"><span data-stu-id="24bb7-160">Compression</span></span>  
 <span data-ttu-id="24bb7-161">圧縮とは、保管するためにファイルのサイズを小さくするプロセスのことです。</span><span class="sxs-lookup"><span data-stu-id="24bb7-161">Compression refers to the process of reducing the size of a file for storage.</span></span> <span data-ttu-id="24bb7-162">圧縮解除は、圧縮ファイルの内容を抽出し、その内容を使用可能な形式にするプロセスです。</span><span class="sxs-lookup"><span data-stu-id="24bb7-162">Decompression is the process of extracting the contents of a compressed file so they are in a usable format.</span></span> <span data-ttu-id="24bb7-163"><xref:System.IO.Compression?displayProperty=nameWithType> 名前空間には、ファイルおよびストリームを圧縮および圧縮解除するための型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="24bb7-163">The <xref:System.IO.Compression?displayProperty=nameWithType> namespace contains types for compressing and decompressing files and streams.</span></span>  
  
 <span data-ttu-id="24bb7-164">次のクラスは、ファイルおよびストリームを圧縮および圧縮解除するときによく使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-164">The following classes are frequently used when compressing and decompressing files and streams:</span></span>  
  
-   <span data-ttu-id="24bb7-165"><xref:System.IO.Compression.ZipArchive> – ZIP アーカイブのエントリを作成および取得します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-165"><xref:System.IO.Compression.ZipArchive> – for creating and retrieving entries in the zip archive.</span></span>  
  
-   <span data-ttu-id="24bb7-166"><xref:System.IO.Compression.ZipArchiveEntry> – 圧縮ファイルを表します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-166"><xref:System.IO.Compression.ZipArchiveEntry> – for representing a compressed file.</span></span>  
  
-   <span data-ttu-id="24bb7-167"><xref:System.IO.Compression.ZipFile> – 圧縮パッケージの作成、抽出、およびオープンを行います。</span><span class="sxs-lookup"><span data-stu-id="24bb7-167"><xref:System.IO.Compression.ZipFile> – for creating,  extracting, and opening a compressed package.</span></span>  
  
-   <span data-ttu-id="24bb7-168"><xref:System.IO.Compression.ZipFileExtensions> – 圧縮パッケージのエントリを作成および抽出します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-168"><xref:System.IO.Compression.ZipFileExtensions> – for creating and extracting entries in a compressed package.</span></span>  
  
-   <span data-ttu-id="24bb7-169"><xref:System.IO.Compression.DeflateStream> – Deflate アルゴリズムを使用してストリームを圧縮および圧縮解除します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-169"><xref:System.IO.Compression.DeflateStream> – for compressing and decompressing streams using the Deflate algorithm.</span></span>  
  
-   <span data-ttu-id="24bb7-170"><xref:System.IO.Compression.GZipStream> – gzip データ形式のストリームを圧縮および圧縮解除します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-170"><xref:System.IO.Compression.GZipStream> – for compressing and decompressing streams in gzip data format.</span></span>  
  
 <span data-ttu-id="24bb7-171">「[方法: ファイルを圧縮して抽出する](../../../docs/standard/io/how-to-compress-and-extract-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-171">See [How to: Compress and Extract Files](../../../docs/standard/io/how-to-compress-and-extract-files.md).</span></span>  
  
## <a name="isolated-storage"></a><span data-ttu-id="24bb7-172">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="24bb7-172">Isolated Storage</span></span>  
 <span data-ttu-id="24bb7-173">分離ストレージは、コードと保存データを関連付ける標準化された方法を定義することにより、分離性と安全性を提供するデータ ストレージ機構です。</span><span class="sxs-lookup"><span data-stu-id="24bb7-173">Isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span> <span data-ttu-id="24bb7-174">ストレージは、ユーザー、アセンブリ、および (必要に応じて) ドメイン別に分離された仮想ファイル システムを提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-174">The storage provides a virtual file system that is isolated by user, assembly, and (optionally) domain.</span></span> <span data-ttu-id="24bb7-175">分離ストレージは、アプリケーションにユーザー ファイルへのアクセス許可がない場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="24bb7-175">Isolated storage is particularly useful when your application does not have permission to access user files.</span></span> <span data-ttu-id="24bb7-176">コンピューターのセキュリティ ポリシーによって制御される方法でアプリケーションの設定またはファイルを保存できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-176">You can save settings or files for your application in a manner that is controlled by the computer's security policy.</span></span>  
  
 <span data-ttu-id="24bb7-177">分離ストレージは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリには使用できません。代わりに、[Windows.Storage](/uwp/api/Windows.Storage) 名前空間のアプリケーション データ クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-177">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps; instead, use application data classes in the [Windows.Storage](/uwp/api/Windows.Storage) namespace.</span></span> <span data-ttu-id="24bb7-178">詳細については、Windows デベロッパー センターの[アプリケーション データ](/previous-versions/windows/apps/hh464917(v=win.10))に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-178">For more information, see [Application data](/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.</span></span>  
  
 <span data-ttu-id="24bb7-179">次のクラスは、分離ストレージを実装するときによく使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-179">The following classes are frequently used when implementing isolated storage:</span></span>  
  
-   <span data-ttu-id="24bb7-180"><xref:System.IO.IsolatedStorage.IsolatedStorage> – 分離ストレージの実装の基底クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-180"><xref:System.IO.IsolatedStorage.IsolatedStorage> – provides the base class for isolated storage implementations.</span></span>  
  
-   <span data-ttu-id="24bb7-181"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – ファイルとディレクトリを格納している分離ストレージ領域を提供します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-181"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – provides an isolated storage area that contains files and directories.</span></span>  
  
-   <span data-ttu-id="24bb7-182"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - 分離ストレージ内のファイルを公開します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-182"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - exposes a file within isolated storage.</span></span>  
  
 <span data-ttu-id="24bb7-183">「[分離ストレージ](../../../docs/standard/io/isolated-storage.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-183">See [Isolated Storage](../../../docs/standard/io/isolated-storage.md).</span></span>  
  
## <a name="io-operations-in-windows-store-apps"></a><span data-ttu-id="24bb7-184">Windows ストア アプリの I/O 操作</span><span class="sxs-lookup"><span data-stu-id="24bb7-184">I/O Operations in Windows Store apps</span></span>  
 <span data-ttu-id="24bb7-185">[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] には、ストリームの読み取りと書き込みを行うための型の多くが含まれています。ただし、このセットにすべての .NET Framework I/O 型が含まれているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="24bb7-185">The [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] contains many of the types for reading from and writing to streams; however, this set does not include all the .NET Framework I/O types.</span></span>  
  
 <span data-ttu-id="24bb7-186">次に、I/O 操作を [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用する場合に注意する必要がある重要な違いを示します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-186">Some important differences to note when using I/O operations in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps:</span></span>  
  
-   <span data-ttu-id="24bb7-187"><xref:System.IO.File>、<xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> など、特にファイル操作に関連する型は、[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="24bb7-187">Types specifically related to file operations, such as <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> and <xref:System.IO.DirectoryInfo>, are not included in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)].</span></span> <span data-ttu-id="24bb7-188">代わりに、[StorageFile](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx)、[StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx) など、[!INCLUDE[wrt](../../../includes/wrt-md.md)] の [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) 名前空間の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-188">Instead, use the types in the [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) namespace of the [!INCLUDE[wrt](../../../includes/wrt-md.md)], such as [StorageFile](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) and [StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).</span></span>  
  
-   <span data-ttu-id="24bb7-189">分離ストレージは使用できません。代わりに、[アプリケーション データ](/previous-versions/windows/apps/hh464917(v=win.10))を使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-189">Isolated storage is not available; instead, use [application data](/previous-versions/windows/apps/hh464917(v=win.10)).</span></span>  
  
-   <span data-ttu-id="24bb7-190">UI スレッドをブロックしないように、<xref:System.IO.Stream.ReadAsync%2A>、<xref:System.IO.Stream.WriteAsync%2A> などの非同期メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-190">Use asynchronous methods, such as <xref:System.IO.Stream.ReadAsync%2A> and <xref:System.IO.Stream.WriteAsync%2A>, to prevent blocking the UI thread.</span></span>  
  
-   <span data-ttu-id="24bb7-191">パス ベース圧縮の型 <xref:System.IO.Compression.ZipFile> と <xref:System.IO.Compression.ZipFileExtensions> は使用できません。</span><span class="sxs-lookup"><span data-stu-id="24bb7-191">The path-based compression types <xref:System.IO.Compression.ZipFile> and <xref:System.IO.Compression.ZipFileExtensions> are not available.</span></span> <span data-ttu-id="24bb7-192">代わりに、[Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) 名前空間の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-192">Instead, use the types in the [Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) namespace.</span></span>  
  
 <span data-ttu-id="24bb7-193">必要に応じて、.NET Framework ストリームと Windows ランタイム ストリームを変換できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-193">You can convert between .NET Framework streams and Windows Runtime streams, if necessary.</span></span> <span data-ttu-id="24bb7-194">詳細については、「[方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)」または「[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-194">For more information, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) or [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx).</span></span> <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 <span data-ttu-id="24bb7-195">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでの I/O 操作の詳細については、「[Quickstart: Reading and writing files (XAML)](/previous-versions/windows/apps/hh758325(v=win.10))」 (クイック スタート: ファイルの読み取りと書き込み) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-195">For more information about I/O operations in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span>  
  
## <a name="io-and-security"></a><span data-ttu-id="24bb7-196">I/O とセキュリティ</span><span class="sxs-lookup"><span data-stu-id="24bb7-196">I/O and Security</span></span>  
 <span data-ttu-id="24bb7-197"><xref:System.IO?displayProperty=nameWithType> 名前空間のクラスを使用する場合、アクセス制御リスト (ACL: Access Control List) などのオペレーティング システムのセキュリティ要件に従い、ファイルとディレクトリへのアクセスを制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-197">When you use the classes in the <xref:System.IO?displayProperty=nameWithType> namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories.</span></span> <span data-ttu-id="24bb7-198">この要件の他にも、<xref:System.Security.Permissions.FileIOPermission> で指定されている要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="24bb7-198">This requirement is in addition to any <xref:System.Security.Permissions.FileIOPermission> requirements.</span></span> <span data-ttu-id="24bb7-199">ACL はプログラムで管理できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-199">You can manage ACLs programmatically.</span></span> <span data-ttu-id="24bb7-200">詳細については、「[方法: アクセス制御リスト エントリを追加または削除する](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-200">For more information, see [How to: Add or Remove Access Control List Entries](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).</span></span>  
  
 <span data-ttu-id="24bb7-201">既定のセキュリティ ポリシーでは、インターネットまたはイントラネットのアプリケーションはユーザーのコンピューターのファイルにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="24bb7-201">Default security policies prevent Internet or intranet applications from accessing files on the user’s computer.</span></span> <span data-ttu-id="24bb7-202">したがって、インターネットまたはイントラネットを経由してダウンロードされるコードを記述する場合に、物理ファイル パスを必要とする I/O クラスを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-202">Therefore, do not use the I/O classes that require a path to a physical file when writing code that will be downloaded over the Internet or intranet.</span></span> <span data-ttu-id="24bb7-203">代わりに、従来の .NET Framework アプリケーション用の[分離ストレージ](../../../docs/standard/io/isolated-storage.md)を使用するか、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用の[アプリケーション データ](/previous-versions/windows/apps/hh464917(v=win.10))を使用します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-203">Instead, use [isolated storage](../../../docs/standard/io/isolated-storage.md) for traditional .NET Framework applications, or use [application data](/previous-versions/windows/apps/hh464917(v=win.10)) for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 <span data-ttu-id="24bb7-204">セキュリティ チェックが実行されるのは、ストリームが構築されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="24bb7-204">A security check is performed only when the stream is constructed.</span></span> <span data-ttu-id="24bb7-205">したがって、ストリームを開いて、そのストリームを信頼度の低いコードやアプリケーション ドメインに渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="24bb7-205">Therefore, do not open a stream and then pass it to less-trusted code or application domains.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="24bb7-206">関連トピック</span><span class="sxs-lookup"><span data-stu-id="24bb7-206">Related Topics</span></span>  
  
-   [<span data-ttu-id="24bb7-207">共通 I/O タスク</span><span class="sxs-lookup"><span data-stu-id="24bb7-207">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
  
 <span data-ttu-id="24bb7-208">ファイル、ディレクトリ、およびストリームに関連する I/O タスクの一覧、および各タスクの関連するコンテンツと例へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-208">Provides a list of I/O tasks associated with files, directories, and streams, and links to relevant content and examples for each task.</span></span>  
  
-   [<span data-ttu-id="24bb7-209">非同期ファイル I/O</span><span class="sxs-lookup"><span data-stu-id="24bb7-209">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 <span data-ttu-id="24bb7-210">非同期 I/O のパフォーマンス上の利点と基本的な操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-210">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
-   [<span data-ttu-id="24bb7-211">分離ストレージ</span><span class="sxs-lookup"><span data-stu-id="24bb7-211">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
  
 <span data-ttu-id="24bb7-212">コードと保存データを関連付ける標準的な方法を定義することにより、分離性と安全性を提供するデータ ストレージ機構について説明します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-212">Describes a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span>  
  
-   [<span data-ttu-id="24bb7-213">パイプ</span><span class="sxs-lookup"><span data-stu-id="24bb7-213">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
  
 <span data-ttu-id="24bb7-214">.NET Framework での匿名パイプ操作と名前付きパイプ操作について説明します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-214">Describes anonymous and named pipe operations in the .NET Framework.</span></span>  
  
-   [<span data-ttu-id="24bb7-215">メモリ マップト ファイル</span><span class="sxs-lookup"><span data-stu-id="24bb7-215">Memory-Mapped Files</span></span>](../../../docs/standard/io/memory-mapped-files.md)  
  
 <span data-ttu-id="24bb7-216">ディスク上のファイルの内容を仮想メモリ内に格納するメモリ マップト ファイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="24bb7-216">Describes memory-mapped files, which contain the contents of files on disk in virtual memory.</span></span> <span data-ttu-id="24bb7-217">メモリ マップト ファイルは、非常に大きなファイルを編集したり、プロセス間通信用の共有メモリを作成したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="24bb7-217">You can use memory-mapped files to edit very large files and to create shared memory for interprocess communication.</span></span>
