---
title: "結合操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 39ab4854-ac84-4738-9d0b-3cb79be84db4
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dce1adb5b918674bc8ee8fc48c8ff5b3c3814a88
ms.lasthandoff: 03/13/2017

---
# <a name="join-operations-visual-basic"></a>結合操作 (Visual Basic)
A*結合*を別のデータ ソースの共通の属性を共有するオブジェクトと&1; つのデータ ソース内のオブジェクトの関連付けは、2 つのデータ ソースのです。  
  
 相互に直接の関連がない&2; つのデータ ソースを対象とするクエリにおいて、結合は重要な操作になります。 オブジェクト指向プログラミングでは、これは一方向の関係における逆の方向など、モデル化されていないオブジェクト間の相関関係を意味する場合があります。 一方向の関係の例として、City 型のプロパティを持つ Customer クラスがあるとします。ただし、City クラスには、Customer オブジェクトのコレクションを表すプロパティはありません。 City オブジェクトのリストから各都市のすべての顧客を取得する場合は、結合演算を使用して顧客を検索できます。  
  
 LINQ フレームワークで提供されている結合メソッドは、 <xref:System.Linq.Enumerable.Join%2A> <xref:System.Linq.Enumerable.GroupJoin%2A>。</xref:System.Linq.Enumerable.GroupJoin%2A> </xref:System.Linq.Enumerable.Join%2A> これらのメソッドでは、等キーが等しいかどうかに基づいて&2; つのデータ ソースに一致する結合を実行します。 (比較に関して、Transact-SQL では、"小なり" 演算子などの "等値" 以外の結合演算子もサポートされます)。リレーショナル データベース用語で<xref:System.Linq.Enumerable.Join%2A>は内部結合、結合の種類のデータ セットで一致するオブジェクトのみが返される</xref:System.Linq.Enumerable.Join%2A>。 <xref:System.Linq.Enumerable.GroupJoin%2A>でもメソッドのリレーショナル データベース用語では、直接相当するものはありませんが、内部結合と左外部結合のスーパー セットを実装します</xref:System.Linq.Enumerable.GroupJoin%2A>。 左外部結合では、他のデータ ソースには相関関係を持つ要素があるない場合でも、最初 (左側) のデータ ソースの各要素を返す結合ですが、します。  
  
 次の図は、2 つのセットと、内部結合または左外部結合としてこれらのセットに含まれている要素の概念図を示しています。  
  
 ![内側/外側を示す&2; つの重なり合う円します。] (../../../../csharp/programming-guide/concepts/linq/media/joincircles.png "JoinCircles")  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Join|キー セレクター関数に基づいて&2; つのシーケンスを結合し、値のペアを抽出します。|`From x In …, y In … Where x.a = y.a`<br /><br /> または<br /><br /> `Join … [As …]In … On …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Join%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=fullName></xref:System.Linq.Queryable.Join%2A?displayProperty=fullName>|  
|GroupJoin|キー セレクター関数に基づいて&2; つのシーケンスを結合し、各要素について結果として得られる一致をグループ化します。|`Group Join … In … On …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [結合およびクロス積クエリを作成します。](http://msdn.microsoft.com/library/d8072ede-0521-4670-9bec-1778ceeb875b)   
 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [方法: 異種ファイル (LINQ) (Visual Basic の場合) からコンテンツを結合します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md)   
 [方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
