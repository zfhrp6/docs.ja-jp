---
title: "エンティティ型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# エンティティ型
*エンティティ型*は、Entity Data Model \(EDM\) でデータ構造を記述するために不可欠な構成要素です。  概念モデルでのエンティティ型は、顧客や注文のように、トップレベル概念の構造を表します。  エンティティ型は、エンティティ型のインスタンスのテンプレートです。  各テンプレートには、次の情報が含まれています。  
  
-   一意の名前   \(必須\)  
  
-   1 つ以上のプロパティにより定義される[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)。  \(必須\)  
  
-   [プロパティ](../../../../docs/framework/data/adonet/property.md)の形式のデータ。  \(省略可能\)  
  
-   [アソシエーション](../../../../docs/framework/data/adonet/association-type.md)の一方の [End](../../../../docs/framework/data/adonet/association-end.md) から別の End へのナビゲーションを可能にする[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)。  \(オプション\)。  
  
 アプリケーションでは、エンティティ型のインスタンスが特定のオブジェクト \(特定の顧客や注文など\) を表します。  エンティティ型の各インスタンスに対して、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)内の[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)を一意にする必要があります。  
  
 2 つのエンティティ型のインスタンスは、型が同じであり、エンティティ キーの値が等しい場合にのみ、等価のインスタンスと見なされます。  
  
## 例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![モデル例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 各エンティティ型のエンティティ キーを構成するプロパティには、"\(キー\)" と示されています。  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) では、概念スキーマ定義言語 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) と呼ばれるドメイン固有言語 \(DSL\) を使用して概念モデルを定義します。  次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## 参照  
 [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [ファセット](../../../../docs/framework/data/adonet/facet.md)