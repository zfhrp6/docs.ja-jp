---
title: LINQ と文字列 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: a76465b33a30d149cd6313e2628ee742e248ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="a25e9-102">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25e9-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="a25e9-103">文字列やそのコレクションは、LINQ を使って照会したり変換したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="a25e9-104">特に、テキスト ファイル内の半構造化されたデータでその利便性が発揮されます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="a25e9-105">LINQ クエリは、従来の文字列関数や正規表現と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="a25e9-106">たとえば、<xref:System.String.Split%2A> または <xref:System.Text.RegularExpressions.Regex.Split%2A> メソッドを使用して、文字列の配列を作成し、その後で LINQ を使用してクエリを実行したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="a25e9-107">LINQ クエリの `where` 句で <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="a25e9-108">LINQ を使用して、正規表現によって返される <xref:System.Text.RegularExpressions.MatchCollection> の結果に対してクエリを実行したり変更したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="a25e9-109">このセクションで説明する手法を使えば、半構造化されたテキスト データを XML に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="a25e9-110">詳細については、「[方法: CSV ファイルから XML を生成する](how-to-generate-xml-from-csv-files.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a25e9-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="a25e9-111">このセクションの例は、次の 2 つのカテゴリに分かれています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="a25e9-112">テキスト ブロックの照会</span><span class="sxs-lookup"><span data-stu-id="a25e9-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="a25e9-113"><xref:System.String.Split%2A> メソッドまたは <xref:System.Text.RegularExpressions.Regex.Split%2A> メソッドを使用して、テキスト ブロックをクエリ可能な小さな文字列の配列に分割することによって、テキスト ブロックのクエリ、分析、および変更を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="a25e9-114">単語や文、段落、ページなどの単位にソース テキストを分割できるほか、クエリ内で必要であれば、さらに細かく分割することもできます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="a25e9-115">方法: 文字列 (LINQ) (Visual Basic) に含まれる単語の出現回数をカウント</span><span class="sxs-lookup"><span data-stu-id="a25e9-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="a25e9-116">テキストに対する単純なクエリを LINQ で行う方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="a25e9-117">方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。</span><span class="sxs-lookup"><span data-stu-id="a25e9-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="a25e9-118">区切りを指定してテキスト ファイルを分割する方法やその各構成要素に対してクエリを実行する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="a25e9-119">方法: 文字列 (LINQ) (Visual Basic) 内の文字に対するクエリ</span><span class="sxs-lookup"><span data-stu-id="a25e9-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="a25e9-120">文字列がクエリ可能型であることを実証します。</span><span class="sxs-lookup"><span data-stu-id="a25e9-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="a25e9-121">方法: LINQ クエリを正規表現 (Visual Basic) とを組み合わせる</span><span class="sxs-lookup"><span data-stu-id="a25e9-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="a25e9-122">LINQ クエリで正規表現を使い、フィルター処理されたクエリ結果に対して複雑なパターン マッチを行う方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="a25e9-123">半構造化されたテキスト形式データのクエリ</span><span class="sxs-lookup"><span data-stu-id="a25e9-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="a25e9-124">テキスト ファイルにはさまざまな種類がありますが、タブ区切りファイルやコンマ区切りファイル、固定長行など同様の形式を持った一連の行で構成されていることは少なくありません。</span><span class="sxs-lookup"><span data-stu-id="a25e9-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="a25e9-125">そのようなテキスト ファイルをメモリに読み込んだ後、LINQ を使って、必要な行を照会したり編集したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="a25e9-126">複数ソースからのデータを組み合わせる作業も LINQ クエリなら簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a25e9-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="a25e9-127">方法: 2 つのリスト (LINQ) (Visual Basic) の差集合を検索</span><span class="sxs-lookup"><span data-stu-id="a25e9-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="a25e9-128">ある特定のリストには存在しているものの、それ以外には存在しない文字列をすべて探す方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="a25e9-129">方法: 並べ替えまたはフィルター テキスト データで任意の単語またはフィールド (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25e9-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="a25e9-130">単語やフィールドに基づいてテキスト行を並べ替える方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="a25e9-131">方法: 区切り記号入りファイル (LINQ) (Visual Basic) のフィールドの順序を変更</span><span class="sxs-lookup"><span data-stu-id="a25e9-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="a25e9-132">.csv ファイルの行に含まれるフィールドを並べ替える方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="a25e9-133">方法: 結合および比較文字列のコレクションに (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25e9-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="a25e9-134">文字列リストをさまざまな方法で結合する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="a25e9-135">方法: 複数のソース (LINQ) (Visual Basic) からオブジェクトのコレクションへの追加</span><span class="sxs-lookup"><span data-stu-id="a25e9-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="a25e9-136">複数のテキスト ファイルをデータ ソースとしてオブジェクトのコレクションを作成する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="a25e9-137">方法: 異種ファイル (LINQ) (Visual Basic) からコンテンツを結合します。</span><span class="sxs-lookup"><span data-stu-id="a25e9-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="a25e9-138">2 つのリストに含まれる文字列を、一致するキーを使って 1 つの文字列に結合する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="a25e9-139">方法: 複数のファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割</span><span class="sxs-lookup"><span data-stu-id="a25e9-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="a25e9-140">1 つのファイルをデータ ソースとして新しいファイルを作成する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="a25e9-141">方法: CSV テキスト ファイル (LINQ) (Visual Basic) で列の値を計算</span><span class="sxs-lookup"><span data-stu-id="a25e9-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="a25e9-142">.csv ファイルでテキスト データに対して数学的計算を実行する方法が紹介されています。</span><span class="sxs-lookup"><span data-stu-id="a25e9-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25e9-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="a25e9-143">See Also</span></span>  
 [<span data-ttu-id="a25e9-144">統合言語クエリ (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a25e9-144">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 [<span data-ttu-id="a25e9-145">方法: CSV ファイルから XML を生成する</span><span class="sxs-lookup"><span data-stu-id="a25e9-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
