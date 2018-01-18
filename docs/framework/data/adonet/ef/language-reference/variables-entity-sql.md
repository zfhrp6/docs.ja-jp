---
title: "変数 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d035f8d5616f2eb4c5a4db31857da2be0cd3d930
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="variables-entity-sql"></a>変数 (Entity SQL)
## <a name="variable"></a>変数  
 変数式は、現在のスコープで定義されている名前付きの式への参照です。 変数の参照を有効にする必要があります[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別子で定義されている[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)です。  
  
 次の例は、式における変数の使用方法を示しています。 FROM 句の `c` は変数の定義です。 SELECT 句内で使用された `c` は、変数参照を表します。  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>参照  
 [識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
 [パラメーター](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
