---
title: "外部キーのプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 外部キーのプロパティ
Entity Data Model \(EDM\) における*外部キーのプロパティ*は、別のエンティティ型の[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)を含む[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)のプリミティブ型[のプロパティ](../../../../docs/framework/data/adonet/property.md) \(または一連のプリミティブ型のプロパティ\) です。  
  
 外部キーのプロパティは、リレーショナル データベースの外部キー列に似ています。  リレーショナル データベースで外部キー列を使用してテーブル内の行の間のリレーションシップを作成するのと同様に、概念モデルでは外部キーのプロパティを使用してエンティティ型の間の[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)を設定します。  エンティティ型の 1 つに外部キーのプロパティがある場合に、2 つのエンティティ型の間のアソシエーションを定義するには、[参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)を使用します。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  `Book` エンティティ型には、`PublisherId` というプロパティがあります。`PublishedBy` アソシエーションに参照整合性制約を定義するときに、このプロパティは `Publisher` エンティティ型のエンティティ キーを参照します。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、外部キーのプロパティ `PublisherId` を使用して、上の概念モデルに示された `PublishedBy` アソシエーションに参照整合性制約を定義します。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)