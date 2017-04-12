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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a79d1427331070da9c545fdd3175115fe187e879
ms.lasthandoff: 03/13/2017

---
# <a name="linq-and-strings-visual-basic"></a>LINQ と文字列 (Visual Basic)
LINQ を使用して、文字列および文字列のコレクションの照会し、変換することができます。 テキスト ファイル内の半構造化データで特に便利ですができます。 LINQ クエリは、従来の文字列関数と正規表現と組み合わせることができます。 たとえば、使用、<xref:System.String.Split%2A>または<xref:System.Text.RegularExpressions.Regex.Split%2A>し、クエリまたは LINQ を使用して変更できる文字列の配列を作成する方法</xref:System.Text.RegularExpressions.Regex.Split%2A></xref:System.String.Split%2A>。 使用することができます、<xref:System.Text.RegularExpressions.Regex.IsMatch%2A>メソッドで、 `where` LINQ クエリの句</xref:System.Text.RegularExpressions.Regex.IsMatch%2A>。 LINQ を使用するには照会または変更して、<xref:System.Text.RegularExpressions.MatchCollection>正規表現によって返される結果</xref:System.Text.RegularExpressions.MatchCollection>。  
  
 半構造化テキスト データを XML に変換するのにこのセクションで説明した手法を使用することもできます。 詳細については、次を参照してください。[方法: CSV ファイルから XML の生成](how-to-generate-xml-from-csv-files.md)します。  
  
 このセクションの例では、2 つのカテゴリに分類されます。  
  
## <a name="querying-a-block-of-text"></a>テキストのブロックのクエリを実行します。  
 クエリ、分析、およびテキスト ブロックを変更するを使用して、クエリ可能な小さな文字列の配列に分割する、<xref:System.String.Split%2A>メソッドまたは<xref:System.Text.RegularExpressions.Regex.Split%2A>メソッド</xref:System.Text.RegularExpressions.Regex.Split%2A></xref:System.String.Split%2A>。 ソース テキストを単語、文、段落、ページ、またはその他の条件に分割し、その後、クエリで必要とされるに応じてその他の分割を実行できます。  
  
 [方法: 文字列 (LINQ) (Visual Basic) での単語の出現回数をカウント](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 テキストに対する単純なクエリの実行に LINQ を使用する方法を示します。  
  
 [方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 任意の境界上でテキスト ファイルに分割する方法と各部分に対してクエリを実行する方法を示します。  
  
 [方法: クエリ (LINQ) (Visual Basic) の文字列内の文字](how-to-query-for-characters-in-a-string-linq.md)  
 文字列がクエリ可能型であることを示します。  
  
 [方法: LINQ クエリは、正規表現 (Visual Basic) とを組み合わせる](how-to-combine-linq-queries-with-regular-expressions.md)  
 フィルター選択されたクエリの結果に一致する複雑なパターンの LINQ クエリで正規表現を使用する方法を示します。  
  
## <a name="querying-semi-structured-data-in-text-format"></a>テキスト形式の半構造化データの照会  
 さまざまな種類のテキスト ファイルは、一連のタブ区切りまたはカンマ区切りのファイル、または固定長の行などのような書式設定を含む多くの場合、線で構成されます。 メモリにこのようなテキスト ファイルが読み取られた後に、クエリを実行するか、または行を変更する LINQ を使用できます。 また、LINQ クエリには、複数のソースからデータを結合したタスクが簡略化します。  
  
 [方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を検索](how-to-find-the-set-difference-between-two-lists-linq.md)  
 1 つのリストに存在するすべての文字列を検索する方法を示します。  
  
 [方法: 並べ替えまたはフィルター テキスト データでは、任意の単語またはフィールド (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 任意の単語またはフィールドに基づくテキスト行を並べ替える方法を示します。  
  
 [方法: 区切り記号入りファイル (LINQ) (Visual Basic) のフィールドの順序を変更](how-to-reorder-the-fields-of-a-delimited-file.md)  
 .Csv ファイルの行のフィールドの順序を変更する方法を示します。  
  
 [方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 さまざまな方法で文字列のリストを結合する方法を示します。  
  
 [方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 データ ソースとして複数のテキスト ファイルを使用してオブジェクトのコレクションを作成する方法を示します。  
  
 [方法: 異種ファイル (LINQ) (Visual Basic の場合) からコンテンツを結合します。](how-to-join-content-from-dissimilar-files-linq.md)  
 1 つの文字列に一致するキーを使用して&2; つのリスト内の文字列を結合する方法を示します。  
  
 [方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 データ ソースとして&1; つのファイルを使用して新しいファイルを作成する方法を示します。  
  
 [方法: CSV テキスト ファイル (LINQ) (Visual Basic) の列の値を計算](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 .Csv ファイル内のテキスト データに対して数学的な計算を実行する方法を示します。  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](index.md)   
 [方法: CSV ファイルから XML を生成する](how-to-generate-xml-from-csv-files.md)

