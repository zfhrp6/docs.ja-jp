---
title: "演算子の優先順位 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bc8ebd235016a22792d98e1a966e8c1217e2823e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="operator-precedence-entity-sql"></a>演算子の優先順位 (Entity SQL)
ときに、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリが複数の演算子、演算子の優先順位は、操作が実行される順序を決定します。 実行される順序により、クエリ結果の値は大きく変わります。  
  
 演算子には、次の表に示す優先順位レベルが定義されています。 優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。  
  
|レベル|演算の種類|演算子|  
|-----------|--------------------|--------------|  
|1|1 次式|`. , [] ()`|  
|2|単項|`! not`|  
|3|乗法|`* / %`|  
|4|加法|`+ -`|  
|5|並べ替え|`< > <= >=`|  
|6|等価比較|`= != <>`|  
|7|条件 AND|`and &&`|  
|8|条件 OR|`or &#124;&#124;`|  
  
 式の中の 2 つの演算子が同じ優先順位レベルである場合は、クエリの中での位置に従って演算子は左から右へと評価されます。 たとえば、`x+y-z` は `(x+y)-z` と評価されます。  
  
 クエリの中で演算子の定義済みの優先順位を無効にするには、かっこを使用します。 この場合、かっこ内のすべての演算が評価され、1 つの結果が作成されてから、かっこ外の演算子でこの結果が使用されます。 たとえば、`x+y*z`乗算`y`によって`z`し、追加`x`が`(x+y)*z`追加`x`に`y`には、結果を乗算し、`z`です。  
  
## <a name="see-also"></a>参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
