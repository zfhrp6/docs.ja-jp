---
title: "要素操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 5fcb0631-dce5-45ff-8abb-353cae21e14f
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 70a66b1cdbcc03a743fb43d497e40c8ae032c0aa
ms.lasthandoff: 03/13/2017

---
# <a name="element-operations-visual-basic"></a>要素操作 (Visual Basic)
要素操作では、シーケンスから単一の特定要素が返されます。  
  
 次のセクションでは、要素の操作を実行する標準クエリ演算子のメソッドが一覧表示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|ElementAt|コレクション内の指定したインデックス位置にある要素を返します。|該当なし。|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName></xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|ElementAtOrDefault|インデックスが範囲外にある場合は、コレクションまたは既定値で指定したインデックス位置にある要素を返します。|該当なし。|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName></xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|First|コレクションの最初の要素または条件を満たす最初の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName></xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName></xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|Firstordefault 演算子|コレクションの最初の要素または条件を満たす最初の要素を返します。 このような要素が存在しない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName></xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName></xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName></xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|末尾|コレクションの最後の要素または条件を満たす、最後の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName></xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|LastOrDefault|コレクションの最後の要素または条件を満たす、最後の要素を返します。 このような要素が存在しない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName></xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName></xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|Single|コレクションの唯一の要素または条件を満たす、唯一の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName></xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|SingleOrDefault|コレクションの唯一の要素または条件を満たす、唯一の要素を返します。 このような要素が存在しないか、コレクションに&1; 個の要素が含まれていない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName></xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
