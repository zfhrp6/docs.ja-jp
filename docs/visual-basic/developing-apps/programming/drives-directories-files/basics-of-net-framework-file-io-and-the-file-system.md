---
title: ".NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)"
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
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b84e8bbaeb09bfe2ccddb17ecb9b0f8f71cd37c6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="1e1af-102">.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e1af-102">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>
<span data-ttu-id="1e1af-103"><xref:System.IO> 名前空間のクラスは、ドライブ、ファイル、ディレクトリの操作に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-103">Classes in the <xref:System.IO> namespace are used to work with drives, files, and directories.</span></span>  
  
 <span data-ttu-id="1e1af-104"><xref:System.IO> 名前空間には <xref:System.IO.File> クラスと <xref:System.IO.Directory> クラスが含まれています。これらのクラスを使用すると、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] でファイルとディレクトリを操作できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-104">The <xref:System.IO> namespace contains the <xref:System.IO.File> and <xref:System.IO.Directory> classes, which provide the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] functionality that manipulates files and directories.</span></span> <span data-ttu-id="1e1af-105">これらのオブジェクトのメソッドは静的メンバーまたは共有メンバーなので、あらかじめクラスのインスタンスを作成しなくてもメンバーを直接使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-105">Because the methods of these objects are static or shared members, you can use them directly without creating an instance of the class first.</span></span> <span data-ttu-id="1e1af-106">これらのクラスに関連するクラスとして、<xref:System.IO.FileInfo> クラスと <xref:System.IO.DirectoryInfo> クラスがあります。`My` 機能を使用しているユーザーには使い慣れたクラスです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-106">Associated with these classes are the <xref:System.IO.FileInfo> and <xref:System.IO.DirectoryInfo> classes, which will be familiar to users of the `My` feature.</span></span> <span data-ttu-id="1e1af-107">これらのクラスを使用するには、名前を完全修飾するか、または、関係するコードの先頭に `Imports` ステートメントを記述して、適切な名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e1af-107">To use these classes, you must fully qualify the names or import the appropriate namespaces by including the `Imports` statement(s) at the beginning of the affected code.</span></span> <span data-ttu-id="1e1af-108">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e1af-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e1af-109">このセクションのそのほかのトピックでは `My.Computer.FileSystem` のクラスではなく、 `System.IO` オブジェクトを使用して、ドライブ、ファイル、およびディレクトリを操作します。</span><span class="sxs-lookup"><span data-stu-id="1e1af-109">Other topics in this section use the `My.Computer.FileSystem` object instead of `System.IO` classes to work with drives, files, and directories.</span></span> <span data-ttu-id="1e1af-110">`My.Computer.FileSystem` オブジェクトは [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のプログラムで使用する主な目的としています。</span><span class="sxs-lookup"><span data-stu-id="1e1af-110">The `My.Computer.FileSystem` object is intended primarily for use in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programs.</span></span> <span data-ttu-id="1e1af-111">`System.IO` のクラスは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] をサポートする [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] などの言語で使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-111">`System.IO` classes are intended for use by any language that supports the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], including [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="definition-of-a-stream"></a><span data-ttu-id="1e1af-112">ストリームの定義</span><span class="sxs-lookup"><span data-stu-id="1e1af-112">Definition of a Stream</span></span>  
 <span data-ttu-id="1e1af-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、ファイルに対する読み取りと書き込みをサポートするストリームを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] uses streams to support reading from and writing to files.</span></span> <span data-ttu-id="1e1af-114">ストリームとは、1 次元の連続したデータの集まりと考えることができます。ストリームには先頭と末尾があり、カーソルでストリーム内での現在の位置を示します。</span><span class="sxs-lookup"><span data-stu-id="1e1af-114">You can think of a stream as a one-dimensional set of contiguous data, which has a beginning and an end, and where the cursor indicates the current position in the stream.</span></span>  
  
 <span data-ttu-id="1e1af-115">![Filestream 内の現在位置を示すカーソル。] (../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")</span><span class="sxs-lookup"><span data-stu-id="1e1af-115">![Cursor shows current position in the filestream.](../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")</span></span>  
  
## <a name="stream-operations"></a><span data-ttu-id="1e1af-116">ストリームの操作</span><span class="sxs-lookup"><span data-stu-id="1e1af-116">Stream Operations</span></span>  
 <span data-ttu-id="1e1af-117">ストリームに格納されているデータは、メモリ、ファイル、または TCP/IP ソケットから取得したものです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-117">The data contained in the stream may come from memory, a file, or a TCP/IP socket.</span></span> <span data-ttu-id="1e1af-118">ストリームに対しては、次の基本操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-118">Streams have fundamental operations that can be applied to them:</span></span>  
  
-   <span data-ttu-id="1e1af-119">読み取り。</span><span class="sxs-lookup"><span data-stu-id="1e1af-119">Reading.</span></span> <span data-ttu-id="1e1af-120">ストリームを読み取ったり、文字列やバイト配列などのデータ構造にストリームからデータを転送したりできます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-120">You can read from a stream, transferring data from the stream into a data structure, such as a string or an array of bytes.</span></span>  
  
-   <span data-ttu-id="1e1af-121">**書き込み**。</span><span class="sxs-lookup"><span data-stu-id="1e1af-121">**Writing**.</span></span> <span data-ttu-id="1e1af-122">ストリームに書き込んだり、データ ソースからストリームにデータを転送したりできます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-122">You can write to a stream, transferring data from a data source into the stream.</span></span>  
  
-   <span data-ttu-id="1e1af-123">**シーク**。</span><span class="sxs-lookup"><span data-stu-id="1e1af-123">**Seeking**.</span></span> <span data-ttu-id="1e1af-124">ストリーム内の現在の位置をクエリおよび変更できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-124">You can query and modify your position in the stream.</span></span>  
  
 <span data-ttu-id="1e1af-125">詳細については、「 [Composing Streams](https://msdn.microsoft.com/library/e4y2dch9)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e1af-125">For more information, see [Composing Streams](https://msdn.microsoft.com/library/e4y2dch9).</span></span>  
  
## <a name="types-of-streams"></a><span data-ttu-id="1e1af-126">ストリームの種類</span><span class="sxs-lookup"><span data-stu-id="1e1af-126">Types of Streams</span></span>  
 <span data-ttu-id="1e1af-127">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、ストリームは <xref:System.IO.Stream> クラスで表されます。これは、その他のすべてのストリームのための抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-127">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a stream is represented by the <xref:System.IO.Stream> class, which forms the abstract class for all other streams.</span></span> <span data-ttu-id="1e1af-128"><xref:System.IO.Stream> クラスのインスタンスを直接作成することはできません。これを実装するいずれかのクラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e1af-128">You cannot directly create an instance of the <xref:System.IO.Stream> class, but must use one of the classes it implements.</span></span>  
  
 <span data-ttu-id="1e1af-129">ストリームにはさまざまな種類がありますが、ファイルの入出力 (I/O) を処理するという目的のために最も重要なのは、ファイルに対する読み取りと書き込みを実現する <xref:System.IO.FileStream> クラスと、分離ストレージに対するファイルやディレクトリの作成を実現する <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> クラスです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-129">There are many types of streams, but for the purposes of working with file input/output (I/O), the most important types are the <xref:System.IO.FileStream> class, which provides a way to read from and write to files, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> class, which provides a way to create files and directories in isolated storage.</span></span> <span data-ttu-id="1e1af-130">この他、ファイル I/O を処理する場合、以下のようなストリームを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-130">Other streams that can be used when working with file I/O include:</span></span>  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <span data-ttu-id="1e1af-131"><xref:System.Net.Sockets.NetworkStream>。</span><span class="sxs-lookup"><span data-stu-id="1e1af-131"><xref:System.Net.Sockets.NetworkStream>.</span></span>  
  
 <span data-ttu-id="1e1af-132">次の表は、ストリームで一般的に実行するタスクの一覧です。</span><span class="sxs-lookup"><span data-stu-id="1e1af-132">The following table lists tasks commonly accomplished with a stream:</span></span>  
  
|<span data-ttu-id="1e1af-133">目的</span><span class="sxs-lookup"><span data-stu-id="1e1af-133">To</span></span>|<span data-ttu-id="1e1af-134">参照トピック</span><span class="sxs-lookup"><span data-stu-id="1e1af-134">See</span></span>|
|---|---|   
|<span data-ttu-id="1e1af-135">データ ファイルに対する読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="1e1af-135">Read and write to a data file</span></span>|[<span data-ttu-id="1e1af-136">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="1e1af-136">How to: Read and Write to a Newly Created Data File</span></span>](https://msdn.microsoft.com/library/36b93480.aspx)|  
|<span data-ttu-id="1e1af-137">ファイルのテキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="1e1af-137">Read text from a file</span></span>|[<span data-ttu-id="1e1af-138">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="1e1af-138">How to: Read Text from a File</span></span>](https://msdn.microsoft.com/library/db5x7c0d.aspx)|  
|<span data-ttu-id="1e1af-139">テキストのファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="1e1af-139">Write text to a file</span></span>|[<span data-ttu-id="1e1af-140">方法: ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="1e1af-140">How to: Write Text to a File</span></span>](https://msdn.microsoft.com/library/6ka1wd3w.aspx)|  
|<span data-ttu-id="1e1af-141">文字列からの文字の読み取り</span><span class="sxs-lookup"><span data-stu-id="1e1af-141">Read characters from a string</span></span>|[<span data-ttu-id="1e1af-142">方法: 文字列から文字を読み取る</span><span class="sxs-lookup"><span data-stu-id="1e1af-142">How to: Read Characters from a String</span></span>](https://msdn.microsoft.com/library/9yyz8a6c.aspx)|  
|<span data-ttu-id="1e1af-143">文字列への文字の書き込み</span><span class="sxs-lookup"><span data-stu-id="1e1af-143">Write characters to a string</span></span>|[<span data-ttu-id="1e1af-144">方法: 文字列に文字を書き込む</span><span class="sxs-lookup"><span data-stu-id="1e1af-144">How to: Write Characters to a String</span></span>](https://msdn.microsoft.com/library/z4kzt0dd.aspx)|  
|<span data-ttu-id="1e1af-145">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="1e1af-145">Encrypt data</span></span>|[<span data-ttu-id="1e1af-146">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="1e1af-146">Encrypting Data</span></span>](https://msdn.microsoft.com/library/as0w18af.aspx)|  
|<span data-ttu-id="1e1af-147">データの復号化</span><span class="sxs-lookup"><span data-stu-id="1e1af-147">Decrypt data</span></span>|[<span data-ttu-id="1e1af-148">データの復号化</span><span class="sxs-lookup"><span data-stu-id="1e1af-148">Decrypting Data</span></span>](https://msdn.microsoft.com/library/te15te69.aspx)|  
  
## <a name="file-access-and-attributes"></a><span data-ttu-id="1e1af-149">ファイル アクセスと属性</span><span class="sxs-lookup"><span data-stu-id="1e1af-149">File Access and Attributes</span></span>  
 <span data-ttu-id="1e1af-150">ファイルの作成、オープン、および共有の方法は、<xref:System.IO.FileAccess>、<xref:System.IO.FileMode>、および <xref:System.IO.FileShare> の各列挙体で制御できます。これらの列挙体には、<xref:System.IO.FileStream> クラスのコンストラクターで使用するフラグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1e1af-150">You can control how files are created, opened, and shared with the <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, and <xref:System.IO.FileShare> enumerations, which contain the flags used by the constructors of the <xref:System.IO.FileStream> class.</span></span> <span data-ttu-id="1e1af-151">たとえば、<xref:System.IO.FileStream> を開くかまたは新規作成するときに、ファイルを追加書き込み用に開くかどうか、指定のファイルが存在しない場合にファイルを新規作成するかどうか、ファイルを上書きするかどうか、などを <xref:System.IO.FileMode> 列挙体で指定できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-151">For example, when you open or create a new <xref:System.IO.FileStream>, the <xref:System.IO.FileMode> enumeration allows you to specify whether the file is opened for appending, whether a new file is created if the specified file does not exist, whether the file is overwritten, and so forth.</span></span>  
  
 <span data-ttu-id="1e1af-152"><xref:System.IO.FileAttributes> 列挙体を使用すると、ファイル固有の情報を収集できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-152">The <xref:System.IO.FileAttributes> enumeration enables the gathering of file-specific information.</span></span> <span data-ttu-id="1e1af-153"><xref:System.IO.FileAttributes> 列挙体は、格納されているファイルの属性を返します。これらの属性によって、圧縮ファイル、暗号化されたファイル、隠しファイル、読み取り専用ファイル、アーカイブ、ディレクトリ、システム ファイル、一時ファイルであるかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="1e1af-153">The <xref:System.IO.FileAttributes> enumeration returns the file's stored attributes, such as whether it is compressed, encrypted, hidden, read-only, an archive, a directory, a system file, or a temporary file.</span></span>  
  
 <span data-ttu-id="1e1af-154">次の表は、ファイル アクセスとファイル属性に関連するタスクの一覧です。</span><span class="sxs-lookup"><span data-stu-id="1e1af-154">The following table lists tasks involving file access and file attributes:</span></span>  
  
|<span data-ttu-id="1e1af-155">目的</span><span class="sxs-lookup"><span data-stu-id="1e1af-155">To</span></span>|<span data-ttu-id="1e1af-156">参照トピック</span><span class="sxs-lookup"><span data-stu-id="1e1af-156">See</span></span>|  
|---|---|
|<span data-ttu-id="1e1af-157">ログ ファイルのオープンとテキストの追加</span><span class="sxs-lookup"><span data-stu-id="1e1af-157">Open and append text to a log file</span></span>|[<span data-ttu-id="1e1af-158">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="1e1af-158">How to: Open and Append to a Log File</span></span>](https://msdn.microsoft.com/library/3zc0w663.aspx)|  
|<span data-ttu-id="1e1af-159">ファイルの属性の判断</span><span class="sxs-lookup"><span data-stu-id="1e1af-159">Determine the attributes of a file</span></span>|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a><span data-ttu-id="1e1af-160">ファイルのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="1e1af-160">File Permissions</span></span>  
 <span data-ttu-id="1e1af-161">ファイルおよびディレクトリに対するアクセスの制御は、<xref:System.Security.Permissions.FileIOPermission> クラスで行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-161">Controlling access to files and directories can be done with the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="1e1af-162">これは、Web フォームの開発者には特に重要な場合があります。既定では、Web フォームは、ASPNET という名前の特別なローカル ユーザー アカウントのコンテキストで実行されます。ASPNET は、[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] および [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のインストール時に作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-162">This may be particularly important for developers working with Web Forms, which by default run within the context of a special local user account named ASPNET, which is created as part of the [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] and [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] installations.</span></span> <span data-ttu-id="1e1af-163">ASPNET ユーザー アカウントはアクセス許可が制限されているため、アプリケーションがリソースへのアクセスを要求したときに、ユーザーが処理を実行できない場合があります (たとえば、Web アプリケーションからファイルへの書き込みなど)。</span><span class="sxs-lookup"><span data-stu-id="1e1af-163">When such an application requests access to a resource, the ASPNET user account has limited permissions, which may prevent the user from performing actions such as writing to a file from a Web application.</span></span> <span data-ttu-id="1e1af-164">詳細については、[セキュリティのアクセス許可](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0)に関するページと <xref:System.Security.Permissions.FileIOPermission> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e1af-164">For more information, see [Security Permissions](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0), and the <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
## <a name="isolated-file-storage"></a><span data-ttu-id="1e1af-165">分離ファイル ストレージ</span><span class="sxs-lookup"><span data-stu-id="1e1af-165">Isolated File Storage</span></span>  
 <span data-ttu-id="1e1af-166">分離ストレージとは、ファイルを扱うときに、必要なアクセス許可をユーザーまたはコードが持っていないために生じる問題を解決するためのものです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-166">Isolated storage is an attempt to solve problems created when working with files where the user or code may lack necessary permissions.</span></span> <span data-ttu-id="1e1af-167">分離ストレージでは、各ユーザーにデータ コンパートメントが割り当てられます。このデータ コンパートメントには、1 つまたは複数のストアを保持できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-167">Isolated storage assigns each user a data compartment, which can hold one or more stores.</span></span> <span data-ttu-id="1e1af-168">ストア間は、ユーザーおよびアセンブリごとに分離できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-168">Stores can be isolated from each other by user and by assembly.</span></span> <span data-ttu-id="1e1af-169">ストアにアクセスできるのは、それを作成したユーザーおよびアセンブリのみです。</span><span class="sxs-lookup"><span data-stu-id="1e1af-169">Only the user and assembly that created a store have access to it.</span></span> <span data-ttu-id="1e1af-170">ストアは、完全な仮想ファイル システムとして機能します。つまり、ストア内でディレクトリやファイルを作成および操作できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-170">A store acts as a complete virtual file system—within one store you can create and manipulate directories and files.</span></span>  
  
 <span data-ttu-id="1e1af-171">次の表は、分離ファイル ストレージに一般に関連するタスクの一覧です。</span><span class="sxs-lookup"><span data-stu-id="1e1af-171">The following table lists tasks commonly associated with isolated file storage.</span></span>  
  
|<span data-ttu-id="1e1af-172">目的</span><span class="sxs-lookup"><span data-stu-id="1e1af-172">To</span></span>|<span data-ttu-id="1e1af-173">参照トピック</span><span class="sxs-lookup"><span data-stu-id="1e1af-173">See</span></span>|
|---|---|  
|<span data-ttu-id="1e1af-174">分離ストアの作成</span><span class="sxs-lookup"><span data-stu-id="1e1af-174">Create an isolated store</span></span>|[<span data-ttu-id="1e1af-175">方法: 分離ストレージでストアを取得する</span><span class="sxs-lookup"><span data-stu-id="1e1af-175">How to: Obtain Stores for Isolated Storage</span></span>](https://msdn.microsoft.com/library/k48a6h13.aspx)|  
|<span data-ttu-id="1e1af-176">分離ストアの列挙</span><span class="sxs-lookup"><span data-stu-id="1e1af-176">Enumerate isolated stores</span></span>|[<span data-ttu-id="1e1af-177">方法: 分離ストレージでストアを列挙する</span><span class="sxs-lookup"><span data-stu-id="1e1af-177">How to: Enumerate Stores for Isolated Storage</span></span>](https://msdn.microsoft.com/library/c3dy613a.aspx)|  
|<span data-ttu-id="1e1af-178">分離ストアの削除</span><span class="sxs-lookup"><span data-stu-id="1e1af-178">Delete an isolated store</span></span>|[<span data-ttu-id="1e1af-179">方法: 分離ストレージでストアを削除する</span><span class="sxs-lookup"><span data-stu-id="1e1af-179">How to: Delete Stores in Isolated Storage</span></span>](https://msdn.microsoft.com/library/5w71t104.aspx)|  
|<span data-ttu-id="1e1af-180">分離ストレージのファイルまたはディレクトリの作成</span><span class="sxs-lookup"><span data-stu-id="1e1af-180">Create a file or directory in isolated storage</span></span>|[<span data-ttu-id="1e1af-181">方法: 分離ストレージでファイルおよびディレクトリを作成する</span><span class="sxs-lookup"><span data-stu-id="1e1af-181">How to: Create Files and Directories in Isolated Storage</span></span>](https://msdn.microsoft.com/library/6h2ws3ft.aspx)|  
|<span data-ttu-id="1e1af-182">分離ストレージのファイルの検索</span><span class="sxs-lookup"><span data-stu-id="1e1af-182">Find a file in isolated storage</span></span>|[<span data-ttu-id="1e1af-183">方法: 分離ストレージ内でファイルおよびディレクトリを検索する</span><span class="sxs-lookup"><span data-stu-id="1e1af-183">How to: Find Existing Files and Directories in Isolated Storage</span></span>](https://msdn.microsoft.com/library/zd5e2z84.aspx)|  
|<span data-ttu-id="1e1af-184">分離ストレージのファイルに対する読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="1e1af-184">Read from or write to a file in insolated storage</span></span>|[<span data-ttu-id="1e1af-185">方法: 分離ストレージ内でファイルの読み取りと書き込みを行う</span><span class="sxs-lookup"><span data-stu-id="1e1af-185">How to: Read and Write to Files in Isolated Storage</span></span>](https://msdn.microsoft.com/library/xf96a1wz.aspx)|  
|<span data-ttu-id="1e1af-186">分離ストレージのファイルまたはディレクトリの削除</span><span class="sxs-lookup"><span data-stu-id="1e1af-186">Delete a file or directory in isolated storage</span></span>|[<span data-ttu-id="1e1af-187">方法: 分離ストレージでファイルおよびディレクトリを削除する</span><span class="sxs-lookup"><span data-stu-id="1e1af-187">How to: Delete Files and Directories in Isolated Storage</span></span>](https://msdn.microsoft.com/library/kx3852wf.aspx)|  
  
## <a name="file-events"></a><span data-ttu-id="1e1af-188">ファイルのイベント</span><span class="sxs-lookup"><span data-stu-id="1e1af-188">File Events</span></span>  
 <span data-ttu-id="1e1af-189"><xref:System.IO.FileSystemWatcher> コンポーネントを使用すると、自システム上のファイルとディレクトリ、またはネットワークでアクセスできる任意のコンピューター上のファイルとディレクトリの変更を監視できます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-189">The <xref:System.IO.FileSystemWatcher> component allows you to watch for changes in files and directories on your system or on any computer to which you have network access.</span></span> <span data-ttu-id="1e1af-190">たとえば、ファイルが変更されたときに、その旨をユーザーに警告することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1e1af-190">For example, if a file is modified, you might want to send a user an alert that the change has taken place.</span></span> <span data-ttu-id="1e1af-191">変更が行われると、1 つまたは複数のイベントが発生し、バッファーに格納され、<xref:System.IO.FileSystemWatcher> コンポーネントに渡されて処理されます。</span><span class="sxs-lookup"><span data-stu-id="1e1af-191">When changes occur, one or more events are raised, stored in a buffer, and handed to the <xref:System.IO.FileSystemWatcher> component for processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e1af-192">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e1af-192">See Also</span></span>  
 <span data-ttu-id="1e1af-193">[ストリームの構成](https://msdn.microsoft.com/library/e4y2dch9) </span><span class="sxs-lookup"><span data-stu-id="1e1af-193">[Composing Streams](https://msdn.microsoft.com/library/e4y2dch9) </span></span>  
 <span data-ttu-id="1e1af-194">[ファイルおよびストリーム入出力](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="1e1af-194">[File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
 <span data-ttu-id="1e1af-195">[非同期ファイル I/O](https://msdn.microsoft.com/library/kztecsys) </span><span class="sxs-lookup"><span data-stu-id="1e1af-195">[Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys) </span></span>  
 [<span data-ttu-id="1e1af-196">.NET Framework のファイル I/O とファイル システムで使用するクラス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e1af-196">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)

