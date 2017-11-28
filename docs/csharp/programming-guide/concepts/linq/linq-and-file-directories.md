---
title: "LINQ とファイル ディレクトリ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 62c7ee272c788ca687b84bb76a853e58f83f69ab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="linq-and-file-directories-c"></a><span data-ttu-id="fe02a-102">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-102">LINQ and File Directories (C#)</span></span>
<span data-ttu-id="fe02a-103">多くのファイル システム操作は基本的にクエリであるため、LINQ での使用に最適です。</span><span class="sxs-lookup"><span data-stu-id="fe02a-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="fe02a-104">ここで示すクエリは破壊的ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fe02a-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="fe02a-105">元のファイルやフォルダーの内容が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="fe02a-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="fe02a-106">これは、クエリは副作用を引き起こすべきではないという規則に従っています。</span><span class="sxs-lookup"><span data-stu-id="fe02a-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="fe02a-107">一般に、参照元データを変更するコード (create、update、または delete の各演算子を実行するクエリなど) は、単にデータを照会するだけのコードとは分離する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe02a-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="fe02a-108">このセクションでは、以下のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="fe02a-109">方法: 指定された属性または名前のファイルを照会する (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-109">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="fe02a-110"><xref:System.IO.FileInfo> オブジェクトで 1 つ以上のプロパティを調べ、ファイルを検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="fe02a-111">方法: 拡張子別にファイルをグループ化する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-111">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="fe02a-112">ファイル名拡張子に基づいて、<xref:System.IO.FileInfo> オブジェクトのグループを返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="fe02a-113">方法: 一連のフォルダーの合計バイト数を問い合わせる (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)  
 <span data-ttu-id="fe02a-114">指定したディレクトリ ツリー内のすべてのファイルの合計バイト数を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="fe02a-115">[方法: 2 つのフォルダーの内容を比較する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)</span><span class="sxs-lookup"><span data-stu-id="fe02a-115">[How to: Compare the Contents of Two Folders (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="fe02a-116">指定した 2 つのフォルダーに存在するファイルをすべて返す方法と、一方のフォルダーにのみ存在し、もう一方には存在しないファイルをすべて返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="fe02a-117">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="fe02a-118">ディレクトリ ツリーで、最もサイズの大きいファイルまたは最もサイズの小さいファイル、あるいは指定した数のファイルを返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="fe02a-119">方法: ディレクトリ ツリーで重複するファイルを問い合わせる (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="fe02a-120">指定したディレクトリ ツリーの複数の場所に出現するすべてのファイル名をグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="fe02a-121">また、カスタム比較演算子に基づいて、より複雑な比較を実行する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="fe02a-122">方法: フォルダー内のファイルの内容を照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-122">How to: Query the Contents of Files in a Folder (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-lin.md)  
 <span data-ttu-id="fe02a-123">ツリー内のフォルダーを反復処理し、各ファイルを開き、ファイルの内容を照会する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="fe02a-124">コメント</span><span class="sxs-lookup"><span data-stu-id="fe02a-124">Comments</span></span>  
 <span data-ttu-id="fe02a-125">ファイル システムの内容を正確に表し、例外を適切に処理するデータ ソースを作成する手順は複雑になります。</span><span class="sxs-lookup"><span data-stu-id="fe02a-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="fe02a-126">ここに示す例では、指定したルート フォルダーおよびすべてのサブフォルダーの下にある、すべてのファイルを表す <xref:System.IO.FileInfo> オブジェクトのスナップショット コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="fe02a-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="fe02a-127">各 <xref:System.IO.FileInfo> の実際の状態は、クエリの実行の開始時点から終了時点までの間に変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fe02a-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="fe02a-128">たとえば、データ ソースとして使用する <xref:System.IO.FileInfo> オブジェクトの一覧を作成したとします。</span><span class="sxs-lookup"><span data-stu-id="fe02a-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="fe02a-129">クエリで `Length` プロパティにアクセスしようとすると、<xref:System.IO.FileInfo> オブジェクトがファイル システムにアクセスして `Length` の値を更新しようとします。</span><span class="sxs-lookup"><span data-stu-id="fe02a-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="fe02a-130">ファイルがもう存在しない場合は、ファイル システムを直接照会していなくても、クエリから <xref:System.IO.FileNotFoundException> が返されます。</span><span class="sxs-lookup"><span data-stu-id="fe02a-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="fe02a-131">ここで示すクエリの中には、状況により、このような特定の例外を処理する個別のメソッドを使用しているものがあります。</span><span class="sxs-lookup"><span data-stu-id="fe02a-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="fe02a-132">別の方法として、<xref:System.IO.FileSystemWatcher> を使用して、データ ソースを動的に更新して常に最新の状態に保つこともできます。</span><span class="sxs-lookup"><span data-stu-id="fe02a-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe02a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe02a-133">See Also</span></span>  
 [<span data-ttu-id="fe02a-134">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="fe02a-134">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
