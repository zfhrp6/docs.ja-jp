---
title: "型システム (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b68bce0e3f1139b48446200decca5beb0a1a1a71
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="type-system-entity-sql"></a>型システム (Entity SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]いくつかの型をサポートしています。  
  
-   `Int32` や `String.` などのプリミティブ型 (単純型)。  
  
-   <xref:System.Data.Metadata.Edm.EntityType>、<xref:System.Data.Metadata.Edm.ComplexType>、<xref:System.Data.Metadata.Edm.RelationshipType> など、スキーマで定義される標準型。  
  
-   <xref:System.Data.Metadata.Edm.CollectionType>、<xref:System.Data.Metadata.Edm.RowType>、<xref:System.Data.Metadata.Edm.RefType> など、明示的にはスキーマで定義されない匿名型。  
  
 ここでは、明示的にはスキーマで定義されていなくても [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされている匿名型について説明します。 プリミティブ型と標準型については、次を参照してください。[概念モデル型 (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)です。  
  
## <a name="rows"></a>行  
 行の構造は、行を構成する型指定された名前付きのメンバーの配列に依存します。 行型には ID がなく、派生元にすることはできません。 同じ行型のインスタンスは、メンバーがそれぞれ同等である場合は同等になります。 行には構造同値以外の動作はなく、共通言語ランタイムに同等のものはありません。 クエリの結果は、行または行のコレクションを含む構造になります。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリとホスト言語の間の API バインドは、結果を生成したクエリでどのように行が構成されるかを定義します。 行のインスタンスを構築する方法については、次を参照してください。[の構築型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)です。  
  
## <a name="collections"></a>コレクション  
 コレクション型は、他のオブジェクトの 0 個以上のインスタンスを表します。 コレクションを作成する方法については、次を参照してください。[の構築型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)です。  
  
## <a name="references"></a>参照  
 参照とは、特定のエンティティ セットにある特定のエンティティへの論理ポインターです。  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、参照の構築、分解、およびナビゲートを行うための次の演算子がサポートされています。  
  
-   [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 メンバー アクセス (ドット) 演算子 (`.`) を使用して参照によるナビゲーションを行うことができます。 次のコード例では、r (参照) プロパティによるナビゲーションで Order の Id プロパティを取得します。  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 参照値が null であるか、参照先が存在しない場合、結果は null になります。  
  
## <a name="see-also"></a>参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 [CSDL、SSDL、および MSL 仕様](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
