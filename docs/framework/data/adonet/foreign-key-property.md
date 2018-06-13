---
title: 外部キーのプロパティ
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 5a00c4d4cc469f5c816b8173843d283d63ccf308
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762651"
---
# <a name="foreign-key-property"></a>外部キーのプロパティ
A*外部キー プロパティ*Entity Data Model (EDM) では、プリミティブ型[プロパティ](../../../../docs/framework/data/adonet/property.md)(またはプリミティブ型のプロパティのセット) で、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)を格納しています。[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)別のエンティティ型。  
  
 外部キーのプロパティは、リレーショナル データベースの外部キー列に似ています。 テーブルの行の間のリレーションシップを作成するリレーショナル データベースの外部キー列を使用すること、同じ方法で概念モデルで外部キー プロパティが確立するために使用される[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)エンティティ型の間です。 A[参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)2 つのエンティティ型、型のいずれかがある外部キーのプロパティとの間のアソシエーションを定義するために使用します。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 `Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、外部キーのプロパティ `PublisherId` を使用して、上の概念モデルに示された `PublishedBy` アソシエーションに参照整合性制約を定義します。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>関連項目  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
