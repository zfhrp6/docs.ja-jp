---
title: "LINQ とファイル ディレクトリ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b9e814c9e9f8519522f288657d6940b07a0b3094
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="987ce-102">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="987ce-102">LINQ and File Directories (Visual Basic)</span></span>
<span data-ttu-id="987ce-103">多くのファイル システム操作はクエリでは基本的にはであり、LINQ アプローチによく適しているためです。</span><span class="sxs-lookup"><span data-stu-id="987ce-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="987ce-104">このセクションでクエリが非破壊的なことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="987ce-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="987ce-105">元のファイルまたはフォルダーの内容を変更するのには使用されません。</span><span class="sxs-lookup"><span data-stu-id="987ce-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="987ce-106">クエリが副次的な影響を引き起こさないことルールに従います。</span><span class="sxs-lookup"><span data-stu-id="987ce-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="987ce-107">一般に、ソース データを変更するコード (を実行するなどのクエリを作成/更新/delete 演算子) おく必要がある別のデータを単にクエリを実行するコードです。</span><span class="sxs-lookup"><span data-stu-id="987ce-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="987ce-108">このセクションでは、以下のトピックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="987ce-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="987ce-109">方法: 指定された属性または名前 (Visual Basic) のファイルをクエリ</span><span class="sxs-lookup"><span data-stu-id="987ce-109">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="987ce-110">1 つ以上のプロパティを確認するには、ファイルを検索する方法を示しています、<xref:System.IO.FileInfo>オブジェクト</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="987ce-111">方法: 拡張機能 (LINQ) (Visual Basic) でファイルをグループ化</span><span class="sxs-lookup"><span data-stu-id="987ce-111">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="987ce-112">グループを返す方法を示しています<xref:System.IO.FileInfo>オブジェクトに基づいて、ファイル名拡張子</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="987ce-113">方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる</span><span class="sxs-lookup"><span data-stu-id="987ce-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="987ce-114">指定したディレクトリ ツリー内のすべてのファイルの合計バイト数を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="987ce-115">[方法:&2; つのフォルダー (LINQ) (Visual Basic) の内容を比較](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span><span class="sxs-lookup"><span data-stu-id="987ce-115">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="987ce-116">2 つの指定したフォルダーに存在するすべてのファイルとファイルをすべて&1; つのフォルダーに存在するを返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="987ce-117">方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会</span><span class="sxs-lookup"><span data-stu-id="987ce-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="987ce-118">ディレクトリ ツリーで、最大値または最小のファイルまたはファイルの指定した数を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="987ce-119">方法: ディレクトリ ツリー (LINQ) (Visual Basic) で重複するファイルのクエリ</span><span class="sxs-lookup"><span data-stu-id="987ce-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="987ce-120">指定したディレクトリ ツリー内で複数の場所で発生するすべてのファイル名のグループ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="987ce-121">カスタムの比較演算子に基づいてさらに複雑な比較を実行する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="987ce-122">方法: クエリ (LINQ) (Visual Basic) のフォルダー内のファイルの内容</span><span class="sxs-lookup"><span data-stu-id="987ce-122">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="987ce-123">ツリー内のフォルダーを反復処理を各ファイルを開き、ファイルの内容を照会する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="987ce-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="987ce-124">コメント</span><span class="sxs-lookup"><span data-stu-id="987ce-124">Comments</span></span>  
 <span data-ttu-id="987ce-125">何らかの複雑性は正確にファイル システムの内容を表すし、例外が適切に処理するデータ ソースの作成に必要です。</span><span class="sxs-lookup"><span data-stu-id="987ce-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="987ce-126">このセクションの例のスナップショット コレクションの作成<xref:System.IO.FileInfo>指定したルート フォルダーの下のすべてのファイルとそのすべてのサブフォルダーを表すオブジェクト</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="987ce-127">それぞれの実際の状態<xref:System.IO.FileInfo>を開始し、クエリの実行を終了するときまでの間に変更することがあります</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="987ce-128">一覧を作成するなど、<xref:System.IO.FileInfo>データ ソースとして使用するオブジェクト</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="987ce-129">アクセスしようとする場合、`Length`クエリでは、プロパティ、<xref:System.IO.FileInfo>の値を更新するファイル システムにアクセスしようとして、オブジェクト`Length`</xref:System.IO.FileInfo>。</span><span class="sxs-lookup"><span data-stu-id="987ce-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="987ce-130">ファイルが存在しない場合、表示、 <xref:System.IO.FileNotFoundException>、クエリでもないクエリを実行するファイル システム直接</xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="987ce-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="987ce-131">このセクションの一部のクエリでは、特定の場合にこれらの特定の例外を使用する別のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="987ce-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="987ce-132"><xref:System.IO.FileSystemWatcher>。</xref:System.IO.FileSystemWatcher>を使用して動的に更新されるデータ ソースを保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="987ce-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987ce-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="987ce-133">See Also</span></span>  
 [<span data-ttu-id="987ce-134">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="987ce-134">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
