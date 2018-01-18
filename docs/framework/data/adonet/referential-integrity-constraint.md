---
title: "参照整合性制約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c343a0eba2478e041186f7bef18a85400c54bb5c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="referential-integrity-constraint"></a>参照整合性制約
A*参照整合性制約*Entity Data Model (EDM) では、リレーショナル データベースの参照整合性制約に似ています。 データベース テーブルから列 (または列) が、別のテーブルの主キーを参照できるように、同じ方法で、[プロパティ](../../../../docs/framework/data/adonet/property.md)(またはプロパティ) の[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)参照できる、[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)別のエンティティ型。 参照されるエンティティ型が呼び出される、*プリンシパル end*制約のです。 プリンシパル end を参照するエンティティ型が呼び出される、*依存 end*制約のです。  
  
 参照整合性制約がの一部として定義されている、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)2 つのエンティティ型の間です。 参照整合性制約の定義には、次の情報を指定します。  
  
-   制約のプリンシパル End。 (エンティティ キーが依存 End により参照されるエンティティ型)  
  
-   プリンシパル End のエンティティ キー。  
  
-   制約の依存 End。 (プリンシパル End のエンティティ キーを参照するプロパティを持つエンティティ型)  
  
-   依存 End の参照プロパティ。  
  
 EDM の参照整合性制約の目的は、常に有効なアソシエーションが存在することを確認するためです。 詳細については、次を参照してください。[外部キー プロパティ](../../../../docs/framework/data/adonet/foreign-key-property.md)です。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。 `Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上の概念モデルに示された `PublishedBy` アソシエーションの参照整合性制約を定義しています。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
