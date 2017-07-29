---
title: "データのパーティション分割 (C#)"
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
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
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
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a>データのパーティション分割 (C#)
LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。  
  
 次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。 最初の操作では、シーケンスの最初の 3 つの要素が返されます。 2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。 3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。  
  
 ![LINQ パーティション分割操作](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。  
  
## <a name="operators"></a>演算子  
  
|演算子名|説明|C# のクエリ式の構文|説明|  
|-------------------|-----------------|---------------------------------|----------------------|  
|Skip|シーケンス内の指定した位置まで要素をスキップします。|該当なし。|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。|該当なし。|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|シーケンス内の指定した位置までの要素を取得します。|該当なし。|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。|該当なし。|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>   
 [標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

