---
title: "Basic Data Types | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Basic Data Types
LINQ to SQL クエリは、Microsoft SQL Server で実行される前に Transact\-SQL に変換されるため、  LINQ to SQL は、SQL Server が基本データ型に対してサポートするのと同じ組み込み機能の多くをサポートします。  
  
## キャスト  
 SQL Server 内に同様の有効な変換が存在する場合は、変換元の CLR 型から変換先の CLR 型への暗黙的または明示的なキャストが有効になります。  CLR キャストの詳細については、「[CType 関数](../Topic/CType%20Function%20\(Visual%20Basic\).md) \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\)」および「[as](../Topic/as%20\(C%23%20Reference\).md)」を参照してください。  変換後に、CLR 式に対して実行された操作の動作は、変換先の型に通常割り当てられる他の CLR 式の動作と一致するように、キャストによって変更されます。継承の割り当てのコンテキストにおいてもキャストは変換可能です。  より厳密なエンティティ サブタイプにオブジェクトを変換して、そのサブタイプに固有のデータへのアクセスを可能にすることができます。  
  
## 等値演算子  
 LINQ to SQL は、LINQ to SQL クエリ内の基本データ型で次の等値演算子をサポートします。  
  
-   等値演算子および非等値演算子 : 等値演算子および非等値演算子は、数値型、<xref:System.Boolean> 型、<xref:System.DateTime> 型、および <xref:System.TimeSpan> 型についてサポートされます。  [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] の演算子 `=` および `<>` の詳細については、「[Comparison Operators](../Topic/Comparison%20Operators%20\(Visual%20Basic\).md)」を参照してください。C\# の比較演算子 `==` および `!=` の詳細については、「[\=\= 演算子](../Topic/==%20Operator%20\(C%23%20Reference\).md)」および「[\!\= 演算子](../Topic/!=%20Operator%20\(C%23%20Reference\).md)」を参照してください。  
  
-   Is 演算子 : `IS` 演算子には、継承の割り当ての使用時にサポートされる変換があります。  これは、オブジェクトが特定の種類のエンティティであるかどうかを検査する場合に、判別列を直接調べる代わりとして使用でき、判別列のチェックに変換されます。  Visual Basic と C\# の Is 演算子の詳細については、「[Is Operator](../Topic/Is%20Operator%20\(Visual%20Basic\).md)」および「[is](../Topic/is%20\(C%23%20Reference\).md)」を参照してください。  
  
## 参照  
 [SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)