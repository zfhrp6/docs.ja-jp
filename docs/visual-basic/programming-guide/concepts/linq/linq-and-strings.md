---
title: "LINQ と文字列 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 94e9627efb183c08bbb67a7e6e82df9132ebdef2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="5776c-102">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5776c-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="5776c-103">LINQ を使用して、文字列および文字列のコレクションの照会し、変換することができます。</span><span class="sxs-lookup"><span data-stu-id="5776c-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="5776c-104">テキスト ファイル内の半構造化データで特に便利ですができます。</span><span class="sxs-lookup"><span data-stu-id="5776c-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="5776c-105">LINQ クエリは、従来の文字列関数と正規表現と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="5776c-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="5776c-106">たとえば、使用、<xref:System.String.Split%2A>または<xref:System.Text.RegularExpressions.Regex.Split%2A>し、クエリまたは LINQ を使用して変更できる文字列の配列を作成する方法</xref:System.Text.RegularExpressions.Regex.Split%2A></xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="5776c-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="5776c-107">使用することができます、<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>メソッドで、 `where` LINQ クエリの句</xref:System.Text.RegularExpressions.Regex.IsMatch%2A>。</span><span class="sxs-lookup"><span data-stu-id="5776c-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="5776c-108">LINQ を使用するには照会または変更して、<xref:System.Text.RegularExpressions.MatchCollection>正規表現によって返される結果</xref:System.Text.RegularExpressions.MatchCollection>。</span><span class="sxs-lookup"><span data-stu-id="5776c-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="5776c-109">半構造化テキスト データを XML に変換するのにこのセクションで説明した手法を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5776c-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="5776c-110">詳細については、次を参照してください。[方法: CSV ファイルから XML の生成](how-to-generate-xml-from-csv-files.md)します。</span><span class="sxs-lookup"><span data-stu-id="5776c-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="5776c-111">このセクションの例では、2 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="5776c-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="5776c-112">テキストのブロックのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5776c-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="5776c-113">クエリ、分析、およびテキスト ブロックを変更するを使用して、クエリ可能な小さな文字列の配列に分割する、<xref:System.String.Split%2A>メソッドまたは<xref:System.Text.RegularExpressions.Regex.Split%2A>メソッド</xref:System.Text.RegularExpressions.Regex.Split%2A></xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="5776c-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="5776c-114">ソース テキストを単語、文、段落、ページ、またはその他の条件に分割し、その後、クエリで必要とされるに応じてその他の分割を実行できます。</span><span class="sxs-lookup"><span data-stu-id="5776c-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="5776c-115">方法: 文字列 (LINQ) (Visual Basic) での単語の出現回数をカウント</span><span class="sxs-lookup"><span data-stu-id="5776c-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="5776c-116">テキストに対する単純なクエリの実行に LINQ を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="5776c-117">方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。</span><span class="sxs-lookup"><span data-stu-id="5776c-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="5776c-118">任意の境界上でテキスト ファイルに分割する方法と各部分に対してクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="5776c-119">方法: クエリ (LINQ) (Visual Basic) の文字列内の文字</span><span class="sxs-lookup"><span data-stu-id="5776c-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="5776c-120">文字列がクエリ可能型であることを示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="5776c-121">方法: LINQ クエリは、正規表現 (Visual Basic) とを組み合わせる</span><span class="sxs-lookup"><span data-stu-id="5776c-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="5776c-122">フィルター選択されたクエリの結果に一致する複雑なパターンの LINQ クエリで正規表現を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="5776c-123">テキスト形式の半構造化データの照会</span><span class="sxs-lookup"><span data-stu-id="5776c-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="5776c-124">さまざまな種類のテキスト ファイルは、一連のタブ区切りまたはカンマ区切りのファイル、または固定長の行などのような書式設定を含む多くの場合、線で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5776c-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="5776c-125">メモリにこのようなテキスト ファイルが読み取られた後に、クエリを実行するか、または行を変更する LINQ を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5776c-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="5776c-126">また、LINQ クエリには、複数のソースからデータを結合したタスクが簡略化します。</span><span class="sxs-lookup"><span data-stu-id="5776c-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="5776c-127">方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を検索</span><span class="sxs-lookup"><span data-stu-id="5776c-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="5776c-128">1 つのリストに存在するすべての文字列を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="5776c-129">方法: 並べ替えまたはフィルター テキスト データでは、任意の単語またはフィールド (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5776c-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="5776c-130">任意の単語またはフィールドに基づくテキスト行を並べ替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="5776c-131">方法: 区切り記号入りファイル (LINQ) (Visual Basic) のフィールドの順序を変更</span><span class="sxs-lookup"><span data-stu-id="5776c-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="5776c-132">.Csv ファイルの行のフィールドの順序を変更する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="5776c-133">方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5776c-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="5776c-134">さまざまな方法で文字列のリストを結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="5776c-135">方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定</span><span class="sxs-lookup"><span data-stu-id="5776c-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="5776c-136">データ ソースとして複数のテキスト ファイルを使用してオブジェクトのコレクションを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="5776c-137">方法: 異種ファイル (LINQ) (Visual Basic の場合) からコンテンツを結合します。</span><span class="sxs-lookup"><span data-stu-id="5776c-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="5776c-138">1 つの文字列に一致するキーを使用して&2; つのリスト内の文字列を結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="5776c-139">方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割</span><span class="sxs-lookup"><span data-stu-id="5776c-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="5776c-140">データ ソースとして&1; つのファイルを使用して新しいファイルを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="5776c-141">方法: CSV テキスト ファイル (LINQ) (Visual Basic) の列の値を計算</span><span class="sxs-lookup"><span data-stu-id="5776c-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="5776c-142">.Csv ファイル内のテキスト データに対して数学的な計算を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5776c-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5776c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="5776c-143">See Also</span></span>  
 <span data-ttu-id="5776c-144">[統合言語クエリ (LINQ) (Visual Basic)](index.md) </span><span class="sxs-lookup"><span data-stu-id="5776c-144">[Language-Integrated Query (LINQ) (Visual Basic)](index.md) </span></span>  
<span data-ttu-id="5776c-145"> [方法: CSV ファイルから XML を生成する](how-to-generate-xml-from-csv-files.md)</span><span class="sxs-lookup"><span data-stu-id="5776c-145"> [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md)</span></span>

