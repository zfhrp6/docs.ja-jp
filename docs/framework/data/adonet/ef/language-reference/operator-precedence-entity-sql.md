---
title: "演算子の優先順位 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 演算子の優先順位 (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリに複数の演算子がある場合は、演算子の優先順位によって、操作の実行順序が決まります。  実行される順序により、クエリ結果の値は大きく変わります。  
  
 演算子には、次の表に示す優先順位レベルが定義されています。  優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。  
  
|レベル|演算の種類|演算子|  
|---------|-----------|---------|  
|1|1 次式|`. , [] ()`|  
|2|単項|`! not`|  
|3|乗法|`* / %`|  
|4|加法|`+ -`|  
|5|並べ替え|`< > <= >=`|  
|6|等価比較|`= != <>`|  
|7|条件 AND|`and &&`|  
|8|条件 OR|`or &#124;&#124;`|  
  
 式の中の 2 つの演算子が同じ優先順位レベルである場合は、クエリの中での位置に従って演算子は左から右へと評価されます。  たとえば、 `x+y-z`  は  `(x+y)-z` と評価されます。  
  
 クエリの中で演算子の定義済みの優先順位を無効にするには、かっこを使用します。  この場合、かっこ内のすべての演算が評価され、1 つの結果が作成されてから、かっこ外の演算子でこの結果が使用されます。  たとえば、`x+y*z` の場合、`y` と `z` の積に `x` が加算されますが、`(x+y)*z` の場合は、`x` と `y` の和に `z` が乗算されます。  
  
## 参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)