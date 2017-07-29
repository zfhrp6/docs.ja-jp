---
title: "要素操作 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: da747e884960c89fabc45d3761da92f913d66362
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="element-operations-c"></a>要素操作 (C#)
要素操作では、シーケンスから単一の特定の要素が返されます。  
  
 次のセクションでは、要素操作を実行する標準クエリ演算子のメソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|C# のクエリ式の構文|説明|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|コレクション内の指定されたインデックス位置にある要素を返します。|該当なし。|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|ElementAtOrDefault|コレクション内の指定したインデックス位置にある要素を返します。インデックスが範囲外の場合は既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|First|コレクションの最初の要素、または条件を満たす最初の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|FirstOrDefault|コレクションの最初の要素、または条件を満たす最初の要素を返します。 そのような要素が存在しない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|末尾|コレクションの最後の要素、または条件を満たす最後の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|LastOrDefault|コレクションの最後の要素、または条件を満たす最後の要素を返します。 そのような要素が存在しない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|Single|コレクションの唯一の要素、または条件を満たす唯一の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|SingleOrDefault|コレクションの唯一の要素、または条件を満たす唯一の要素を返します。 そのような要素が存在しない場合、またはコレクションの要素が 1 つだけでない場合は、既定値を返します。|該当なし。|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>   
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

